[English README is here](https://github.com/Pumi1a/BURUPURO-TIMER/blob/main/README-en.md)

Qiita にも記事として投稿してあります。記事リンクは[こちら](https://qiita.com/Pumila/items/ef72f110f8f5e8fad1df)から。
## はじめに
BLUE PROTOCOL（以下、ブルプロ）の昼夜切り替えタイミングを通知してくれる Discord Bot を作成しました。作ろうと思った経緯はブルプロをやっている方なら分かると思います。ブルプロには昼限定や夜限定湧きのネームドボスが存在します。そして、昼夜は 25 分で切り替わります。しかし、ミッション中や、自由探索に入っていると今、昼なのか夜なのか分からないのです。また、他の作業をやりながら、夜湧きネームドのためにブルプロを起動するという方もいると思います（私が現にそうでした）。そのために、昼夜切り替えタイミングを通知してくる Bot を作成しました。

## 注意点
エラー報告は開発者の [Twitter](https://twitter.com/Pumi1a) か [github](https://github.com/Pumi1a/BURUPURO-TIMER) までお知らせ下さい。様々な条件で検証をしたつもりですが、私が Python 初心者なこともありバグがあると思います。申し訳ありません。現時点で把握しているバグについては最後の方で記載しています。上手く動作しない時は `/reset_server` コマンドを実行して再設定してみて下さい。

なお、利用しているホスティングサービスは "Railway" になります。性能はメモリが 8GB、CPU が 8 コアになります。そこまで負荷のかかる Bot ではないと思いますが、もしかしたら安定しなくなるかもしれません。"Railway" については以下記事にまとめています。

https://qiita.com/Pumila/items/29f26fb349d5592046ae


## 導入方法
**注意：Bot の導入はサーバの管理者権限を持っている方しか出来ません。**

[こちら](https://discord.com/api/oauth2/authorize?client_id=1127823303369834578&permissions=3072&scope=bot%20applications.commands)からクリックしてログイン後、導入したいサーバを選択して[はい]、続いて認証を押下して下さい。ロボットかどうかの確認画面でチェックして導入完了です。
必要なくなったら、サーバ負荷軽減のために追放して頂けると助かります。

## 使い方
**注意： 5 分おきにサーバ情報の更新を行っていますが、スラッシュコマンドの実行のタイミングによっては、期待通りの挙動を示さないことがあります。** 例えば、通知先のチャンネル変更したのに、デフォルトの通知先に通知される、通知をオフにしたのに通知されるなどです。これらに関してはプログラムの仕様上の問題なのでご了承下さい。

**また、基準時間を設定しないと Bot による投稿はされません。**

**Bot を再デプロイしたときには再度設定をお願いします。データベースの用意が面倒なので、サーバごとの設定はデータベースに保存していません。ご了承下さい。**

### 各スラッシュコマンドの説明
Bot の各スラッシュコマンドについて説明していきます。スラッシュコマンド実行時に以下のようなエラーが出たときはもう一度コマンドを試してみて下さい。

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ad29da08-18cc-0377-f841-a0c0b9fa2655.png)

#### 通知先のチャンネルを変更する
通知先のチャンネルを変更することができます。デフォルトはシステムメッセージのチャンネルになっています。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/set_channel` を選択して下さい。
2. 通知をさせたいチャンネル名を入力し、実行して下さい。候補として挙がっているものから選択しても構いません。
3. Bot に投稿権限がないチャンネル、もしくはテキストチャンネルではないチャンネルを選択した場合、以下のような警告が出ます。`Warning: No permission to post in the channel {new_channel.name}.`, `{new_channel.name} is not a text channel.`。
3. Bot から `Set channel to {new_channel_name}.` とメッセージが来ます。

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/935ca7eb-0d9e-f222-600e-b67538ad1402.png)

#### 基準時間を設定する
昼夜切り替えのタイミングを設定することができます。各サーバで切り替えタイミングが異なっていたり、メンテナンスなどでズレる可能性があるため、自動で設定はしません。ユーザが昼夜切り替えのタイミングを入力するようにしています。入力する時間は過去の時間でも問題ありません。

エラーなどによりきちんと投稿されないことがあります。基準時間を現時刻の30分前くらいに設定して、投稿されるのを確認してから正しい基準時間を設定することをおすすめします。投稿されなかったら、`/reset_server` コマンドを実行して再度設定してみて下さい。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/set_day_base_time` または `/set_night_base_time` を選択して下さい。`set_day_base_time` では、昼になったタイミングを設定するコマンドで、同時に夜の時間も設定してくれます。逆に `set_night_base_time` では、夜になったタイミングを設定するコマンドで、同時に昼の時間も設定してくれます。
2. どちらか都合のいいコマンドを選択し、時間を入力してコマンドを実行して下さい。
3. Bot から `Day base time set to: {hour}:{minute}. The night base time is set to: {hour}:{minute}.` とメッセージが来ます。

<img width=300 src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/4f06aa25-460a-ab9b-57ae-0737c6dc347c.png"><img width=300 src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/19d8706b-3d62-82a5-fb77-f165967f85b8.png">

#### 昼夜のどちらかを通知、または両方を通知する
昼夜のどちらかだけ通知をさせたいという方もいますよね（夜限のネームドは夜だけ通知させればいいわけですし）。そこで、昼夜両方を通知させるか、昼夜のどちらかだけ通知させるかを設定することができます。デフォルト値は両方通知するようになっています。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/set_state` を選択して下さい。
2. 選択肢として、[Day, Night, Both] が挙がると思います。夜だけ通知させたい方は、`Night` を、昼だけ通知させたい方は `Day` を選択して実行して下さい。やっぱり両方通知させたくなったら、 `Both` を選択して下さい。
3. Bot から `State set to: {state}` とメッセージが来ます。

![4.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ddcd4da3-2486-7e55-2cad-58b22a1ac6ce.png)

#### 通知するタイミングを「あと何分で昼/夜になります」と変更する
昼夜ピッタリに通知が来ても、ゲームを起動してネームド討伐に間に合わないよという方のために、「あと何分で昼/夜になります」と通知方法を変更させることができます。デフォルト値は 0 です。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/notify_in_advance` を選択して下さい。
2. 次にどれくらい前に通知させたいかを分単位で入力し実行して下さい。
3. Bot から `Will now notify {minutes_before} minutes in advance.` とメッセージが来ます。

![5.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/b6d3089b-17d2-da45-29e8-a064da134e43.png)

#### 常に通知するか選択する
常に昼夜のタイミングを通知するか設定することができます。デフォルト値は `True` です。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/set_persistent_posting` を選択して下さい。
2. 選択肢として、[True, False] が挙がると思います。常に通知させたくない方は、`False` を選択して下さい。
3. Bot から `Set persistent_posting to {new_value}.` とメッセージが来ます。

![6.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ee389fe1-6d6e-bb89-a848-eedc968c8ff2.png)


#### 一時的に通知するか選択する
一時的に昼夜のタイミングを通知するか設定することができます。デフォルト値は `False` です。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/set_temporary_posting` を選択して下さい。
2. 選択肢として、[True, False] が挙がると思います。一時的に通知させたい時に、`True` を、もう通知させなくてよくなったら `False` を選択して下さい。
3. Bot から `Set temporary_posting to {new_value}.` とメッセージが来ます。

![7.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/d849bba8-72d0-b2d9-7097-5b46116d6eb0.png)

機能的には `/set_persistent_posting` で補える機能ですが、一応作っておきました。どちらを使用しても構いません。

#### 設定を初期設定にリセットする
各種設定を初期設定にリセットすることができます。上手く投稿がされない時などに使用してみて下さい。
1. "/" を入力して、ブルプロタイマーのアイコンをクリックし、コマンド一覧から、`/reset_server
` を選択して実行して下さい。
2. Bot から `Server configuration has been reset. Default post channel set to {channel.name}. Please input your settings.` とメッセージが来ます。

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/53e9d72e-0ac3-9a23-ccf0-4996e17a3f02.png)

## 現時点で把握しているバグ

## 現時点での要望

## 最後に
ブルプロ楽しいーーーー！！！オロチの「生命の奔流」全然出ねええええええええ（くそがぁーーーーー）。オロチ 11 体厳選しましたよ…そのために、50 分間隔でタイマーをかけながら、他の作業をしていたのですが、これ Bot で自動化できるんじゃねと思い作成しました。ぜひ使ってみて下さい。
サーバの維持費用のために、この Bot を気に入ってくれた方はご寄付して頂けると助かります。

【Amazon ギフト券 受取人：yskl6695@gmail.com】

https://www.amazon.co.jp/dp/B004N3APGO

【PayPal】

https://www.paypal.com/paypalme/IrsPumila

ご意見、ご感想、ご要望、エラー報告などは[Twitter](https://twitter.com/Pumi1a) まで。

