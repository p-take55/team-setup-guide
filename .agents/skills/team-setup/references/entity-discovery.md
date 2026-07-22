# Entity discovery（Entity の棚卸し）

この reference は Scope と Entities で使う。Registry 操作の前に投影された `aachat-company` skill を読む。現在の enum と mutation contract はそちらが正本。

## 対象範囲を確定する

次を確認する:

- 既存の setup root、または Company Registry が空の場合は sponsor 確認済みの root 候補。そして対象が会社・事業・製品・チームのどの subtree か。
- 含める領域と除外する領域。
- 事実を確認し tradeoff を決められる setup sponsor。
- Team Owner / Admin で、Concept publish と `person` / `partner` / `agreement` の管理ができる Registry steward。
- sponsor が agent に読むことを許可した資料。

Scope を抜けるのに必須なのは、対象 root（既存 or sponsor 確認済み候補）・対象範囲・sponsor の 3 つだけ。対象外・steward・資料は、この時点で分かる分を記録すればよく、未確定でも Scope を止めない。steward は sensitive Entity 操作と Concept publish の前までに確定させる。normal Entity の登録は steward を待たずに進められる。

Company root の概要があればそこから始め、関連 subtree だけに絞る。既定で Registry 全体を取得しない。root が無ければ、Scope は検証済みの root 候補名、`organization` kind、想定 status、根拠で完了してよい。それを最初の Entities mutation として登録し、再読込し、`PROJECT.md` の候補を canonical な Entity ID / 参照へ置き換える。root の identity を創作せず Ask する。

## 候補を見つける

文書中のあらゆる名詞ではなく、Team の安定した構成要素を探す。task、campaign、KPI、責任、関係、一時的な作業は、独立して Entity kind の要件を満たす場合を除いて除外する。

現在の enum は投影された `aachat-company` contract が正本。分類時は次の意味を使う:

| Kind | 表す安定 identity | Mutation |
|---|---|---|
| `organization` | 正式な組織単位として機能する会社・事業・部門・チーム | agent 可 |
| `person` | Team を構成する個人 | 人間のみ |
| `offering` | 顧客へ継続提供する製品・サービス・プラン | agent 可 |
| `media` | 継続運用する Web サイト・SNS・newsletter 等の発信 channel | agent 可 |
| `community` | membership や共通の参加目的を持つ継続的な参加者集団 | agent 可 |
| `system` | 会社構成の一部として管理する主要な製品・業務システム | agent 可 |
| `facility` | 継続的なオフィス・店舗・工場・拠点・主要設備 | agent 可 |
| `partner` | 確認済みの継続的な取引・提携関係を持つ外部主体 | 人間のみ |
| `agreement` | 契約・ライセンス・正式合意の安定 identity | 人間のみ |

顧客向けの `offering` と、それを支える内部の `system` を区別する。正式な `organization` と参加者の `community` を区別する。確認済みの継続 `partner` と、資料で単に言及されただけの vendor を区別する。1 つの identity を複数 kind へ重複させない。

各候補について次を検証する:

| 項目 | テスト |
|---|---|
| Name | これは正式または継続的な識別名か？ |
| Kind | サポートされる 1 つの kind だけがその正体を表すか？ |
| Status | `planned / current / retired` が作業進捗ではなく会社構成を表すか？ |
| Parent | これは所有・利用・依存・責任ではなく、唯一の主要な構造上の parent か？ |
| Evidence | sponsor または許可された資料が存在と分類を確認できるか？ |
| Existing match | 同じ安定 identity が別名で既に存在しないか？ |

kind を創作したり、欠けた関係を名前や階層に埋め込んだりしない。誤った parent より、parent 無しを選ぶ。

## 小さな batch で確認する

曖昧な候補を、共有する 1 つの分岐でグループ化する。確認済みの事実を示し、登録を変える点だけを聞く。

sponsor に `後で決める` を選ばせてよい。その候補は未登録のままにし、後続の link や OKR が必要とするまで non-blocking として記録する。

## 登録して検証する

- サポートされる非 sensitive な Entity を、再送可能な nonce 付きで登録する。
- `person` / `partner` / `agreement` は絶対に変更しない。人間に管理画面での操作を依頼する。
- Ask の回答は人間の mutation が行われた証拠ではない。Company の状態を再読込する。
- 各 batch の後に該当 subtree を再読込し、重複、retired parent 配下の active な子、誤った階層を確認する。
- `realizes` link は published Concept にだけ、かつ Entity がその共有された意味を構造的に実現するときだけ張る。

## 出力

正本状態を再読込した後にだけ、検証済み inventory を作る。未解決の推測は入れない。残る人間操作を blocking / non-blocking に分類する。
