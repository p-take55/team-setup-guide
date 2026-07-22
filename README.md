# {{agent_name}}

{{description}}

aachat の agent repository。`aachat up` で session が立ち上がる度にここから
identity / memory / knowledge / skill が読み込まれ、agent の挙動を決める **永続ストレージ** として機能する。

## このrepoが定義するもの

| ファイル / ディレクトリ | 役割 | session への取り込み |
|---|---|---|
| `identity.md` | agent の人格・役割・行動原則の正本 | session worktree の `.claude/CLAUDE.md` に `<aachat-identity>` ブロックとして注入される |
| `environment.yaml` | 依存パッケージ宣言（apt / brew / pip / npm / cargo） | リモート workspace 実行時の環境構築に使う |
| `.claude/skills/<skill>/SKILL.md` | この agent 専用の skill | session worktree の `.claude/skills/<skill>/` に projection される（aachat 標準 skill と merge） |
| `memory/` | session 間で引き継ぐ状態・優先順位・保留中の会話 | agent から自由に読み書きできる。push して初めて次 session に反映される |
| `knowledge/` | 長期参照する事実・リファレンス・ドメイン知識 | 同上 |

> `identity.md` は旧 `CLAUDE.md` の置き換え。`.claude/CLAUDE.md` の `<aachat-managed>` 区画は session 起動時に aachat が毎回再生成するため、ここで CLAUDE.md を置いても上書きされて意味がない。

## ローカルでの場所

aachat を立ち上げているマシン上では、この repo は次のパスに展開される（macOS / Linux）。

| パス | 内容 | 触ってよい？ |
|---|---|---|
| `~/aachat/agents/{{agent_name}}/` | user-visible な worktree（`main` 追従） | ✅ identity / skills / memory の編集はここで |
| `~/aachat/.run/cache/<owner>--{{agent_name}}.git/` | bare clone（aachat 内部キャッシュ） | ❌ 直接触らない |
| `~/aachat/.run/workspaces/{{agent_name}}--<short-id>/aachat/agents/{{agent_name}}/` | session ごとの一時 worktree | ⚠️ session 中の作業領域。終了時にクリーンアップされる |

team repo を `aachat init` した側からは、`aachat/agents/{{agent_name}}/` というシンボリックリンク経由で `~/aachat/agents/{{agent_name}}/` と同じ場所が見える。

## 編集の仕方

- agent の挙動を変えたいときは `~/aachat/agents/{{agent_name}}/identity.md` を編集する
- session 中の自己改善は agent 自身が `memory/` / `knowledge/` / `.claude/skills/` を更新する
- 変更は **push して初めて次 session に反映される**（session worktree は使い捨てなので、その場の編集は session 終了で消える）

## 触ってはいけないもの

- 認証情報・トークン・秘密鍵（`.gitignore` で除外）
- 絶対パス・環境固有の値

## 話しかける

```bash
aachat project send <project> "@{{agent_name}} <依頼>"
```

`chat` CLI は session 内側の agent 専用。outside agent / 人間は `aachat` CLI を使う。
