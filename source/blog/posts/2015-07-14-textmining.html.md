---
title: 次に買うシャンプーの検討
date: 2015-07-14 23:20 JST
tags: 分析
---

<br>
ユーザーローカルからテキストマイニングツールがリリースされていたので、さっそく試してみました。

- http://textmining.userlocal.jp/

<br>
今使っているシャンプーがイマイチ合わないので、次に買うシャンプーを選ぶために、@cosmeの口コミを分析してみます。シャンプーランキング1位と2位を比較してみることにしました（3位はコンディショナーだったため除外）。口コミ数に差がありますが、ツールのお試しということで、気にしません。

- [Ahalo butter(アハロバター)	プレミアムスカルプクリアシャンプー／リペアトリートメント](http://www.cosme.net/product/product_id/10091820/reviews/agg/30/agl/34/msf/1)
- [インフィニティ	エステクレンジング](http://www.cosme.net/product/product_id/10091712/reviews/agg/30/agl/34/msf/1)

両者ともに、購入者かつ30代の口コミのみを抽出しました。口コミデータのスクレイピングは、いつものようにGoogleスプレッドシートの`IMPORTXML関数`を活用しました。

<br>

- [プレミアムスカルプクリアシャンプーの口コミ分析](http://textmining.userlocal.jp/home/file_analyze/f68777665ef12f33265d08ce2cf1f336)
<a href="http://textmining.userlocal.jp/home/file_analyze/f68777665ef12f33265d08ce2cf1f336"><img src="http://i.gyazo.com/e03a68801c7c14d1d215a0e3ff56a210.png" width=600px /></a>

<br>

- [エステクレンジングの口コミ分析](http://textmining.userlocal.jp/home/file_analyze/b5b069ca0879d4148b6ae8f3825485b1)
<a href="http://textmining.userlocal.jp/home/file_analyze/b5b069ca0879d4148b6ae8f3825485b1"><img src="http://i.gyazo.com/368f7e368b0060a7eed0823e9c7d4383.png" width=600px /></a>

<br>

どちらのシャンプーも、「泡立つ」や「サラサラ」は共通のワードのようです。

しかし、1位のプレミアムスカルプクリアシャンプーの方は、スカルプトリートメントや抜け毛といった単語も目立ちます。夏で暑いこともあり、頭皮の状態や抜け毛がちょうど気になるところだったので、次はこちらのシャンプーを試してみたいと思います。

<br>
