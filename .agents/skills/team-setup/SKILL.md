---
name: team-setup
description: aachat の Team を、最初の対象確認と事実ベースの Company Entity 棚卸しから、人間への確認、Concept proposal、draft OKR、最初の Project、運用 handoff まで案内する。新しい Team を立ち上げる、既存組織を aachat へ載せる、不完全な Company Map を組み直す、回答・Concept publish・計測・人間専用操作を待っている team setup Project を再開する、といったときに使う。
---

# チームセットアップ

人間と agent が次の判断を下し、最初の Project を動かせる、**最小で完全な Team model** を作る。**主役は対話。記録は人間に見せない裏方。** 優秀なインタビュアーとして一つずつ聞き、答えをもらうたびに裏で正本へ記録する。終わったとき、人間の側に aachat の知識は一切要らない。

## 対話のルール（他のどの節より優先）

人間へ向けたすべての応答をこのループで作る:

```text
聞く（1問）→ 答えをもらう → 裏で登録・再読込 → 一行で報告 → 次の1問
```

1. **1ターン1問。** 一度に求める判断は 1 つだけ。番号付きの質問リストを出したら失格。次の質問は前の答えを見てから決める。
2. **推測できることは聞かずに確認する。** team slug、話している相手、既存の資料や Registry から当たりをつけ、「〜で合ってますか？」で消化する。「合ってる」で済む確認は 1 問と数える。
3. **答えを次の質問の前に登録する。** 確定した事実はその場で正本へ書き、再読込してから、人間の言葉で一行だけ報告する。まとめて後で登録しない。
4. **先の話を今出さない。** 管理者権限・時間軸・除外範囲などは、その操作や判断の直前に初めて話題にする。
5. **応答は短く。** 報告 1 行＋質問 1 つが基本形。人間が読む量と決める量を常に最小化する。

### 見本

```text
人間: やりましょか

agent: DataLoverチームのセットアップですね。私が一つずつ聞くので、
       答えてもらうだけで進みます。まず確認——
       最終的な決めごとはtakedaさんがする、で合ってますか？

人間: 合ってる

agent: では始めます。DataLoverって、ひとことで言うと
       誰向けの何のプロダクトですか？

人間: 中小企業向けのデータ分析SaaSです

agent: （裏で root と DataLover を登録・再読込してから）
       会社の構成に「Commons Technologies › DataLover」を記録しました。
       チームは何人くらいで、どんな役割の人がいますか？
```

この密度と長さを最後まで保つ。フォームのような列挙を返した時点で失格。

## 人間への言葉

内部語は内部の判断・記録だけで使い、人間へ返す文からは消す。

- 出さない語: Phase 番号、Registry、Entity、Concept、OKR、mutation、gate、sponsor、steward。
- 言い換えの例: sponsor →「最終的に決める人」/ steward →「公開や重要データを扱える管理者」（必要になるまで話題にしない）/ Company Entity →「会社の構成（部署・製品・拠点など）」/ Concept →「チームの方針・判断基準」/ OKR →「目標と、その測り方」。

## 開始と再開

0. この session が setup Project に属していることを確認する。setup Project が無ければ Team Registry を変更しない。Discover の Team Setup template を開始するか、setup のライフサイクルを載せる Project を明示的に選ぶよう人間に依頼する。
1. 現在の Project の `PROJECT.md` を読む。
2. shared document を作成・編集する前に、投影された `aachat-session` skill を読む。
3. 新しい確認をする前に、既存の未回答・回答済み Project Ask を読む。
4. 現在の Company / Concept / OKR / Project の状態は、次の行動を変え得る範囲だけ読む。
5. 現在の段階は、チェック済みのボックスではなく Registry の状態から判定する。
6. 最も早い blocking な段階から続ける。完了済みの mutation をやり直さない。

対象（会社・事業・チームのどれか）と最終判断者が定まっていなければ、そこから対話を始める。除外範囲・時間軸・Registry steward は分かった分だけ記録し、揃っていなくても先へ進む（steward は sensitive Entity 操作と Concept publish の前までに確定させる）。

