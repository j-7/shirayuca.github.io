---
title: ブログエントリ作成方法
date: 2014-07-08 20:18 JST
tags: post
---


ブログのエントリ作成方法のメモです。このブログは、shirayuca.github.io 上に Middleman で作っています。ローカルでは、エントリは、
```/Users/yuca/dev/shirayuca.github.io/source/blog/posts```
に置いています。



+ TITLE に任意のタイトルを入れて、エントリの .md ファイルを作成します。

```
bundle exec middleman article TITLE
```


+ すると、 下記のようにタイトルなどの情報が入った .md ファイルが作成されます。tags には、タグを入れます。

```
---
title: TITLE
date: 2014-07-08
tags: 
---
```


+ 記事を編集します。

+ 記事の確認をします。

```
bundle exec middleman server
```


+ 記事を投稿します。

```
git add .
git status
git commit -m "message"
git push origin middleman
bundle exec middleman build
bundle exec middleman deploy
``` 