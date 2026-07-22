---
name: team-setup
description: aachat の Team を、最初の対象範囲確認と事実ベースの Company Entity 棚卸しから、人間への Ask、Concept proposal、draft OKR、最初の Project、運用 handoff まで案内する。新しい Team を立ち上げる、既存組織を aachat へ載せる、不完全な Company Map を組み直す、回答・Concept publish・計測・人間専用操作を待っている team setup Project を再開する、といったときに使う。
---

# チームセットアップ

人間と agent が次の判断を下し、最初の Project を動かせる、**最小で完全な Team model** を作る。事実、人間の判断、不確実性を、それぞれ正しい aachat の置き場所に保つ。

## 開始と再開

0. この session が setup Project に属していることを確認する。setup Project が無ければ Team Registry を変更しない。Discover の Team Setup template を開始するか、setup のライフサイクルを載せる Project を明示的に選ぶよう人間に依頼する。
1. 現在の Project の `PROJECT.md` を読む。
2. shared document を作成・編集する前に、投影された `aachat-session` contract を読む。
3. 新しい Ask を作る前に、既存の未回答・回答済み Project Ask を読む。
4. 現在の Company / Concept / OKR / Project の状態は、次の行動を変え得る範囲だけ読む。
5. 現在の phase は、チェック済みのボックスではなく Registry の状態から判定する。
6. 最も早い blocking phase から続ける。完了済みの mutation をやり直さない。

`PROJECT.md` にまだ対象 root（既存 or sponsor 確認済み候補）・対象範囲・setup sponsor が定まっていなければ、Scope から始める。対象外・時間軸・Registry steward はここで分かる分だけ記録し、揃っていなくても Scope を通過してよい（steward は sensitive Entity 操作と Concept publish の前までに確定させる）。

## 中核ループ

すべての phase の内側で同じループを回す:

```text
調べる → 小さな候補集合を作る → 未解決の判断を提示する → 必要なら Ask
       → 確定した mutation を適用する → 正本の状態を再読込する → handoff を更新する
```

Ask を最初の独立した 1 phase として扱わない。blocking な判断と、non-blocking な backlog を区別する。現在の phase の判断だけを扱い、先の phase の推奨（Entity の分割・parent など）を、事実を確認する前に混ぜない。

## Phase router

| Phase | 読む | Gate（次へ進む条件） |
|---|---|---|
| Scope | `references/entity-discovery.md` | 対象 root（既存 or sponsor 確認済み候補）・対象範囲・sponsor（判断者）が明確。対象外・時間軸・steward は未確定でも Phase 0 を止めない（steward は sensitive Entity 操作 / Concept publish 前、時間軸は Phase 3 で確定） |
| Entities | `references/entity-discovery.md` と投影された `aachat-company` | 確認済みの通常 Entity が登録・再読込され、人間専用操作が分類されている |
| Concepts | `references/concept-modeling.md` と投影された `aachat-concepts` | 必要な proposal が存在し、OKR を実質的に方向づけ・制約する Direction / Guardrail Concept が published である |
| Outcomes | `references/okr-and-projects.md` と投影された `aachat-okr` | 有効な draft OKR が存在する、または計測整備 Project と再開条件が存在する |
| Initiatives | `references/okr-and-projects.md` | 人間が最初の解決案（solution bet）を選び、その対象 KR が明確である |
| Bootstrap | `references/completion.md` | Project docs と handoff が揃い、必要な membership が canonical な Project 状態で確認済みである |

その phase で動く前に、参照ファイルを最後まで読む。Ask を作成・待機する前に投影された `aachat-ask` を読む。

## Ask と一時停止

- 現在の turn を越えて残る判断には Project Ask を使う。
- Ask は、確認済みの文脈、未解決の分岐、正当化できる場合の推奨、各回答後に何が起きるかを示してから行う。
- 1 つの Ask に複数 Phase の判断を混ぜない。Scope の Ask で Entity 構成（分割・parent など）を一緒に聞かない。
- 事実確認より先に Entity 構成や分割を推奨しない。まず確認済みの事実を示し、未確定点だけを分岐として出す。
- `unknown / 後で決める` が正当な non-blocking の結論になり得る場合は、それを許容する。
- 現在の gate を止める操作だけを `Waiting for human (blocking)` に置く。後回しにできる review や follow-up は、setup を `waiting_for_human` にせず `Non-blocking follow-up` に残す。
- Project Ask への回答は session を自動再開しない。停止前に `PROJECT.md` に Ask を反映し、人間に「回答して、agent へ `回答したので続けて` と送る」よう伝える。
- 再開時は回答と Registry の正本状態を読む。記憶している transcript の文脈に頼らない。

回答が現在の turn で返り、待つことが本当に有用なときだけ、上限付きの Session Ask を使う。短間隔で polling しない。

## ライフサイクル gate

- Concept proposal は pending であり正本ではない。published として報告しない。
- Entity の `realizes` link と OKR の Concept link は、Concept に現在 published な内容がある後にだけ追加する。
- publish を blocking にするのは、pending な Direction / Guardrail が OKR または Project の選択を実質的に変える・制約するときだけ。`guidance_strength = governing` を要求しない。補助的な pending finding は non-blocking として進める。
- draft OKR には、baseline と target を備えた 2〜5 件の完全な KR が必要。計測できない場合は、先に計測整備 Project を作り、setup を `model_ready_partial` にする。
- agent は Project を作れるが、人間による member 追加、Concept publish、sensitive Entity 登録が行われたとは主張しない。人間の操作後に再読込する。

## 保存先

- Entity / Concept / OKR の正本データは各 Registry に置く。
- 質問と回答は Project Ask に置く。
- Project 固有の判断、検証済み inventory、handoff は shared document に置く。
- 推測段階の候補テーブルを、確定した shared document として保存しない。
- `templates/entity-inventory.md` は事実が確認された後にだけ使う。
- `templates/setup-handoff.md` は Model ready で使い、Operational で更新する。

## 完了

`references/completion.md` を読む。次のいずれか 1 つの状態を報告する:

- `in_progress`
- `waiting_for_human`
- `model_ready_partial`
- `model_ready`
- `operational`

waiting / pending / draft / partial の状態を complete へ丸めない。
