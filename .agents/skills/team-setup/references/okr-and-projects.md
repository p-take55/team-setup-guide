# OKR と最初の Project

この reference は Outcomes と Initiatives で使う。Registry 操作の前に投影された `aachat-okr` skill を読む。ライフサイクル、KR、owner、Check-in、link contract はそちらが正本。

## 理想 → 問題 → outcome へ進む

1. 人間がどの時間軸で計画したいかを聞く。
2. その時間軸で、誰にとって何が観測可能に変わるべきかを聞く。
3. 現状を、測定値と明確にラベルした人間の観測から確立する。
4. 症状、考えられる原因、制約、solution idea を分ける。
5. 問題を、理想の妨げ度・根拠・Team の影響力・依存・遅延コストで比較する。
6. 正当化できるとき問題を推奨し、Team が所有する問題は人間に選ばせる。
7. その問題が十分に減った後の状態を Objective として書く。
8. 理想が現実になりつつある証拠として、2〜5 件の KR を定義する。

Concept を直接 OKR へ翻訳しない。published Concept は、理想と選んだ問題が Team の direction と guardrail に沿うかの確認に使う。

## KR を定義する

各 KR には metric、unit、baseline、明確に異なる target が要る。達成度、速度、失敗率、人間の負担、持続した行動など、補完的な観測を好む。同じ signal の言い換えを複数並べない。

baseline や target を創作しない。測定がどこから来るか、なぜその target が重要かを聞く。target は、履歴、顧客との約束、経済性、capacity、benchmark、または人間の明示的な stretch 選択から導いてよい。

## 計測の欠落

OKR contract は baseline 未定の KR をサポートしない。妥当な metric を測定できない場合:

1. 有効な観測可能 proxy が存在するか検証する。
2. 無ければ、OKR の前に計測整備 Project を作る。
3. setup を `model_ready_partial` にする。
4. 何が測定できれば OKR 登録が解けるか、誰が提供するかを記録する。
5. baseline 取得後に再開する。

この計測整備は明示的な非 OKR の例外。まだ target KR を持たず、有効な OKR を解くためだけに存在する。baseline 取得後は、最初の solution bet を選ぶ前に Outcomes へ戻る。計測の導入を Key Result に偽装しない。

## 最初の solution bet を選ぶ

solution を Objective と KR の外に保つ。Project 候補を次で比較する:

- 期待される KR への影響と因果の根拠。
- solution 仮説を支える根拠。
- OKR 期間内に実行し学べるか。
- owner と member の空き。
- bet が外れたときの可逆性と学び。

推奨を提示し、人間に選ばせる。上記の計測整備を除き、選んだ問題と target KR が明確になった後にだけ Project を作る。

Project handoff には次を含める:

- 選んだ問題と solution 仮説。
- target OKR と KR。
- なぜこの Project がそれらを動かすのか。
- 範囲と non-goal。
- 最初の検証または Check-in の point。
- 必要な人間の member 操作。
- setup transcript なしで実行できる初回 session brief。

agent は Project を作れるが、member 追加が行われたと主張してはならない。人間に member 追加を依頼し、membership を再読込してから初回 session を始める。
