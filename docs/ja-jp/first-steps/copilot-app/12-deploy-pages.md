---
title: "レッスン 12 - GitHub Pages でサイトをデプロイ"
description: "GitHub Copilot app を使用して Pages ワークフローを構成し、プルリクエストをレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

GitHub Pages を使用して Space Quiz を公開します。Copilot はワークフローの準備とデプロイ手順の案内を支援しますが、変更のレビューとサイトの公開確認はユーザーの責任です。

このレッスンでは、次の操作を行います。

- Copilot に GitHub Pages のデプロイ構成を依頼します。
- マージ前にワークフローとプルリクエストをレビューします。
- デプロイを確認し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、利用者が簡単に試せる方法が必要です。GitHub Pages で単一ファイルのサイトを公開すると、サーバーやランタイム依存関係を追加せずに、公開 URL から利用できるようになります。

## Copilot にデプロイを準備してもらう

> [!WARNING]
> プルリクエストを作成すると、コードがコミットおよびプッシュされる場合があります。プロンプトを送信する前に、承認設定とデプロ先リポジトリを確認してください。**すべて承認**を選択すると、別途確認プロンプトが表示されない場合があります。

`space-quiz` の Copilot app セッションで、次のプロンプトを送信します。

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## ワークフローとプルリクエストをレビュー

1. リポジトリに README がない場合にのみ追加されていることを確認します。
2. ワークフローのビルド・デプロイ手順、トリガー、権限など、プルリクエストの変更を確認します。
3. ワークフローが、未マージのプルリクエストではなくデフォルトブランチからデプロイすることを確認します。
4. 修正を依頼し、更新された差分をレビューします。マージを承認する前に、必要なプルリクエストチェックがすべて成功するまで待機します。

## マージとデプロイを承認

> [!WARNING]
> 次のプロンプトは、エージェントにプルリクエストのマージ、リポジトリの Pages 設定変更、サイト公開を承認します。レビューを完了し、リポジトリとプルリクエストを確認してから送信してください。承認設定によっては、追加の確認プロンプトなしでこれらの操作が実行される場合があります。

レビューしたプルリクエストの番号で `<PR_NUMBER>` を置き換えて、次の別プロンプトを送信します。

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![マージされた space-quiz のプルリクエスト、Build website、Upload artifact、Deploy to Pages の手順を含む GitHub Actions の Deploy website 実行成功、および yourname.github.io/space-quiz/ の公開中の Space Quiz を示す 3 様式の図。](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 報告された URL を開いて、Space Quiz が読み込まれることを確認します。

エージェントが Pages の有効化やマージを実行できない場合は、提示された手順に従ってください。デプロイが完了し、公開サイトが読み込まれるまでタスクは完了したとはみなさないでください。

## 概要と次のステップ

Space Quiz は公開サイトとして利用できるようになり、エージェントの報告だけに頼らずデプロイを確認しました。[レッスン 13: レビューと次のステップ][next-lesson] に進みます。

[next-lesson]: ../13-review/
