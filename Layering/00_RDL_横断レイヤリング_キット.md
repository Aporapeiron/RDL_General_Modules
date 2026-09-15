# RDL 横断レイヤリング・キット v0.2

*RDL_General_Modules / Layering*

## 変更履歴

### v0.2 — 2026-09-15

- 名称を **「RDL 汎用レイヤリングモデル」から「RDL 横断レイヤリング・キット」へ変更**。
- 「汎用」は広い一般成立を強く示唆するため、複数領域で使い回すという配置上の意味に留めて **「横断」** を採用。
- 「モデル」は対象そのものの構造を主張する響きが強いため、軽量な補助道具であることを示す **「キット」** へ変更。
- `Layering = f(B, Purpose, Axis)`、`μ_Λ`、多次元 Layer Space を必須仕様ではなく記述補助として明記。
- 4-Layer構成を一般則から `Temporal / Stability 4-Layer Profile` の一例へ位置づけ直した。
- 運用原則を「規範」よりも「使い方の目安」として軽量化。
- ファイル名の区切りはツールチェーンで扱いやすいよう `_` に統一。

### v0.1

- Layering の初期整理。
- Purpose / B / Axis に応じた層配置、Hierarchyとの分離、多次元化、再Layering、`ξ` による実体化防止を記述。

---

## 0. 目的

本キットは、SILNまたは任意の有限関係構造を、**用途に応じた軸で複数のLayerへ整理するための軽量な補助ツール群**である。

特定領域の専用モデルではなく、GameAI・社会・物理・その他の領域で、似た整理操作を横断的に使い回すための共通の見方・書式を置く。

ここでいうLayerは、対象世界にあらかじめ存在する絶対的階層ではない。

> **有限境界 B と Purpose のもとで、選択した整理軸に従って構成される有限な配置である。**

したがって、

```text
Layer_B != absolute ontology
```

である。

本キットは「対象は本当にLayerでできている」と主張するためのものではない。

> **用途に応じて整理すると便利だからLayerとして見る。**

という程度の道具として扱う。

---

## 1. Layering Context

対象を `S`、有限境界を `B`、整理目的を `P` とする。

現在のBで扱う有限要素集合を、

```text
X_B(S) = {x1, x2, ..., xn}
```

とする。

Layering Contextを概念的に、

```text
Λ = (S, B, P, A, R)
```

と書く。

- `S` : 対象SILN / 対象構造
- `B` : 有限境界
- `P` : Purpose
- `A` : 整理に使う軸の集合
- `R` : 配置・比較・接続規則

Layeringは、実用上、

```text
Layering = f(B, Purpose, Axis)
```

という整理操作として読める。

この式は厳密な普遍関数を宣言するものではなく、**何を基準にLayerを切ったかを忘れないための記述補助**である。

---

## 2. 整理軸 Axis

Layerを切る軸は固定しない。

例：

```text
A_time        : 更新速度 / 保持時間
A_stability   : 安定度 / 変化抵抗
A_scale       : 空間・時間・エネルギー等のスケール
A_scope       : 適用範囲
A_dependency  : 他構造への依存度
A_abstraction : 抽象度 / 記述粒度
A_control     : 操作可能性 / 権限制約
A_cost        : 変更コスト
```

同じ対象でも軸が違えば配置が異なってよい。

```text
Layer_(B,A1)(x) != Layer_(B,A2)(x)
```

これは分類失敗ではない。

> **用途に応じて、必要な軸を選ぶ。**

---

## 3. Descriptor と Layer配置

各要素 `x` について、現在のBとPurposeのもとで有限なDescriptorを取ることができる。

```text
d_(B,P)(x) = (a1(x), a2(x), ..., ak(x))
```

Layer集合を、

```text
L_Λ = {l1, l2, ..., lm}
```

とするなら、整理結果を概念的に、

```text
Layer_Λ : X_B(S) -> L_Λ
```

と書ける。

ただしLayer境界付近の要素を一つへ強制する必要はない。

必要なら、

```text
μ_Λ(x, li)
```

をLayerへの適合度として持ち、複数Layerへの重複配置を許す。

`μ` は確率である必要はない。

この表記も必須仕様ではなく、曖昧な境界を無理に一つへ押し込めないための補助表現である。

---

## 4. Layering と Hierarchy の分離

LayeringとHierarchyは同一ではない。

```text
Layering
= 選択した軸上での整理配置

Hierarchy
= contains / composed_of / depends_on / governs 等の上下・包含・依存関係
```

したがって、

```text
Layering != Hierarchy
```

である。

真に階層関係を扱う場合は、例えば、

