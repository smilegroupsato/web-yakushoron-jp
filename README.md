# web-yakushoron-jp

Web管理｜薬象論｜yakushoron.jp

最終更新日時：2026-06-10 06:42 JST

## 目的

このリポジトリは、薬象論サイト `yakushoron.jp` のWeb公開用ファイルを管理するための正本です。

Notionは内部ノート・研究原本・素材整理の場所として扱い、このGitHubリポジトリはWeb公開用HTML / CSS / 画像 / 静的ファイルの履歴管理と自動公開の起点として扱います。

## 公開サイト

- サイト名：薬象論
- ドメイン：yakushoron.jp
- 公開URL：https://yakushoron.jp/
- 公開形式：静的HTML / CSS / 画像
- サイト方針：医療情報ではなく、薬をめぐる批評・研究ノート

## ディレクトリ構成

2026-06-10時点で確認した主要構成です。

```text
/
├─ README.md
├─ site/
│  ├─ index.html
│  ├─ robots.txt
│  ├─ sitemap.xml
│  ├─ css/
│  │  ├─ style.css
│  │  ├─ hero-fix.css
│  │  ├─ home-tight.css
│  │  └─ doryoku-no-hate.css
│  ├─ pages/
│  │  ├─ introduction.html
│  │  ├─ yakumei-no-jocho.html
│  │  └─ doryoku-no-hate.html
│  └─ assets/
│     ├─ favicon.svg
│     └─ images/
│        ├─ hero-main-clean.png
│        ├─ feature-introduction-clean.png
│        ├─ essay-yakumei-clean.png
│        ├─ essay-doryoku-clean.png
│        ├─ essay-yowai-clean.png
│        ├─ essay-toshi-clean.png
│        ├─ essay-seishin-clean.png
│        ├─ research-axes-clean.png
│        ├─ notes-bibliography-clean.png
│        ├─ hero-desktop-20260521-v2.png
│        ├─ hero-mobile-20260521-v2.png
│        ├─ feature-intro.svg
│        ├─ essay-yakumei.svg
│        ├─ essay-doryoku.svg
│        ├─ essay-yowai.svg
│        ├─ essay-toshi.svg
│        ├─ essay-seishin.svg
│        ├─ note-readings.svg
│        └─ note-biblio.svg
└─ .github/
   └─ workflows/
      └─ deploy.yml
```

## 現在読み込まれているCSS

- トップページ `site/index.html`
  - `site/css/style.css`
- 薬象論序説 `site/pages/introduction.html`
  - `site/css/style.css`
  - `site/css/hero-fix.css`
  - `site/css/home-tight.css`
- 薬名の情緒 `site/pages/yakumei-no-jocho.html`
  - `site/css/style.css`
  - `site/css/hero-fix.css`
  - `site/css/home-tight.css`
- 努力の果て `site/pages/doryoku-no-hate.html`
  - `site/css/style.css`
  - `site/css/hero-fix.css`
  - `site/css/home-tight.css`
  - `site/css/doryoku-no-hate.css`

`hero-fix.css` と `home-tight.css` は初期実装・調整時の経緯が残るCSSです。削除可否は未判断のため、現時点ではファイルを残しています。

## 主要画像ファイル

現在のトップページで主に参照している画像は以下です。

- `hero-main-clean.png`：トップページのメインHero画像
- `feature-introduction-clean.png`：薬象論序説カード用画像
- `essay-yakumei-clean.png`：薬名の情緒サムネイル
- `essay-doryoku-clean.png`：努力では届かないところサムネイル
- `essay-yowai-clean.png`：弱い救済サムネイル
- `essay-toshi-clean.png`：都市身体サムネイル
- `essay-seishin-clean.png`：精神変容物質サムネイル
- `research-axes-clean.png`：Research Axes 背景画像
- `notes-bibliography-clean.png`：Notes / Bibliography 背景画像

過去の実装や予備素材として、以下の画像も残しています。

- `hero-desktop-20260521-v2.png`
- `hero-mobile-20260521-v2.png`
- `feature-intro.svg`
- `essay-yakumei.svg`
- `essay-doryoku.svg`
- `essay-yowai.svg`
- `essay-toshi.svg`
- `essay-seishin.svg`
- `note-readings.svg`
- `note-biblio.svg`

## 画像形式

現在の主要ビジュアルはPNG中心です。初期READMEに記載していたJPEG版のHero画像名は、現行のトップページ実装とは一致しないため削除しました。

SVG素材は、初期サムネイルや仮素材として残しています。現在のトップページでは、主に `*-clean.png` 系の画像を背景画像として読み込み、その上にHTML/CSSで文字を重ねています。

高解像度の生成素材や作り替え用素材は、必要に応じてGoogle Drive側の素材パッケージも参照します。

## 運用ルール

1. Web公開用ファイルは `site/` 以下に置く。
2. GitHubの `main` ブランチに入った内容を、GitHub Actionsで公開サーバへ反映する。
3. FTPでの手動アップロードは原則行わない。
4. FTPパスワード、APIキー、トークン、シークレットはリポジトリに書かない。
5. サーバ情報はGitHub Repository Secretsで管理する。
6. 画像ファイルは必要に応じて手動アップロードし、HTML / CSS / README はGitHub履歴が残るようにコミットで更新する。

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

- 2026-06-10 06:42 JST：READMEの実ファイル構成・画像説明を現状に合わせて更新。トップページにcanonical / OGP / Twitter Card等のメタ情報を追加。
- 2026-06-01：GitHub Actions → ロリポップ等 自動更新運用へ移行開始。
- 2026-05-23：サイト設計・素材パッケージを確定。ヘルター・スケルター画像は1番目案、精神変容物質画像は2番目案を採用。
- 2026-05-21：薬象論序説の初期静的サイトを作成。
