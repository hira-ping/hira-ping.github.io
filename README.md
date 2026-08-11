# My Wiki

ストック型の情報管理を目的とした構築

## 使用技術・テンプレート
* **静的サイトジェネレーター:** [Hugo](https://gohugo.io/)
* **テーマ:** [Hugo Relearn Theme](https://mcshelby.github.io/hugo-theme-relearn/)
* **アイコン:** Font Awesome 6

## セットアップ時の主なカスタマイズ内容

デフォルトのRelearnテーマから、以下のカスタマイズを行った。

### 1. デザイン・レイアウトの変更
* **テーマカラーの変更**
  * `hugo.toml` にて `themeVariant = "zen-light"` を指定し、白黒ベースのデザインに統一。
* **オリジナルロゴの適用**
  * `layouts/partials/logo.html` を作成し、デフォルトのテキストロゴを画像に上書き。
  * CSS（Flexbox）を用いてロゴとタイトルの余白を調整。
  * `border-radius: 50%` と `object-fit: cover` を指定し、画像を綺麗な円形に切り抜き表示。

### 2. トップページ（Home）の構成
* **最近の更新リストの自作**
  * `layouts/shortcodes/recent.html` を作成し、直近で更新されたページの上位5件を自動取得して表示するショートコードを実装。
* **サイトマップの自動表示**
  * `content/_index.md` にて `{{% children depth="2" %}}` を使用し、Notebook以下の階層構造を自動的に目次として表示。

### 3. サイドバー・ナビゲーションの調整
* **アイコンの最適化**
  * 各ページのフロントマター（`menuPre`）にて、Font Awesome 6（`fa-solid` など）のアイコンを指定。
  * アイコンとテキストが詰まるのを防ぐため、閉じタグの直後に半角スペース（または `&nbsp;`）を挿入して余白を確保。
* **外部リンク（ショートカット）の追加**
  * `hugo.toml` の `[[menu.shortcuts]]` を用いて、X (Twitter)、note、LinkedIn、GitHub への導線を設置。
  * フロー情報（SNSなど）との役割を明確に分離。

### 4. リンクの挙動変更
* **外部リンクを別タブで開く設定**
  * `hugo.toml` に `externalLinkTarget = "_blank"` を追加し、サイト外へのリンクがデフォルトで新しいタブで開くように変更。
  * ショートカットメニューにも個別に `[menu.shortcuts.params] target = "_blank"` を設定。

### 5. バージョン管理（Git）の設定
* `.gitignore` を設定し、自動生成される不要なファイル群（`/public/`, `/resources/`, `.hugo_build.lock` 等）を追跡対象から除外してリポジトリを軽量化。

## ローカルでの起動方法

リポジトリをクローン後、以下のコマンドでローカルサーバーを立ち上げてプレビューできる。

```bash
hugo server -D