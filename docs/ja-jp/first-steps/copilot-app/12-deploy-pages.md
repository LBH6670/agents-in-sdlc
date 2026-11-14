---
title: "レッスン 12 - GitHub Pages でサイトをデプロイする"
description: "GitHub Copilot app を使って Pages ワークフローを設定し、その pull request をレビューして、公開された Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Space Quiz を GitHub Pages にデプロイして、誰でもアクセスできる場所に公開します。Copilot はワークフローを準備してデプロイを案内できますが、変更をレビューし、サイトが公開されたことを確認するのはユーザーの責任です。

このレッスンでは、次の操作を行います。

- Copilot に GitHub Pages へのデプロイ設定を依頼します。
- マージする前に、ワークフローと pull request をレビューします。
- デプロイを確認し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、誰でも簡単に試せる方法がまだありません。単一ファイルのサイトを GitHub Pages で公開すると、サーバーやランタイム依存関係を追加せずに公開 URL からアクセスできるようになります。

## Copilot にデプロイの準備を依頼する

> [!WARNING]
> pull request を作成すると、コードがコミットおよびプッシュされる場合があります。このプロンプトを送る前に、承認設定と送信先のリポジトリを確認してください。**Approve all** を選択している場合、別の確認プロンプトが表示されるとは限りません。

`space-quiz` の Copilot app セッションで、次のプロンプトを送信します。

```plaintext
このリポジトリに GitHub Pages のデプロイを準備してください。必要に応じて Web サイトをビルドし、変更が既定のブランチに反映された後に GitHub Pages へデプロイする GitHub Actions ワークフローを作成してください。README がまだない場合は、アプリの説明とローカルでの実行方法を記載した README を追加してください。これらの変更を含む pull request を作成し、そのリンクと必要な Pages の設定または権限を報告してください。マージ、自動マージの有効化、Pages 設定の変更、デプロイは行わないでください。停止して、レビューを待ってください。
```

## ワークフローと pull request をレビューする

1. リポジトリに README がまだない場合にのみ追加されていることを確認します。
2. ワークフローのビルドとデプロイの手順、トリガー、権限を含め、pull request の変更をレビューします。
3. マージ前の pull request ではなく、既定のブランチからデプロイするワークフローであることを確認します。
4. 必要な修正を依頼し、更新された diff をレビューします。マージを許可する前に、必須の pull request チェックがすべて成功するまで待ちます。

## マージとデプロイを許可する

> [!WARNING]
> 次のプロンプトは、レビュー済みの pull request のマージ、リポジトリの Pages 設定の変更、サイトの公開をエージェントに許可します。レビューを完了し、リポジトリと pull request を確認した後にのみ送信してください。承認設定によっては、追加の確認なしで実行される場合があります。

`<PR_NUMBER>` をレビューした pull request の番号に置き換え、別のプロンプトとして送信します。

```plaintext
このリポジトリの pull request <PR_NUMBER> をレビューし、マージとデプロイを許可します。GitHub Actions を使う GitHub Pages を有効にし、必須チェックの成功後に限り、その pull request をマージしてください。デプロイが成功するまで監視し、公開サイトの最終 URL を報告してください。Pages の有効化やマージの権限がない場合は、私が何を承認または実行する必要があるかを正確に説明してください。サイトが実際に公開されるまでは、成功したと報告しないでください。
```

![3 段階の図: マージされた Space Quiz の pull request、Build website・Upload artifact・Deploy to Pages の各ステップが成功した GitHub Actions の Deploy website 実行、yourname.github.io/space-quiz/ で公開された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## デプロイを確認する

1. GitHub Actions のデプロイ実行が成功するまで確認します。
2. 報告された URL を開き、Space Quiz が読み込まれることを確認します。

エージェントが Pages の有効化や pull request のマージを行えない場合は、提示された具体的な手順に従ってください。デプロイが成功し、公開サイトが読み込まれるまで、タスクを完了したと見なさないでください。

## まとめと次のステップ

Space Quiz を公開サイトとして利用できるようにし、エージェントの報告に頼らずデプロイを確認しました。[レッスン 13: 振り返りと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
