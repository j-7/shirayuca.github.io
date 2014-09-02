---
title: watts.strogatz.game でスモールワールド・シミュレーション
date: 2014-09-02 21:14 JST
tags: ネットワーク分析
---
<br />

R のパッケージ igraph の watts.strogatz.game() 関数を用いて、スモールワールド・シミュレーションを行います。sna パッケージにて紹介されていたものを、igraph にて行った形となります。 igraph と sna では、レギュラーグラフの作り方に違いがあるので、全く同じ結果にはなりません。

<br />
#### ネットワーク図の作成
ランダム性 p について、0、0.2、1の3種類でネットワーク図を作成します。また、平均経路長、クラスター係数、および最短距離マトリックスと特定頂点の最短経路も出します。

<script src="https://gist.github.com/shirayuca/4af16341509466a9be13.js"></script>


<br />
#### 100回繰り返し
ランダム性 p について、0から1まで 0.01刻みに100回繰り返し、その結果の平均経路長とクラスター係数をプロットします。

<script src="https://gist.github.com/shirayuca/0e6e00182086f7149a15.js"></script>


<br />
#### クラスター係数と平均経路長の変化
上記で100回繰り返した結果について、 p = 0 の値で割った、初期値に対する日の変化として片対数グラフを作成します。

<script src="https://gist.github.com/shirayuca/5ea82d0a31dd7b35650a.js"></script>


<br />
#### 参考文献
下記の書籍にて sna パッケージで説明されていたものを応用しました。
- http://www.amazon.co.jp/%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E5%88%86%E6%9E%90-R%E3%81%A7%E5%AD%A6%E3%81%B6%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%82%B9-8-%E9%88%B4%E6%9C%A8-%E5%8A%AA/dp/4320019288