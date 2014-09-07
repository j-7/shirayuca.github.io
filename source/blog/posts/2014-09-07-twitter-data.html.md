---
title: GoogleスプレッドシートでTwitter検索結果のデータ収集
date: 2014-09-07 23:12 JST
tags: データ
---

<br />

Googleスプレッドシートを使って、任意のキーワードでTwitter検索をした結果のデータを収集します。最初の設定に少しだけ手間がかかりますが、1度設定すれば、あとは勝手にデータを収集し続けてくれるので、お手軽で便利です。作成は基本的に、下記のブログで紹介されているスクリプトをベースとしており、そこから特定セルに検索キーワードを入れるなどの加工を行っています。大変お世話になりました、ありがとうございます。

- http://blog.hika69.com/blog/2014/01/28/google-apps-script/


<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter1.png">


<br />
#### 手順

1. Twitterアプリの作成
2. GoogleスプレッドシートとTwitterアプリの連携
3. Googleスプレッドシートでスクリプトの編集
4. データのフィルタリングや集計


<br />
#### 1. Twitterアプリの作成
[Twitter Developers](https://dev.twitter.com/)の[Twitter Application Management](https://apps.twitter.com)にてアプリケーションを作成し、データ収集に必要なAPIキー等を取得します。私は下記のように入力しました。

- Name: for GoogleAppsScript(任意の名前)
- Description: GoogleAppsScriptから利用します(任意の説明)
- Website: http://shirayuca.github.io/ (任意のURL)
- Callback URL: https://spreadsheets.google.com/macros (左記と同じように入力)

作成すると、`API key`と`API secret`が発行されます。


<br />
#### 2. GoogleスプレッドシートとTwitterアプリの連携
任意の名前でGoogleスプレッドシートを作成します。その後、メニューバーから`ツール > スクリプトエディタ`を選択します。ここでも任意のプロジェクト名をつけてください。

続いて、スクリプトエディタのメニューバーから`リソース > ライブラリ`を選択し、「ライブラリを検索」に`MHGYgT-unu1fC7zXOkNfBUVSHJARy_IP7`と入力します。その後、選択ボタンを押して、Twitterのライブラリが表示されたら、バージョンを「1」として保存します。

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter2.png">

その後、スクリプトエディタのメニューバーから`ファイル > プロジェクトのプロパティ`を選択し、ユーザープロパティのタブで、Twitterアプリ作成時に発行された`API key`と`API secret`を下記のように入力します。入力し終えたら、保存します。

- `TWITTER_CONSUMER_KEY` に `API key`
- `TWITTER_CONSUMER_SECRET` に `API secret`


<br />
#### 3. Googleスプレッドシートでスクリプトの編集
コード.gs上に、下記のGistスクリプトをコピーし、保存してください。

- https://gist.github.com/shirayuca/88c309c168052d35d29d

スプレッドシートに戻り、A1に検索キーワードを入力してください。データは、4行目以降(A4セル以降)に出力されます。そのため、下表のように、3行目のA3セルからF3列に、適宜列名を付与するといいでしょう。

|	セル	|	列名	|
|-----------|------------|
|	A3	|	ID	|
|	B3	|	日時	|
|	C3	|	tweet	|
|	D3	|	tweetURL	|
|	E3	|	USER	|
|	F3	|	tweet内URL	|

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter3.png">

その後、スクリプトエディタに戻り、メニューバーから`実行 > myFunction`で、スクリプトを実行します。初回実行時のみ、色々な承認のアラートが出るので、OKとしてください。

定期的に検索し、データを蓄積していきたい場合は、スクリプトエディタのメニューバーから`リソース > すべてのトリガー`に移動し、「新しいトリガーを追加」して、myFunctionを定期的に実行するタイマーを指定します。下記の画像の例では、30分ごとに検索を行っています。トリガーの初回起動時にも承認アラーとが出るので、OKとしてください。

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter4.png">


<br />
#### 4. データのフィルタリングや集計
収集したデータは、適宜フィルタリングや加工を行うことで、より扱いやすくなります。簡単な例を下記のスプレッドシートにまとめました。下記のシートは、データをある程度収集した後、値のみを貼付けて、今回のフィルタリングや集計をわかりやすく説明するために作成した例です。実際にスクリプトを定期的に動かし続けている場合には、集計データもリアルタイムに変更されます。今回は、「ミューズリー」という検索キーワードを設定しています。

- https://docs.google.com/spreadsheets/d/1bDv7IbcHYRt8OFHs5SoSiGIY_mIcjugS2qlvEeum1bA/edit?usp=sharing

収集したtweetに特定の文字列が含まれているかどうかを確認したい場合には、下図のように、任意の列を作成し、その文字列を含んでいる場合に「1」というフラグを立てます。例として、H4セルには`=countif($F4,"*"&H$3&"*")`と入力しています。これは、tweet内URLを表示しているF列に、H3セル「pic」を含んでいるか否かを判定するものです。(tweet本文では、URLは全て短縮URLt.coで表示されるため、別途本文内URL列を作っています。)

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter5.png">

また、新しいシートを作成し、本文内URLのみの一覧を表示することも簡単です(「URLのフィルタ」シート参照)。スプレッドシートのFILTER関数を用いて、`=filter('シート1'!F:F,'シート1'!K:K=1)`のように条件をつけると、データのあるシート1上のF列に関して、先ほど「1」というフラグを立てた行の本文内URLのみを表示できます。本文内URLのみの一覧は、Amazonへのリンクがどれくらいあるか、その内容はどのようなものかを確認したい際などに役立ちそうです。

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter6.png">

同様に、FILTER関数を用いて、特定のキーワードを含むtweetの一覧のみを別途表示することも可能です(「発言のフィルタ(ダイエット)」参照)。

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter7.png">

また、特定の文字列がどの程度出現しているかのグラフを作成することもできます(「具材のグラフ」シート参照)。シート1にて、特定の文字列を含んでいる場合に「1」としたため、それを合計すれば、出現頻度となります。下記の例では、ミューズリーと合わせる具材は何が人気かがわかります。

<img src="http://shirayuca.github.io/blog/2014/09/07/twitter-data/twitter8.png">

集計方法に関しては、月別の集計や推移など、色々な観点で行うことができそうです。

<br />