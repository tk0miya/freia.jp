:date: 2006-05-14 17:55:00
:categories: ['Zope', 'Plone']
:body type: text/x-rst

==============================================
2006/05/14 Zopeを2.9.3にアップグレードしてみる
==============================================

*Category: 'Zope', 'Plone'*

前から検討していたのですが、やっとZope2.9にアップグレードすることが出来ました。

- 旧構成

  - Python-2.4.2
  - Zope-2.8.5
  - Plone-2.1.2
  - COREBlog2-0.82?

- 新構成

  - Python-2.4.3
  - Zope-2.9.3
  - Plone-2.1.2
  - COREBlog2-0.9b

Plone-2.1.2はZope-2.9系列でテストされていません。危ないですねー。まあ実験環境だしいいか。あとついでにCMFContentsPanelsを使ってトップページを変えてみました。Plone標準の「最近の更新」portletをanonymousに見せるのはあまり意味がないので止めたかった、というのが理由ですが、今までportletはそれしか表示してなかったので今はportletがありません。なんか寂しくなった気がします。

CMFContentsPanels-2.1はPlone2.1.2に最適化されていないので、これからいろいろとカスタマイズしていこうと思います。ということでまずはCOREBlog2エントリを表示するviewletを作ってみました。（つづく）


.. :extend type: text/html
.. :extend:

