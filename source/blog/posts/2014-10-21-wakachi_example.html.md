---
title: Googleスプレッドシートで分かち書きされた要素を数え上げ
date: 2014-10-21 19:11 JST
tags: GoogleAppsScript
---

<br />

Googleスプレッドシートで、分かち書きされた要素を数え上げます。

<br />
#### スクリプト
下記の2つの記事で紹介しているスクリプトを、Googleスプレッドシートの [ツール]→[スクリプトエディタ]から貼りつけ、保存してください。

- http://shirayuca.github.io/blog/2014/10/19/wordcount.html
- http://shirayuca.github.io/blog/2014/10/21/wakachigaki.html

下記のように、各々のスクリプトファイル（〜.gs）を作成します。

<img src="https://qiita-image-store.s3.amazonaws.com/0/48375/27952c95-fb78-bff5-5e87-a26384568ee8.png" width=400px />

<br />
#### 使い方
下記の公開スプレッドシートにて、実際の使い方の例を示しています。

- https://docs.google.com/spreadsheets/d/17SPL31fsaraUZhsxnBTxRZaGiXbYdISFWA_7UV3mKMg/edit?usp=sharing


<br />
##### 手順1：分かち書き
まず、任意のテキスト群を用意します。今回は、素敵な鬼女様（ http://sutekinakijo.com/ ）の新着タイトルを`=IMPORTXML()`関数で取得しました。A2セルにはブログURLが入っています。

```
=importxml(A2,"//h1[@class='article-title']")
```

その後、テキストの隣のセルに、`=wakachigaki()`関数と`=TRANSPOSE()`関数を組み合わせ、分かち書きされた要素を横列に表示します。B2セルにはブログタイトルテキストが入っています。

```
=transpose(wakachigaki(B2))
```

<img src="https://qiita-image-store.s3.amazonaws.com/0/48375/c097dace-a8c5-9243-7991-23a2558e8bbf.png" width=800px />

<br />
##### 手順2：数え上げ
新しいシート上で、`=wordCount()`関数を実行し、先ほど横列に順次表示された分かち書き後要素を数え上げます。`=wordCount()`関数では、分かち書きされた要素がある範囲全てを参照してください。

<img src="https://qiita-image-store.s3.amazonaws.com/0/48375/4e7910a5-bf4d-8d99-6ec7-92a8f3ad8a1a.png" width=300px />

数え上げ結果は、新しいシートで値として貼付けしソートする等、適宜活用してください。

![5.png](https://qiita-image-store.s3.amazonaws.com/0/48375/b6679f12-5588-713c-89e1-2410b1106b98.png)



<br />
#### 参考
- http://chasen.org/~taku/software/TinySegmenter/


<br />