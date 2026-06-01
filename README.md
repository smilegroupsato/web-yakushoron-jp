# web-yakushoron-jp

Web管理｜薬象論｜yakushoron.jp

## 目的

このリポジトリは、薬象論サイト `yakushoron.jp` のWeb公開用ファイルを管理するための正本です。

Notionは内部ノート・研究原本・素材整理の場所として扱い、このGitHubリポジトリはWeb公開用HTML / CSS / 画像 / 静的ファイルの履歴管理と自動公開の起点として扱います。

## 公開サイト

- サイト名：薬象論
- ドメイン：yakushoron.jp
- 公開形式：静的HTML / CSS / 画像
- 初期公開ページ：薬象論序説

## ディレクトリ構成

```text
/
├─ README.md
├─ site/
│  ├─ index.html
│  ├─ robots.txt
│  ├─ sitemap.xml
│  ├─ css/
│  │  └─ style.css
│  └─ assets/
│     ├─ favicon.svg
│     └─ images/
│        ├─ hero-desktop-20260521-v2.jpg
│        └─ hero-mobile-20260521-v2.jpg
└─ .github/
   └─ workflows/
      └─ deploy.yml
```

## 運用ルール

1. Web公開用ファイルは `site/` 以下に置く。
2. GitHubの `main` ブランチに入った内容を、GitHub Actionsで公開サーバへ反映する。
3. FTPでの手動アップロードは原則行わない。
4. FTPパスワード、APIキー、トークン、シークレットはリポジトリに書かない。
5. サーバ情報はGitHub Repository Secretsで管理する。

## GitHub Secrets

GitHub Actionsによる自動デプロイには、Repository Secrets に以下を登録する。

```text
FTP_SERVER
FTP_USERNAME
FTP_PASSWORD
SERVER_DIR
```

意味：

- `FTP_SERVER`：ロリポップ等のFTPS / FTPサーバ名
- `FTP_USERNAME`：FTP / WebDAVアカウント名
- `FTP_PASSWORD`：FTP / WebDAVパスワード
- `SERVER_DIR`：サーバ側の公開フォルダ

## 初回デプロイ

初回は `.github/workflows/deploy.yml` の `dry-run: true` を有効にした状態でテストする。

テストでアップロード対象・公開先ディレクトリに問題がないことを確認してから、`dry-run: true` を削除して本番反映する。

## 更新履歴

- 2026-05-21：薬象論序説の初期静的サイトを作成。
- 2026-05-23：サイト設計・素材パッケージを確定。ヘルター・スケルター画像は1番目案、精神変容物質画像は2番目案を採用。
- 2026-06-01：GitHub Actions → ロリポップ等 自動更新運用へ移行開始。

## 画像形式

公開用リポジトリでは、転送量とGitHub管理のため、ヒーロー画像はJPEG最適化版を使用しています。高解像度のPNG原本はGoogle Drive保存済みの素材パッケージを参照してください。
