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