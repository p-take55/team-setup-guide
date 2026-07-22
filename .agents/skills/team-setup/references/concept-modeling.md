# Concept modeling（Concept のモデリング）

この reference は Concepts で使う。読む・提案する前に投影された `aachat-concepts` skill を読む。現在の kind、意味軸、source、類似 gate、relation、review ライフサイクルはそちらが正本。

## 3 つの channel から意味を掘り出す

すべての Concept に 3 つを揃えることを要求せず、関連する channel を使う:

- 宣言された意思（Declared intent）: 権限を持つ人間が今 Team に対して選ぶこと。
- 表れた実践（Revealed practice）: 実際の選択・犠牲・例外・投資が露わにする優先順位。
- 観測された現実（Observed reality）: 顧客・metric・incident・実験から得た問題と学び。

現在の意思が欠けていれば人間に直接聞く。kind 名を質問票にしない。有用な直接質問には、望む変化、現在の集中と意図的な除外、tradeoff の優先、譲れない制約、重要だが不確かな信念がある。

## 暗黙の判断を再構成する

歴史が重要なとき、判断の episode を再構成する:

```text
状況 → 実際の選択肢 → 選択 → 犠牲 → 述べられた理由 → 結果 → 権限 → source
```

述べられていない理由を創作しない。episode 横断で繰り返される緊張を探し、判断 model の候補を作る:

```text
[文脈] では、[代替] より [選択] を選ぶ。理由は [理由]。
[境界] のときは適用しない。
```

反対の選択、他の episode、反証、範囲の境界、権限で stress test する。未解決の矛盾は、人間に Concept kind を選ばせるのではなく、人間に問う。

## 網羅と抑制のバランス

探索の後、関連する意味が次の観点で理解できているか確認する:

- Direction: Team が存在する理由、約束、方向、goal。
- Guardrails: principle、policy、重要な decision。
- Learning: problem、question、hypothesis、finding、重要な metric。
- Response: idea と具体的な solution 候補。

これは kind ごとに 1 つずつ埋めるノルマではなく、網羅の確認。重要な欠落ごとに、既存 Concept で足りるか、proposal が要るか、人間待ちか、今回の setup に無関係かを説明する。

同じ判断価値を持つ候補は統合する。Project 固有の詳細は project docs に残す。重複した新規 Concept より、既存 Concept、change proposal、意味のある link を選ぶ。

## 意味が明確になった後にだけ分類する

現在の enum と意味軸は投影された `aachat-concepts` contract が正本。探索の後、次の kind の意味を使う:

| 領域 | Kind | 意味 |
|---|---|---|
| Direction | `purpose` | Team が存在する理由 |
| Direction | `value_proposition` | 誰にどんな固有価値を約束するか |
| Direction | `strategy` | outcome へ向けた集中と意図的な除外の選択 |
| Direction | `goal` | OKR の測定契約を持たない、再利用可能な目指す状態・方向 |
| Guardrails | `principle` | 価値や選択肢が衝突するときに使う判断 heuristic |
| Guardrails | `policy` | 明示的なルールまたは譲れない制約 |
| Guardrails | `decision` | 権限を持つ人間が採用した重要な選択 |
| Learning | `metric` | Team が繰り返し見る測定観点 |
| Learning | `problem` | 根拠のある、解く価値のある問題 |
| Learning | `question` | Project 横断で追い続ける価値のある未解決の問い |
| Learning | `hypothesis` | 反証可能だが未検証の信念 |
| Learning | `finding` | 根拠のある観測・学び |
| Response | `idea` | まだ評価していない可能性 |
| Response | `solution` | problem への具体的な応答候補 |

`principle` は tradeoff を導き、`policy` はルールを定める。`problem` は所有できるほど確立したもの。未検証の説明は `hypothesis` のまま。`finding` は根拠のある観測を報告し、`decision` は人間の選択を記録する。Project Ask は、その問いが Team 横断で残る必要がある場合を除いて `question` Concept ではない。`idea` は problem への具体的応答として枠付けられたときにだけ `solution` になる。OKR の period / baseline / target / owner / Check-in を `goal` や `metric` Concept に複製しない。

## 正しく提案する

- kind は意味が安定してから選ぶ。
- scope、abstraction、horizon、guidance、maturity はそれぞれ独立に選ぶ。
- 人間の直接宣言は `human_decision` source で意味を与えられるが、mutation には現在の session 等の Project-scoped な source も必要。
- 観測の不確実性を保つ。hypothesis を finding へ格上げしない。
- 作成を強行せず、類似（similarity）の応答に従う。

## Publication gate

proposal の作成は pending review を生む。pending な Direction または Guardrail が、`guidance_strength` に関わらず OKR の意味や制約を実質的に変えるとき、Outcomes phase を block する。補助的な pending Concept は non-blocking のままでよい。Concept publish は人間の操作。指名された Team Owner / Admin の Registry steward へ回し、published revision を後で再読込する。

Entity の `realizes` link と OKR の Concept link は publish 後にだけ追加する。再開時は link 前に Concept と review 状態を再読込する。
