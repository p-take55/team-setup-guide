# 完了と再開の状態

一時停止・handoff・setup 完了の宣言の前にこの reference を使う。

次の順序で、ちょうど 1 つの状態を選ぶ:

1. すべての運用条件を検証できたら `operational`。
2. model は review できるが、計測などの宣言済み前提が有効な OKR または運用可能な Project を妨げるなら `model_ready_partial`。
3. 必要な Concept publish を含むすべての Model ready gate を満たしたときにだけ `model_ready`。
4. 先行する gate が人間専用操作で block されているなら `waiting_for_human`。
5. agent が安全に続けられるなら `in_progress`。

選んだ milestone が `model_ready_partial` でも、人間操作は Waiting for human に別で記録する。milestone は model の完成度を、waiting 欄は次に誰が動くべきかを表す。

## 状態の定義

### in_progress

agent が、新たな人間の権限や外部状態なしに安全に続けられる。

### waiting_for_human

blocking な Ask、Concept publish、sensitive Entity mutation、member 追加、その他の人間専用操作が未完了。

停止前に:

- `PROJECT.md` の current phase と Waiting for human を更新する。
- 対象の resource または操作を特定する。
- なぜ block するか、何が non-blocking で残るかを述べる。
- 操作後に agent を再開する方法を人間に伝える。

### model_ready_partial

Team model と意図した outcome は review できるが、計測整備 Project や別の明示的前提が有効な OKR または運用可能な Project を妨げている。

### model_ready

確認済み Entity 状態、意図した outcome、問題の選択、有効な OKR 定義、Project 候補を sponsor が review できる。その OKR を実質的に方向づけ・制約する Direction / Guardrail Concept は published である。補助的な proposal は non-blocking な pending のまま残ってよい。

### operational

すべての条件を満たす:

- 必要な通常 Entity が登録・再読込されている。
- blocking な sensitive Entity 操作が検証済み。
- OKR を実質的に方向づけ・制約する Direction / Guardrail Concept が published。
- 2〜5 件の KR を持つ有効な draft OKR が存在する。
- target KR と solution 仮説を持つ最初の Project が存在する。
- 必要な人間 member が揃っている。
- 初回 session brief と検証 point が準備済み。
- 残る作業が明示的に non-blocking。

## 正本での検証

過去の tool 応答やチェックリストの文言から完了を推測しない。関連する Company / Concept / OKR / Project / Ask / membership の状態を再読込する。

## Handoff

`templates/setup-handoff.md` を使う。Registry の内容を複製せず、正本 resource へ link する。次を分ける:

- 達成した milestone。
- 登録・publish された状態。
- pending review。
- 人間操作。
- 計測または data の前提。
- 次の Project 行動と担当者。

sponsor が milestone を受け入れ、setup 固有の blocking 操作が残っていないときにだけ、setup Project を close する。