## 進行の内部管理（人間に見せない）

段階と gate は agent の内部判定にだけ使う。会話に段階名・gate を出さない。

| 段階 | 読む | 内部 gate |
|---|---|---|
| Scope | `references/entity-discovery.md` | 対象 root（既存 or sponsor 確認済み候補）・対象範囲・sponsor（判断者）が明確。対象外・時間軸・steward は未確定でも止めない（steward は sensitive 操作 / Concept publish 前、時間軸は Outcomes で確定） |
| Entities | `references/entity-discovery.md` と投影された `aachat-company` | 確認済みの通常 Entity が登録・再読込され、人間専用操作が分類されている |
| Concepts | `references/concept-modeling.md` と投影された `aachat-concepts` | 必要な proposal が存在し、OKR を実質的に方向づけ・制約する Direction / Guardrail Concept が published である |
| Outcomes | `references/okr-and-projects.md` と投影された `aachat-okr` | 有効な draft OKR が存在する、または計測整備 Project と再開条件が存在する |
| Initiatives | `references/okr-and-projects.md` | 人間が最初の解決案（solution bet）を選び、その対象 KR が明確である |
| Bootstrap | `references/completion.md` | Project docs と handoff が揃い、必要な membership が canonical な Project 状態で確認済みである |

その段階で動く前に、参照ファイルを最後まで読む。段階をまたぐ判断を 1 つの質問に混ぜない。事実確認より先に Entity 構成（分割・parent）を推奨しない。

## 人間へ聞く・止まる

- 目の前に人間がいる session では、chat で一問ずつ聞く。そこで Project Ask を作らない。
- Project Ask は例外で、「決めるべき人がこの session にいない」「日をまたぐ検討が要る」ときだけ使う。作成前に投影された `aachat-ask` を読む。
- `分からない / 後で決める` が正当な結論になり得る場合は、それを許容して non-blocking に記録する。
- 現在の gate を止める操作だけを `Waiting for human (blocking)` に置く。後回しにできる review や follow-up は、setup を `waiting_for_human` にせず `Non-blocking follow-up` に残す。
- Project Ask への回答は session を自動再開しない。使った場合は停止前に `PROJECT.md` を更新し、回答後に「回答したので続けて」と送ってもらう導線を残す。
- 再開時は回答と Registry の正本状態を読む。記憶している transcript の文脈に頼らない。

## ライフサイクル gate

- Concept proposal は pending であり正本ではない。published として報告しない。
- Entity の `realizes` link と OKR の Concept link は、Concept に現在 published な内容がある後にだけ追加する。
- publish を blocking にするのは、pending な Direction / Guardrail が OKR または Project の選択を実質的に変える・制約するときだけ。`guidance_strength = governing` を要求しない。補助的な pending finding は non-blocking として進める。
- draft OKR には、baseline と target を備えた 2〜5 件の完全な KR が必要。計測できない場合は、先に計測整備 Project を作り、setup を `model_ready_partial` にする。
- agent は Project を作れるが、人間による member 追加、Concept publish、sensitive Entity 登録が行われたとは主張しない。人間の操作後に再読込する。

## 保存先

- Entity / Concept / OKR の正本データは各 Registry に置く。
- 質問と回答のうち Project Ask を使ったものは Project Ask に置く。
- Project 固有の判断、検証済み inventory、handoff は shared document に置く。
- 推測段階の候補テーブルを、確定した shared document として保存しない。
- `templates/entity-inventory.md` は事実が確認された後にだけ使う。
- `templates/setup-handoff.md` は Model ready で使い、Operational で更新する。

## 完了

`references/completion.md` を読む。次のいずれか 1 つの状態を内部で判定し、`PROJECT.md` に記録する:

- `in_progress`
- `waiting_for_human`
- `model_ready_partial`
- `model_ready`
- `operational`

waiting / pending / draft / partial の状態を complete へ丸めない。人間への報告は状態名ではなく、「何ができたか」「次に何をすればいいか」を平易な言葉で 1〜3 行にする。
