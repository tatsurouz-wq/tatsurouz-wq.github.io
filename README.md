# tatsurouz-wq.github.io

アプリサポートページのGitHub Pagesリポジトリです。

## GitHub Actionsワークフローを停止する方法

このリポジトリではGitHub Actionsワークフローが実行されています。ワークフローを停止したい場合は、以下の方法を使用してください。

### 方法1: GitHubウェブインターフェースから停止する

1. [Actionsタブ](https://github.com/tatsurouz-wq/tatsurouz-wq.github.io/actions)にアクセスします
2. 左側のサイドバーから停止したいワークフローを選択します
3. 実行中のワークフローラン（黄色のマークが表示されている）をクリックします
4. 右上の「Cancel workflow」ボタンをクリックします

### 方法2: ワークフローを無効化する

特定のワークフローを一時的または永続的に無効化するには：

1. [Actionsタブ](https://github.com/tatsurouz-wq/tatsurouz-wq.github.io/actions)にアクセスします
2. 左側のサイドバーから無効化したいワークフローを選択します
3. 右上の「...」（三点リーダー）メニューをクリックします
4. 「Disable workflow」を選択します

### 方法3: GitHub CLIを使用する（コマンドライン）

GitHub CLI（gh）がインストールされている場合：

```bash
# 実行中のワークフローランをキャンセル
gh run cancel <run-id>

# または、最新のワークフローランをキャンセル
gh run cancel $(gh run list --workflow="ワークフロー名" --limit 1 --json databaseId --jq '.[0].databaseId')

# ワークフローを無効化
gh workflow disable <workflow-id または workflow-name>
```

### 方法4: GitHub APIを使用する

REST APIを使用してワークフローを停止することもできます：

```bash
# ワークフローランをキャンセル
curl -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  https://api.github.com/repos/tatsurouz-wq/tatsurouz-wq.github.io/actions/runs/<run-id>/cancel

# ワークフローを無効化
curl -X PUT \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  https://api.github.com/repos/tatsurouz-wq/tatsurouz-wq.github.io/actions/workflows/<workflow-id>/disable
```

## 現在のワークフロー

このリポジトリには以下のワークフローが設定されています：

- **Copilot coding agent**: GitHub Copilotによるコーディング支援ワークフロー
- **pages-build-deployment**: GitHub Pagesのビルドとデプロイメントワークフロー

## 参考リンク

- [GitHub Actions ドキュメント](https://docs.github.com/ja/actions)
- [ワークフローの管理](https://docs.github.com/ja/actions/managing-workflow-runs)
- [GitHub CLI](https://cli.github.com/)

## ライセンス

© Tatsuro Furuya
