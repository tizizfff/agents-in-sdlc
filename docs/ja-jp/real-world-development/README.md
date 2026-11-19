---
title: "実世界での開発"
slug: ja-jp/real-world-development
authors:
  - geektrainer
lastUpdated: 2026-09-16
---

現実に近いシナリオ、完成度の高いアプリケーション、共有されたバックログを使用して、ソフトウェア開発ライフサイクル全体で GitHub Copilot を体験します。計画、コード作成、動作テスト、プルリクエストのレビュー、エージェントによる作業管理を反復的に行います。

## シナリオ

Tailspin Toys はボードゲームをテーマにしたクラウドファンディングを提供する架空の企業です。ここでは、あなたが同社の新しい開発者としてチームのバックログを担当します。バックログには GitHub Issue が登録されており、フィルタリングやページネーションなどの機能に加え、アクセシビリティやコーディング規約の改善が含まれています。

## 開発環境を選択

GitHub Copilot は、作業場所を問わず利用できます。ビルド方法に合った環境を選択してください。各ワークショップは独自のセットアップから始まり、共有の Tailspin Toys シナリオを使用します。

### [GitHub Copilot CLI][cli]

ターミナルでエージェント型アシスタントを使用します。Plan モードと Autopilot モード、インストラクション、スキル、カスタムエージェント、Playwright MCP、Agent Merge、実用的なスラッシュコマンドを活用します。

### [GitHub Copilot app][app]

エージェントセッションを並行実行し、セッションモードを切り替えてキャンバスで共同作業し、デスクトップアプリから GitHub Issue とプルリクエストを管理します。

### [GitHub Copilot cloud agent][cloud]

GitHub Issue を非同期エージェントに割り当て、作業を誘導し、進捗を監視して、エージェントが作成するプルリクエストをレビューします。

### [Visual Studio Code][vscode]

エディターを離れずに、Visual Studio Code と GitHub Codespaces で GitHub Copilot を使用します。Copilot Chat のエージェントモード、MCP サーバー、カスタムエージェントを利用します。

[cli]: cli/
[app]: app/
[cloud]: cloud/
[vscode]: vscode/