```text
H_Λ = (X_B, R_H)
```

を別に置き、`R_H` に `contains / depends_on / composed_of / abstracts` 等を明示できる。

異なるLayerに属することだけを理由に、親子関係を仮定してはならない。

---

## 5. 線形Layerと非線形Layer

Layeringは必ずしも一列の上下構造である必要はない。

単純な線形型：

```text
L0 -> L1 -> L2 -> L3
```

分岐型：

```text
      L1
     /  \
   L2    L3
     \  /
      L4
```

必要なら重複・ネットワーク型も使える。

したがって、

> **Layering != Linear ordering**

である。

---

## 6. 多次元 Layer Space

複数のAxisを同時に採用する場合、各要素を一つのLayer番号ではなく、多次元の有限Descriptorとして見ることもできる。

例えば、

```text
A = {time, scale, abstraction, control, stability}
```

なら、

```text
x -> (a_time, a_scale, a_abstraction, a_control, a_stability)
```

となる。

概念的には、

```text
LayerSpace_B subset of finite n-dimensional descriptor space
```

として扱える。

ただし、これは常用を勧めるものではない。

人間向けの運用では、全軸を同時表示するより、必要なViewへ投影した方が扱いやすい。

```text
High-dimensional Layer Space
        ↓ projection
Temporal View
Scale View
Organizational View
Abstraction View
```

> **用途に応じて、必要十分な軸だけを選ぶ。必要以上に高次元化しない。**

---

## 7. Temporal / Stability 4-Layer Profile

旧来の、

```text
物理構造
基層構造
中核構造
上層構造
```

は、本キットでは `Temporal / Stability 4-Layer Profile` の一例として扱う。

主要Axisは、

```text
time scale / stability / change cost
```

である。

概念的には、

```text
L0  長期・高安定・高変更コスト
L1  長期・高慣性
L2  中期・反復により定着
L3  短期・高速・変更容易
```

と読める。

ただし、`m = 4` は一般則ではない。

用途に応じて2層、3層、5層、連続量、重複Layerを採用してよい。

---

## 8. 低速拘束と高速沈降

Temporal / Stability系のLayerでは、典型的に二方向の関係を区別できる。

低速Layerから高速Layerへ：

```text
slow constraints
      ↓
fast state / action
```

高速Layerから低速Layerへ：

```text
repeated fast interaction
      ↓ sedimentation
slower persistent structure
```

したがってLayer構造は、単純な一方向木とは限らない。

反復・蓄積・破断・再構成によって、Layer間の関係そのものが変化しうる。

---

## 9. B変更と再Layering

Layer配置は固定しない。

```text
Λ_B
 ↓
Layer_B
 ↓
ΔB / Purpose変更 / 新規RIB_B
 ↓
再記述
 ↓
Λ_B'
 ↓
Layer_B'
```

同じ要素 `x` について、

```text
Layer_(B1)(x) != Layer_(B2)(x)
```

となってよい。

これは矛盾ではなく、観測・操作条件の違いである。

---

## 10. ξ と実体化防止

Layeringは整理を便利にする一方、整理された区分を「対象そのものの実体」と誤認させやすい。

そのため、本キットでは `[B-ξ]` を重要な注意条件とする。

```text
forall finite B : ξ(B) != 0
```

したがって、

```text
Complete_B(Layer Map) = true
```

であっても、

```text
ξ(B) = 0
```

とはならない。

圧縮すると、

```text
整理の成功
!=
存在論的実体化
```

である。

Layer名が明瞭であるほど、Layerの外側・間・重複・未回収関係を忘れてはならない。

> **レイヤーは対象を切る道具であって、対象そのものではない。**

---

## 11. 使い方の目安

1. 何のために整理するかを先に決める。
2. その用途に必要なBを置く。
3. 必要なAxisだけを選ぶ。
4. Layer数を先に固定しない。
5. LayeringとHierarchyを混同しない。
6. 必要なら重複所属・非線形配置を使う。
7. 多次元化は可能だが、見づらくなるなら必要なViewへ投影する。
8. ΔBやPurpose変更後は切り直してよい。
9. Layer Mapが完成してもξを消さない。
10. Layerを対象の本質へ昇格させない。

---

## 12. 一文圧縮

> **RDL 横断レイヤリング・キットは、有限BとPurposeのもとで用途に合う整理軸を選び、対象を扱いやすいLayerへ配置・投影するための軽量な補助ツール群である。Layerは対象そのものではなく、再配置可能な有限整理であり、常にξを伴う。**

## 超圧縮

> **用途に応じて切る。切った線を世界そのものだと思わない。**
