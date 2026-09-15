# RDL Layering Module

RDL において、対象を **用途に応じて複数の層へ整理するための汎用モジュール**。

Layer は対象世界にあらかじめ刻まれた絶対的な階層ではない。

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

- `00_汎用レイヤリングモデル.md` — Layering の一般定義、軸、多次元化、Hierarchyとの分離、ξ
- `10_応用例_GameAI_NPC.md` — DNA / Neural / Physical / Experience / Realtime
- `20_応用例_社会モデル.md` — Geography / History-Culture / Institution / Group / Individual / Realtime
- `30_応用例_物理・スケールレイヤー.md` — 物理構造の時間安定レイヤーと、理論のScale Layer

## 基本原則

```text
Layering = f(B, Purpose, Axis)
```

同じ対象でも Purpose / B / Axis が変われば、Layer配置は変わってよい。

理論上は複数軸を同時に使う高次元Layer Spaceを許すが、運用では用途に必要な軸だけを選び、必要以上に高次元化しない。

そして、どれほど整理が成功しても、有限な Layer Map は終端閉包ではない。

```text
Complete_B(Layer Map) = true
and
ξ(B) != 0
```

> **レイヤーは対象を切る道具であって、対象そのものではない。**
