# Team Setup Guide

事実ベースのEntity棚卸しから、Concept、OKR、最初のProjectが動き出すところまでを案内するaachat agentです。

## できること

- セットアップ対象と判断者を確認する
- Company Entityを棚卸しし、安全にRegistryへ登録する
- 人間の意思、実際の判断、観測から必要なConceptを提案する
- 時間軸での理想と現在の問題からdraft OKRを作る
- 解決案を比較し、最初のProjectとhandoffを整える
- Ask、Concept publish、計測不足、人間操作待ちから再開する

## 使い方

1. aachatのDiscoverで`p-take55/team-setup-guide`を開き、Cloneして自分のcopyを作ります。
2. copyを所有する環境で`aachat up`を実行し、agentがreadyになるまで待ちます。
3. チームセットアップ用Projectの`Add Agent`から、そのcopyをmemberとして追加します。
4. Composerのagent target chipで追加したagentを選び、「このProjectのチームセットアップを始めて」と送ります。
5. Project Askへ回答した後は、同じ方法でagentを選び「回答したので続けて」と送ります。

Project timelineの`@mention`は通知であり、agent sessionを起動しません。

テンプレートからagentは自動clone・自動配属されません。Projectを先に開始し、後から追加しても`PROJECT.md`から再開できます。

## Workflow

```text
Scope → Entities → Concepts → Outcomes → Initiatives → Bootstrap
```

各phaseで、調査、候補提示、必要なAsk、人間確認、Registry更新、再読込を反復します。重要なConceptがpendingの場合やbaselineを取得できない場合は、状態と再開条件を残して止まります。

## 成果

- 確認済みCompany Entity
- review可能なConcept proposalと必要なpublished Concept
- outcomeと2〜5件のKRを持つdraft OKR
- 対象KRと解決仮説が明確な最初のProject
- blocking / non-blockingな残課題と再開手順

## Repo構成

| Path | Role |
|---|---|
| `identity.md` | agentの役割と境界 |
| `.agents/skills/team-setup/` | セットアップworkflowと参照資料 |
| `environment.yaml` | runtime設定。追加packageやsecretは不要 |
| `memory/` / `knowledge/` | 将来、Project固有ではない再利用知見が得られた場合だけ使用 |

Project固有の事実、判断、仕様、進捗はagent repoではなく、対象Projectのshared documentと各Registryへ保存します。
