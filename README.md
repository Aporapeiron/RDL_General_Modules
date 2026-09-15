# RDL General Modules

**RDL_General_Modules** は、RDLの複数領域で横断的に再利用できる **領域非依存の構造整理・操作モジュール**を置くリポジトリです。

`RDL_Functions` や `RDL_Durability_Modules` と責務を分けます。

```text
RDL_Functions
= 外部理論・数理・実装との翻訳 / Function化

RDL_Durability_Modules
= 維持・変形・遷移・破断の検査

RDL_General_Modules
= 複数領域で再利用する構造整理・配置・補助操作

RDL_JunkDNA
= まだModuleとして固定しない未採用・未廃棄断片
```

Generalは「何でも置く箱」ではありません。

> **Human / Music / GameAI / Enterprise / 物理・社会等の複数領域で、同じ整理・操作形式を再利用できるものを置く。**

---

## Current Modules

### [Layering](Layering/)

有限境界 `B`、Purpose、整理軸 `Axis` に応じて、対象を複数のLayerへ整理する汎用モジュール。

```text
Layering = f(B, Purpose, Axis)
```

Layerは対象世界にあらかじめ存在する絶対階層ではなく、現在の用途に対する有限な整理配置です。

主な論点：

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

外部手法・旧分類・既存操作をRDL語彙へ一段翻訳した、まだ正式Moduleではない操作候補を保持しています。

現在は主に、

- 多重SILNの比較・配置
- シミュレーション破断検査

等が残っています。

今後、責務が固まったものは `Layering` のような正式Module、`RDL_Durability_Modules`、`RDL_Functions`、または `RDL_JunkDNA` へ再配置します。

---

## General Module の昇格基準

Generalへ正式Moduleとして置くものは、最低限次を満たすことを目安とします。

1. 特定領域だけに閉じない。
2. Purpose / B / 入力 / 出力または操作結果を説明できる。
3. Core primitiveを勝手に再定義しない。
4. Human / Music / GameAI等、複数領域へ同じ形式で適用可能である。
5. どの条件で使え、どこで破れるかを記述できる。
6. 完成した整理結果を終端的真理へ昇格させず、`ξ` を保持する。

---

## 一文圧縮

> **RDL_General_Modules は、RDLの複数応用領域で共通利用できる、領域非依存の構造整理・配置・補助操作を保持する横断Module層である。**
