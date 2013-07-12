---
layout: post
title: "new pageとテンプレートレイアウトのカスタマイズ"
date: 2013-07-12 17:13
comments: true
categories: [octopress]
---

octopressは、[jekyll](http://jekyllrb.com/)に、blogスタイルの
テンプレート構造とrake管理タスクをかぶせたものです。
markdownやyaml等で書くソースをHTMLにするのは、jekyllの機能です。

jekyllは、任意のサイト構造を構成することが可能で、
octopressからも、若干手間がかかるけど、任意のページやリソースを配置する
ことができます。

<!-- more -->

## 画像ファイル、JSファイル

ファイルは、``source/``以下の任意の位置に配置でき、``rake deploy``で
同じパス上にアップロードされます。
postなどからハイパーリンクを張るだけです。

## 枠付きページ

rakeコマンドで作成することができます。

```bash
rake new_page[path/to/page]
```

すると``source/path/to/page/index.markdown``というファイルが生成されます。
postと同様に編集して、``rake generate`` & ``rake deploy``すれば、
postと同様な枠のついたかたちで、アップロードされます。

ただし、postと違ってトップページから自動でリンクが貼られることはありません。

## フレームレイアウトの編集

たとえば、新しく作ったページを"Blog"や"Archives"と並ぶ
リンクとして追加したい場合は、
``_inlucdes/custom/navigation.html``をエディタで編集し、追加します。

```html
<ul class="main-navigation">
  <li><a href="{{ root_url }}/path/to/page/">My Page</a></li>
  <li><a href="{{ root_url }}/">Blog</a></li>
  <li><a href="{{ root_url }}/blog/archives">Archives</a></li>
</ul>
```

## 枠付HTMLページ

rakeコマンドで``.html``をつけて作成すると、枠付のHTMLを
生成するページソースを作成できます。

```bash
rake new_page[path/to/page/index.html]
```

この場合もやはりヘッダ情報YAML入りのファイルが、
``source/path/to/page/index.html``にできます。

この中身には、HTMLボディに入れる要素を記述します。

```html
<div>
...
</div>
```

``rake generate``によって、このまわりに枠がついた
HTMLファイルが生成されます。
