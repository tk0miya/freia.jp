:date: 2005-10-12 00:09:04
:categories: ['Zope']
:body type: text/x-rst

=============================================
2005/10/12 コメントスパム削除対策（後ろ向き）
=============================================

*Category: 'Zope'*

あまりにもコメントスパムが多いので、手動で削除するのは馬鹿らしくなってきました。
多いときは10分で20投稿くらいされてしまったりします。今日は3時間で100件きました。
しかもアクセス元IPが毎回変わっているのがタチが悪い。

対策としては、setomitsさんが `コメントスパム弾き実験 3`_ で書かれているような、 **投稿させない** 対策と、 `一つ前の記事`_ で書いたような、 **疑わしい投稿をチェックする** 対策が考えられます。

`COREBlog1.2.1`_ の機能でフィルタリングは出来たので、フィルタされた投稿を元に、投稿させない方法を考えてみたいと思います。


.. _`コメントスパム弾き実験 3`: http://matatabi.homeip.net/blog/setomits/473
.. _`一つ前の記事`: http://www.freia.jp/taka/blog/256
.. _`COREBlog1.2.1`: http://www.zope.org/Members/ats/COREBlog



.. :extend type: text/x-rst
.. :extend:

とりあえずは投稿されてしまったスパムを一覧化して、傾向を調べたり、削除したり、誤って非表示になってしまったものを表示しにたりするツールを作ってみました。最終的に全部削除するにしても、ZMIでエントリを一つ一つ回って歩きたくないし。

download: `COREBlogModerates-0.1`_ (for COREBlog1.2.1)

作ったと言っても、とりあえず自分が必要そうな機能だけなので、COREBlogにパッチが必要だったり、インストールが面倒だったりします。あとかじりかけのJavaScriptなんかも使って遊んでます。

.. figure:: coreblog_moderates01
  :target: images/coreblog_moderates01

  画面はこんな感じ。これだとスパムの傾向を分析しにくい、というか出来ないですが、
  とりあえず一括削除くらいは出来ます。


.. _`COREBlogModerates-0.1`: http://www.freia.jp/taka/file/Zope/COREBlogModerates-0.1.tgz/file_view




