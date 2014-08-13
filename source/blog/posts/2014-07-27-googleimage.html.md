---
title: 各県のラーメン画像
date: 2014-07-27 22:11 JST
tags: ウェブ
---

ふと、「各都道府県 AND ラーメン」で検索した画像一覧があったらおもしろいんじゃないか、と思いました。そこで、「都道府県名 AND ラーメン」のGoogleの画像検索のトップを抽出する Google Apps Script を作成しました。

<p><br /></p>
#### [各都道府県のラーメン画像](https://docs.google.com/spreadsheets/d/1-Bz_JMxg9mqIfAmFxFgEvJArgeF8Z171999wSKQfA7Y/edit?usp=sharing)
<p><br /></p>

<p><a href="https://docs.google.com/spreadsheets/d/1-Bz_JMxg9mqIfAmFxFgEvJArgeF8Z171999wSKQfA7Y/edit?usp=sharing"><img alt="ラーメンシート" src="http://shirayuca.github.io/blog/2014/07/27/googleimage/ramen.png"></a></p>

<p><br /></p>
#### Googleスプレッドシート上での関数等
<p><br /></p>
下記のように関数を作成し、「各都道府県名 AND ラーメン」というキーワードを引数としてURLを取得し、その後該当URLの画像を表示しています。
<script src="https://gist.github.com/shirayuca/204a9d3a269dc8dde883.js"></script>

<p><br /></p>
こちらのスクリプトは、下記の2ページを参考に作成しています。

- http://t-kashima.hateblo.jp/entry/2012/03/11/235755
- http://www.garunimo.com/program/linux/linux43.xhtml


<br />
<br />