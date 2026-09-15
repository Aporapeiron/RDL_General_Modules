# RDL General Modules

**RDL_General_Modules** は、RDLの複数領域で使い回せる **小さな構造整理・配置・補助ツール**を置くリポジトリです。

Coreへ入れるほど基底的ではないが、Human / Music / GameAI / Enterprise / 社会・物理などで何度も使えそうな道具を、軽く取り出せる形で保持します。

`RDL_Functions` や `RDL_Durability_Modules` とは責務を分けます。

```text
RDL_Functions
= 外部理論・数理・実装との翻訳 / Function化

RDL_Durability_Modules
= 維持・変形・遷移・破断の検査

RDL_General_Modules
= 複数領域で使い回せる構造整理・配置・補助ツール

RDL_JunkDNA
= まだツールやModuleとして固めない未採用・未廃棄断片
```

Generalは「何でも置く箱」ではありませんが、過度に重い一般理論を置く場所でもありません。

> **Coreに入れるほどではない。しかし複数の場所で繰り返し使えて便利。**

その程度の軽さを基本にします。

---

## Current Kits / Tools

### [RDL 横断レイヤリング・キット](Layering/)

有限境界 `B`、Purpose、整理軸 `Axis` に応じて、対象を複数のLayerへ整理する軽量キット。

```text
Layering = f(B, Purpose, Axis)
```

これは普遍的な階層理論を主張する式ではなく、**何のために・どのBで・どの軸を使って整理したか**を見失わないための補助表現です。

主な見方：

```text
Temporal / Stability Layer
Scale Layer
Organizational Layer
Abstraction Layer
Multi-dimensional Layer Space
Layering と Hierarchy の分離
低速拘束と高速沈降
ΔB後の再Layering
ξによる実体化防止
```

応用例：

- GameAI NPC — `DNA / Neural / Physical / Experience / Realtime`
- 社会モデル — `Geography / History-Culture / Institution / Group / Individual / Realtime`
- 物理構造 — `Material / Structure / History / Operating State / Realtime Interaction`
- 物理理論 — Newtonian / relativistic / quantum 等をScale / Validityで整理

Layer Mapが局所的に完成しても、終端閉包とはみなしません。

```text
Complete_B(Layer Map) = true
and
ξ(B) != 0
```

> **レイヤーは対象を切る道具であって、対象そのものではない。**

---

## Experimental candidates

### `翻訳後の暫定操作案/`

外部手法・旧分類・既存操作をRDL語彙へ一段翻訳した、まだ置き場所が固まっていない操作候補を保持しています。

現在は主に、

- 多重SILNの比較・配置
- シミュレーション破断検査

等が残っています。

責務が見えてきたものは、`Layering` のようなKit / Tool、`RDL_Durability_Modules`、`RDL_Functions`、または `RDL_JunkDNA` へ移します。

---

## General に置く目安

Generalへ置くものは、だいたい次を満たせばよいものとします。

1. 特定領域だけに閉じず、複数の場所で使い回せそうである。
2. Purpose / B / 入力 / 出力または整理結果を説明できる。
3. Core primitiveを勝手に再定義しない。
4. 少なくとも複数の応用先で同じ見方・操作が役立つ。
5. 使える条件と、うまくいかない条件を書ける。
6. 整理結果を終端的真理へ昇格させず、`ξ` を保持する。

これは厳密な昇格試験ではなく、置き場所を決めるための目安です。

---

## 一文圧縮

> **RDL_General_Modules は、Coreほど重くないが複数領域で繰り返し使えて便利な、横断的な小道具を置く場所である。**
