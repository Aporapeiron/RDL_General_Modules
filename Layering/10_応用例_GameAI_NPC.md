# 応用例：GameAI NPC Layering Profile v0.1

*RDL_General_Modules / Layering / Example*

## 0. 目的

GameAIのNPC内部を、単一状態ではなく **更新速度と拘束範囲の異なる複数Layer** として整理する。

このProfileは、

```text
Purpose = NPCの内部状態・学習・行動・世代差を整理する
Axis    = 更新速度 / 保持時間 / 拘束伝播
```

という条件で構成する。

普遍的なNPC存在論ではない。

---

## 1. 基本配置

初期Profile：

```text
DNA Layer
    ↓
Neural M_B
    ↓
Physical M_B
    ↓
Experience M_B
    ↓
Realtime M_B

変化しにくい
      ↓
変化しやすい
```

この順序は整理用Profileであり、固定的な自然階層ではない。

---

## 2. DNA Layer

DNA LayerはNPC生成時に与えられる最も低速な拘束条件。

初期実装では、生涯中に更新しない固定パラメータとする。

```text
DNA = immutable during lifetime
```

DNAは現在の解釈状態そのものではなく、後続Layerの取りうる範囲を拘束する。

例：

```text
危険感度の初期範囲
探索傾向
学習速度レンジ
記憶減衰特性
身体サイズ範囲
移動能力上限
感覚性能範囲
```

概念的には、

```text
M_B^neural   in Ω_N(DNA)
M_B^physical in Ω_P(DNA)
```

と置ける。

DNAを通常の `M_B` 更新対象へ無理に含める必要はない。

---

## 3. Neural M_B

Neural `M_B` は、取得した `RIB_B` をどう処理・比較・保持・解釈しやすいかを拘束する比較的低速な構造。

例：

```text
注意配分
危険 / 報酬への基本感度
学習率
忘却率
一般化の強さ
探索 / 活用傾向
刺激への反応速度
```

同じ `RIB_B` でも Neural `M_B` が異なれば、形成される `F` は異なりうる。

---

## 4. Physical M_B

Physical `M_B` は、現在の身体状態・運動能力・物理的制約についてNPC側で有効な有限拘束構造。

例：

```text
現在の速度性能
負傷
疲労
体力
使用可能な身体部位
旋回能力
攻撃可能距離
感覚器の現在状態
```

ここで、

```text
物理世界そのもの
!=
Physical M_B
```

である。

Physical `M_B` はNPCの現在Bにおける身体的行動可能域の有限記述である。

---

## 5. Experience M_B

Experience `M_B` は、生涯中の相互作用履歴から形成された比較的持続的な関係拘束。

例：

```text
この場所には餌がある
この場所では過去に襲われた
この個体は危険
この経路は成功率が高い
この行動は失敗しやすい
```

概念的には、

```text
M_B^experience(t+1)
= Update(M_B^experience(t), RIB_B, F, E, History)
```

と扱える。

---

## 6. Realtime M_B

Realtime `M_B` は最も高速に更新される現在状態の拘束層。

例：

```text
現在見えている対象
直前に聞いた音
現在の空腹
現在の逃走対象
選択中の行動
短期的な優先順位
```

```text
M_B^rt(t) -> M_B^rt(t + Δt)
```

のようにtick単位で更新されうる。

---

## 7. 更新速度

初期実装では、概念的に、

```text
η_DNA < η_Neural < η_Physical < η_Experience < η_Realtime
```

とみなす。

ただし厳密な不等式を普遍則とはしない。

運用上は、

```text
DNA        : 生涯中固定
Neural     : 非常に低速
Physical   : 低〜中速
Experience : 中速
Realtime   : 高速
```

程度の区分でよい。

---

## 8. 層間の拘束伝播

低速Layerは高速Layerの可能域を拘束する。

```text
DNA
 ↓
Neural / Physical
 ↓
Experience
 ↓
Realtime
```

一方、高速Layerで反復する関係は、より低速なLayerへ沈降しうる。

```text
Realtimeで反復
      ↓
Experienceとして定着
```

将来的には、

```text
Experienceの長期反復
      ↓
Neuralの再構成
```

のような遅い逆向き更新も扱える。

したがって、これは単純な一方向木ではない。

---

## 9. 生殖への拡張

DNA Layerを他の可変Layerから分離しておくと、生殖を既存NPC更新系の外側へ自然に追加できる。

```text
DNA_A --\
         > recombination / mutation -> DNA_child
DNA_B --/
```

概念的には、

```text
DNA_child = Recombine(DNA_A, DNA_B) + Mutation
```

新個体では、

```text
M_B^neural(0)   = Init_N(DNA_child)
M_B^physical(0) = Init_P(DNA_child)
```

として初期化する。

Experience / Realtimeは原則として直接継承しない。

したがって、

> **経験内容そのものではなく、学習・反応・身体形成の可能域が継承される。**

という構造になる。

これにより、

```text
DNA variation
↓
Neural / Physical の差
↓
Experience形成の差
↓
行動差
↓
生存・繁殖成功の差
↓
次世代DNA分布の変化
```

という進化的過程を後から接続できる。

---

## 10. エピジェネティクス

初期モデルでは扱わない。

必要になった場合のみ、

```text
DNA
 ↓
Expression / Development
 ↓
Neural / Physical
```

という中間Layerを追加する。

初期段階では、

```text
DNA -> Neural / Physical
```

の直接初期化で十分とする。

---

## 11. ξ と注意

この5層を綺麗に定義できても、NPCが「本当にこの5層からできている」とは扱わない。

```text
NPC 5-Layer Profile
!=
universal ontology
```

Layer Mapの外側・間・重複・未回収関係は残る。

```text
Complete_B(NPC Layer Map) = true
and
ξ(B) != 0
```

---

## 12. 一文圧縮

> **GameAI NPCでは、DNAを生涯中固定の生成拘束とし、Neural・Physical・Experience・Realtimeという更新速度の異なる有限関係拘束Layerを重ねることで、先天差・身体状態・学習履歴・瞬間判断を分離し、生殖・進化を後から接続できる。**
