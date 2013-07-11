---
layout: post
title: "_config.yml について"
date: 2013-07-11 14:55
comments: true
categories: [octpress]
---

Octpressの設定は、``_config.yml``で行う。

<!-- more -->

``_config.yml``には、ページheaderとして埋め込まれるsite情報を
[YAML形式](http://magazine.rubyist.net/?0009-YAML)で記述する。

```yaml
url: http://bellbind.github.io
title: bellbind.github.io
subtitle: github pages
author: bellbind
simple_search: http://google.com/search
description: >
  put something
```

yamlなので、``description``のように長いテキストは、インデントさせて
マルチラインで記述できる。

また、``date_format``を以下の
[srtrftimeフォーマット](http://doc.ruby-lang.org/ja/1.9.3/method/Time/i/strftime.html)
にすることで、日付は、YYYY-MM-DDになるようにした。

```yaml
date_format: "%F"
```

最後にYAMLの注意点として、key-valueの間のコロンの後ろには
スペース1つが必須です。

```yaml
user:bellbind   # 間違い
user: bellbind  # 正解
```

