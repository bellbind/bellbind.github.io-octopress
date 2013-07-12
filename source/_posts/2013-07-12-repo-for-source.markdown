---
layout: post
title: "ソース用リポジトリへ保存する"
date: 2013-07-12 17:47
comments: true
categories: [octopress, git]
---

octopressのdeployで、リポジトリ``username.github.io``にアップされるのは、
あくまで生成結果のファイル群だけです。ソースはアップされません。

ソースもアップするには、別途ソースのためのリポジトリを用意し、
そこにoctopress全体をアップします。

<!-- more -->

github pages用に設定したoctopressは、branchが``source``になっています。
そこで、あらためてアップロード用に``master``ブランチを用意します。

```bash
git checkout -b master
```

編集したファイルを追加し、masterにcommitします。

```bash
git add source
git add _config.yml
git commit -m "add my posts"
```

つづいて、github上でアップロードするための空リポジトリを用意します。
その名前を``username.github.io-octopress``とします。

リモートの設定します。

```bash
git remote add origin git@github.com:username/username.github.io-octopress
git config branch.master.remote origin
```

そしてpushすればアップロードされます。

```bash
git push -u origin master
```

## 日々の更新アップロード

post等のみで、configを編集しないのであれば、

```bash
git add source
git commit -m "new posts"
git push
```

でアップロードできるでしょう。

## octopress本家の更新のマージ

octopressでは、オリジナルのリモートブランチが"octopress"に設定されます。
よって、以下によって本家の更新を適用できます。

```bash
git pull octopress master
```

