---
title: 毎日、Amazonの特定商品の価格を取得する
date: 2015-05-16 18:50 JST
tags: GoogleAppsScript
---

<br/>

毎日、Amazonの特定商品の価格を取得するGoogleスプレッドシートを作成しました。元々、担当授業でもスプレッドシートを活用してスクレイピングを試みていましたが、アクセスしたその瞬間のスナップショットを取得するというものでした。定期的にスクレイピングする方法も行ってみたいと思い（例えば、何かのスコアを毎日取得するなど）、今回、Amazonの特定商品の価格を例に行いました。下記のA列、B列に毎日データが追加されていきます。グラフ化等行うと面白そうですね。

- [Amazon価格の取得シート](https://docs.google.com/spreadsheets/d/1BVZH0-Vpvg6-FR3XJ4_b3_mimkU4FKVBQ3Tpg7YT6SQ/edit?usp=sharing)

<a href="https://docs.google.com/spreadsheets/d/1BVZH0-Vpvg6-FR3XJ4_b3_mimkU4FKVBQ3Tpg7YT6SQ/edit?usp=sharing"><img src="http://i.gyazo.com/4d9e5dca1e3bfb1d06d979716be3d6bf.png", width="600"></a>


<br />
#### 使い方
1. 上記で公開しているシートをコピー
2. E1セルに任意のAmazon商品ページを入力
3. トリガーを設定（私は、毎日取得という方法にする予定です）


シートをコピーして使用しない場合は、下記のコードをスクリプトエディタに貼り付けて使用します。

<script src="https://gist.github.com/shirayuca/01c62520329566a82dcb.js"></script>


<br/>
#### 参考
- http://www.bmoo.net/archives/2012/04/313841.html
- http://engineer-intern.jp/archives/7551

<br/>

