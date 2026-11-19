---
slug: ja-jp/real-world-development/cloud
title: "GitHub Copilot cloud agent"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot cloud agent](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** を使用すると、GitHub Copilot がクラウド上で非同期に作業できます。GitHub 上で作業を割り当てると、cloud agent がバックグラウンドでリポジトリを調査し、変更を加えてプルリクエストを作成します。

このワークショップでは、cloud agent に従わせるカスタムインストラクションを追加し、GitHub Issue を割り当てます。エージェントダッシュボードからセッションを監視・誘導し、カスタムエージェントで作業方針を調整して、プルリクエストをレビューして結果を反復改善します。

## 演習

| 演習 | トピック | 説明 |
|----------|-------|-------------|
| [0. 前提条件][ex0] | セットアップ | リポジトリと Codespace を作成 |
| [1. カスタムインストラクション][ex1] | コンテキスト | cloud agent が従うインストラクションを追加 |
| [2. Cloud Agent][ex2] | 非同期エージェント | Copilot cloud agent に Issue を割り当て |
| [3. カスタムエージェント][ex3] | 専門エージェント | カスタムエージェントを確認して使用 |
| [4. エージェントの管理][ex4] | 監視 | エージェントセッションを監視・誘導 |
| [5. 反復改善][ex5] | レビュー | PR をレビューし、Copilot の作業を反復改善して次の手順を選択 |

## 前提条件

参加前に、次を確認してください。

- [ ] GitHub アカウントで、**Copilot Student、Pro、Pro+、Business、Enterprise** のいずれかの有効なプランを利用していること
- [ ] アカウントまたは組織で Copilot cloud agent が有効になっていること

> [!TIP]
> 有料プランを利用していませんか？検証済み学生は [GitHub Education][callout-student-plan-education] から GitHub Copilot を無料で利用できます。**Copilot Student** プランには、このワークショップで使用するエージェント、MCP、コードレビュー、Copilot CLI が含まれます。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> Cloud agent は、Copilot Free を除く **Copilot Student、Pro、Pro+、Business、Enterprise** で利用できます。Copilot Business または Enterprise では、管理者が組織で有効化する必要があります。

> [!NOTE]
> このワークショップでは MCP は扱いません。MCP サーバーの利用を確認するには、[CLI ワークショップ](../cli/) または [VS Code ワークショップ](../vscode/) を参照してください。

## はじめに

**[演習 0: 前提条件から始める →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
