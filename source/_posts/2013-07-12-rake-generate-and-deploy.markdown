---
layout: post
title: "rake generate and deploy"
date: 2013-07-12 16:49
comments: true
categories: [octopress]
---

config設定や記事ポストなど何か編集をしたら、
以下のコマンドによって、サイトへdeployします。

```bash
rake generate
rake deploy
```

<!-- more -->

以下のコマンドでも同様です。

```bash
rake gen_deploy
```

octopressの提供するrakeのtask一覧は、

```bash
rake -T
```

で表示できます。


