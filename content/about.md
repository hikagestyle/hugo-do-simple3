+++
title = "あばうと"
date = 1999-01-01T00:00:00+09:00
+++

あばうとのページ。

<img src="../images/1920x1080.jpg" alt="サンプル画像" width="50%">

これは<span style="color: red; ">赤文字</span>です。


![サンプル画像](../images/1920x1080.jpg)

画像は「static/images」へ入れて管理していく方針。
- themes/テーマ名/static では無い

固定ページと記事投稿は、相対リンクの階層が異なるので、記述に注意する。

記事投稿
- ../../images/xxx.jpg
- `![テキスト](../../images/xxx.jpg)`

固定ページ
- ../images/xxx.jpg
- `![テキスト](../images/xxx.jpg)`


## 環境

- x230（Lenovo ThinkPad）
- LinuxMint 20.3


## 補足

サクッと使う個人的な用途で小規模を想定。

blogフォルダへ投稿を詰め込んで、タグで仕分けるイメージ。

HUGOで個人的に使うシンプルなテーマ。

短時間で作ったので、大雑把にやっつけです。


## 基本的な仕様

ドメイン直下、サブディレクトリでも、とりあえず使えるはず。（hugo.tomlのbaseURLによる）

- hugo v0.127.0
- pure.css
- hugo.toml（config.toml）
	- baseURL（最後のスラッシュ有り）
- toml形式を採用（記事投稿のデフォルト設定）
- カテゴリー無し
- タグ（tags）有効
- 投稿のタグ付けは日本語を使わないようにする（翻訳・英訳）
- デフォルトは、10件ごとのページ送り
	- hugo.toml,Paginate = 10
	- blog
	- tags/xxx
- 固定ページ（デフォルト:日付表示なし）
	- hugo-do-simple3/layouts/_default/single.html
	- コメントアウト
- メニューページ（固定ページ）

[マークダウン](../tags/markdown/)


## 注意点と覚え書き

- 記事に「日本語のタグ付け」は避けたほうが良い。（ビルド生成される日本語フォルダは、相性の悪いサーバーがある）
- タグ付けは、半角英数字で小文字が無難。
- タグの並び順は、アルファベット順が無難。（terms.html,Alphabetical,<a href="https://gohugo.io/templates/taxonomy-templates/" target="_blank" rel="nofollow noopener noreferrer">Taxonomy Templates</a>）
- 多機能なので、シンプルに記事投稿へ集中するほうが負担は少ない。
- hugo.tomlは、記述のルールや順番がある。（<a href="https://gohugo.io/getting-started/configuration/" target="_blank" rel="nofollow noopener noreferrer">Configure Hugo</a>）


## ビルドまでの流れ

- hugo.tomlの編集
	- baseURL(最後のスラッシュ有り)
	- title
	- description
- templatesを必要に応じて編集
	- hugo-do-simple3/layouts/partial/_analytics.html
	- hugo-do-simple3/layouts/partial/_sidebar.html
	- hugo-do-simple3/layouts/index.html
- 記事の作成
	- mdファイル(content/blog)
- ローカルチェック
	- hugo server
	- hugo server -D
- ビルド
	- hugo
	- hugo -D
- publicフォルダが生成される


