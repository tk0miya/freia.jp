:date: 2007-03-04 19:02:01
:categories: ['Event', 'python', 'turbogears']
:body type: text/x-rst

===========================================================
2007/03/04 動画配信奮闘記 in Python Developers Camp 2007 冬
===========================================================

*Category: 'Event', 'python', 'turbogears'*

結論から言うと、動画配信に素人が手を出してはいけない。とってもアブナイ。

ページ右にあるのが、今回自分がキャンプに参加してそれぞれなにに時間を割いたかまとめてみたグラフ。簡単にまとめると、

- 撮影関連	42%
- TGハック	28%

開発:撮影関連 = 2:3 ということで、開発よりも撮影の方が長い！なんだそりゃ！その分寝る時間を削ったりしたら1日4時間未満の睡眠時間になってしまった。いったいどこのですマーチですか、これは。

とりあえず帰ってきて片付けも済んだので、次ははまらないように問題点をメモしておこう。



.. :extend type: text/x-rst
.. :extend:

1日目
-------

今回事前に分かっていたネックはたくさんある。ほんとにたくさんある。

- 各担当者・機器が現地でやっとそろう

  - 配信担当者(自分)
  - カメラ(jun-g)
  - エンコードPC(kinoshita)
  - 配信サーバー(nakaj_)

- ネットワークは宿(`銀嶺`_)のものを借用

  - ルーターはいじれない
  - 現地に行くまで状況が分からない

- 動画配信経験者がいなかった
- IEEE1394搭載WindowsPCが動画中継にはつらいスペックだった


こんな状態なので、いろいろなトラブルがあるだろうなあと思って機器類をバッグに詰め込んだら大変なことに。バッグにスキー道具は一切入っていないのに **25kg** ぐらいあった。バカじゃないかと。雪山に何しに行くのかと。そして現地で配信のテストをしようとしたら案の定問題が。

- 配信に使おうと思っていた18080ポートが開いてない

最初の配信の30分前だったのでポート番号を変えて実験する余裕もなく、とりあえずPuTTYを入れてssh port forwardingで配信。この方法はCPU負荷と帯域負荷が少し高いのが欠点。あとkeep alive用に ``ping -i 10 localhost`` とかやってても時々sshが切れてしまったのであまりよい代替手段ではなかった。最初の配信ではもう一つ問題があって

- 320x240 15fps では処理が間に合わなかった(音飛びした)

これは使用した中継PCが `VAIO-U3`_ でCPUがTM5800 933MHzだったから。でもこれ以外用意できなかったんだからしょうがない。回線的には100kbps程度なので問題なし。しょうがないので、320x240 10fpsに設定を変えたところ、なんとか音声も音飛び無しでいけるようになった。

その後、発表形式の合間にデータを吸い出してGoogleVideoに上げる予定だったのだが、合間の時間にデータを取り出そうにも等速でしかとりだせない。そしてタイムスケジュール的に取り出してる余裕はほとんどなかった。

- データ吸い出し用デバイスはカメラ以外に用意する必要があった
- 吸い出し担当者と録画担当者は別々の方がよい
- 録画担当者は複数人でローテーションするべきだった

今回、全配信を一人で担当したので全発表型プログラムに拘束^H^H参加した。また、カメラの向きや拡大縮小などもやらないと320x240ではスクリーンの文字が見えないので中座や内職も出来ず。そして起きるトラブル。 **マジで大変** 。

あ、あとこんなことも。

- 撮影者(自分)がDVカメラ初めて操作した

そんなかんじで初日はまともな配信が出来てなかったと思う。とりあえずその日の内に対策できそうなport番号変更から着手。深夜1時頃に配信サーバー担当者(nakaj_)と連絡を取りつつ実施して分かったのは、

- `銀嶺`_ の無線APは外に出るほとんどのportが閉じている
- しょうがないのでwell known portを調べたら23番(telnet)が使えた(笑)

ということだった。そういえばGMailが使えないという声もあったな。とりあえず23番ポートを使えば何とかなるかということで、実験終了。結局1日目はTurboGears触ったのは行きの電車の中だけだった‥‥。


長くなったので、次回につづく。


.. _`銀嶺`: http://www.ginrei.co.jp/
.. _`VAIO-U3`: http://www.vaio.sony.co.jp/Products/PCG-U3/spec_master.html
.. _nakaj: http://nakaj.net/



.. :comments:
.. :comment id: 2007-03-04.7540597080
.. :title: Re:動画配信奮闘記 in Python Developers Camp 2007 冬
.. :author: Kinoshita
.. :date: 2007-03-04 21:35:54
.. :email: 
.. :url: 
.. :body:
.. こんなに大変だったとは！
.. おつかれさまでしたー。
.. 
.. 続きを楽しみにしてます。
.. 
.. ※スペック的には、
.. 　ThinkPadS30でもあまり変わらなかったのでしょうかね？
.. 
.. :comments:
.. :comment id: 2007-03-05.1784097522
.. :title: Re:動画配信奮闘記 in Python Developers Camp 2007 冬
.. :author: nakaj
.. :date: 2007-03-05 11:19:39
.. :email: 
.. :url: http://nakaj.net/Nikki
.. :body:
.. ごめんなさい、ごめんなさい、ごめんなさい。。。
.. 
.. :comments:
.. :comment id: 2007-03-05.1815786523
.. :title: Re:動画配信奮闘記 in Python Developers Camp 2007 冬
.. :author: しみずかわ
.. :date: 2007-03-05 12:30:57
.. :email: 
.. :url: 
.. :body:
.. kinoshitaさん,nakajさん、そしてjun-gさんのおかげで、まがりなりにも動画配信することが出来たと思います。誰が欠けてもうまくいかなかったのではないかと。そして念のためお願いした三脚やカメラなどご協力いただいた皆さんもありがとうございました。
.. 
.. とはいえ次回はトラックナンバーをもうちょっと下げるよう計画したいですね。今回の経験をフィードバックしていきましょう！
.. （トラックナンバーとは...ググってくださいw）
.. 
.. :comments:
.. :comment id: 2007-03-05.1705371795
.. :title: Re:動画配信奮闘記 in Python Developers Camp 2007 冬
.. :author: kuma8
.. :date: 2007-03-05 21:36:11
.. :email: 
.. :url: 
.. :body:
.. あぁ、すんませんでした。
.. 本当にいろいろありがとうございました。m(_ _)m
.. 
.. 
.. :comments:
.. :comment id: 2007-03-05.9810740868
.. :title: Re:動画配信奮闘記 in Python Developers Camp 2007 冬
.. :author: jun-g
.. :date: 2007-03-05 21:49:42
.. :email: 
.. :url: 
.. :body:
.. 本当にお疲れ様でしたー！
.. っていうか撮影まかせっぱにしてすみませんでした…。
.. 
