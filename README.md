# github-pages-test

Nextra-based documentation site with automatic GitHub Pages deployment.

## 技術スタック

- **Node.js**: 20.17.0
- **Next.js**: Pages Router を使用
- **Nextra**: ドキュメント生成フレームワーク

## 機能

### 1. Nextraサンプルドキュメントサイト
- Nextraを使用した静的ドキュメントサイト
- MDX形式でのドキュメント作成
- レスポンシブデザイン対応

### 2. 本番デプロイワークフロー
- `main`ブランチへのマージで自動的にGitHub Pagesへデプロイ
- 手動トリガーによるデプロイも可能
- ワークフロー: `.github/workflows/deploy.yml`

### 3. PRプレビューワークフロー
- PRが作成されると、PR専用のプレビューページが自動生成
- PRごとに独立したURLでプレビュー確認可能
- PRがクローズされると、プレビューページも自動削除
- ワークフロー: `.github/workflows/preview.yml`

## セットアップ

### 依存関係のインストール

```bash
npm install
```

### 開発サーバーの起動

```bash
npm run dev
```

http://localhost:3000 でドキュメントを確認できます。

### ビルド

```bash
npm run build
```

静的サイトが `out` ディレクトリに生成されます。

## GitHub Pages設定

リポジトリの設定でGitHub Pagesを有効にする必要があります：

1. リポジトリの Settings > Pages に移動
2. Source を "GitHub Actions" に設定
3. `main`ブランチにマージすると自動的にデプロイされます

## ワークフロー

### デプロイワークフロー (deploy.yml)
- **トリガー**: `main`ブランチへのpush、または手動実行
- **動作**: Nextraサイトをビルドし、GitHub Pagesにデプロイ
- **URL**: `https://gniw.github.io/github-pages-test/`

### プレビューワークフロー (preview.yml)
- **トリガー**: PRの作成、更新、クローズ
- **動作**: PR専用のプレビューページを生成・更新・削除
- **URL**: `https://gniw.github.io/github-pages-test/pr-{PR番号}/`
- PRコメントに自動的にプレビューURLが投稿されます

## ドキュメントの追加

1. `pages`ディレクトリに新しい`.mdx`ファイルを作成
2. `pages/_meta.json`でページの順序とタイトルを設定
3. Markdown形式でコンテンツを記述

## ライセンス

ISC