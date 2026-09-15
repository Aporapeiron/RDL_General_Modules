# RDL 横断レイヤリング・キット

RDLで、対象を **用途に応じて複数のLayerへ整理するための軽量な補助キット**。

GameAI・社会・物理など、異なる領域で似た整理操作が使えそうなときに、共通の見方・書式として横断利用する。

「汎用理論」や「対象世界の普遍的階層」を主張するものではない。

```text
Purpose / finite B / Axis
        ↓
   Layering
        ↓
有限な整理配置
        ↓
必要なら再投影・再配置
```

したがって、

```text
Layer = 整理上の配置
≠ 対象そのものの存在論的実体
```

とする。

## 文書構成

- `00_RDL_横断レイヤリング_キット.md` — キット本体。整理軸、多次元化、Hierarchyとの分離、ξ
- `10_応用例_GameAI_NPC.md` — DNA / Neural / Physical / Experience / Realtime
- `20_応用例_社会モデル.md` — Geography / History-Culture / Institution / Group / Individual / Realtime
- `30_応用例_物理・スケールレイヤー.md` — 物理構造の時間安定レイヤーと、理論のScale Layer

## 基本の使い方

```text
Layering = f(B, Purpose, Axis)
```

これは厳密な普遍関数の宣言ではなく、**何のために、どのBで、どの軸を使って切ったかを明示するための補助表現**である。

同じ対象でも Purpose / B / Axis が変われば、Layer配置は変わってよい。

複数軸を同時に使う高次元Layer Spaceも必要なら扱えるが、運用では用途に必要な軸だけを選び、見づらくなるなら必要なViewへ投影する。

> **用途に応じて、必要十分な切り方を選ぶ。**

そして、どれほど整理が成功しても、有限な Layer Map は終端閉包ではない。

```text
Complete_B(Layer Map) = true
and
ξ(B) != 0
```

> **レイヤーは対象を切る道具であって、対象そのものではない。**
