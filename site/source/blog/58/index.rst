:date: 2004-08-12 23:11:13
:categories: ['Programming', 'python']
:body type: text/x-rst

=========================
2004/08/12 アクセス数計測
=========================

*Category: 'Programming', 'python'*

先週辺りから、Worldから自宅サーバーへのアクセスが出来ない現象が多発しています。サーバーのOSを入れ替えてからOSそのものは落ちていないようなのですが、ナゼか外部からアクセスできなくなるようです。試しに定期的に外部にメールを発信するようにしたところ、そのタイミング毎にアクセスが可能になるようで、OSというよりはルータとかを疑った方が良いような気がしてきました。

ところで、今日は何時頃にアクセスできなくなっていたのか、というのを知りたくなったので、apacheのアクセスログを集計してみることにしました。最近pythonで簡単なプログラムを書くのが趣味になりつつあるので、今日もまたpythonで書いてみます。


.. :extend type: text/x-rst
.. :extend:

apacheのログから時間単位のアクセス数を計算::

  #!/usr/local/bin/python
  
  import fileinput
  import re
  
  date = re.compile("(\d+)/\w+/\d+:(\d+):(\d+):(\d+)")
  hour = ""
  times = 0
  
  for line in fileinput.input("/var/log/httpd/freia-access.log"):
    time = date.search(line)
    if time:
      groups = time.groups()
      group = groups[0]+" "+groups[1]
      if hour != group:
        print "%s: %s" % (hour, "*"*(times/10))
        hour = group
        times = 0
      times += 1
  
  print "%s: %s" % (hour, "*" *(times / 10))

結果はこんな感じです::

  12 00: ************
  12 01: *******************************
  12 02: *********
  12 03: *
  12 04: *****
  12 05: ***********
  12 06: *********
  12 07: ******
  12 08: ***************
  12 10: ********
  12 11: ***************
  12 12:
  12 13: *************
  12 14: ************************************************
  12 15: *****************************************
  12 16: ****************************
  12 17: ******************************
  12 18: ********************
  12 19: **********************
  12 20: ***********************
  12 21: **************************
  12 22: ****************************
  12 23: ******

‥‥ここまでやってから気づいたのですが、これでは単なるアクセス数集計で、どの辺りでアクセスが途切れているかを知ることは出来ません。だめじゃん。

とりあえず１分単位で集計して途切れタイミングを知ることだけは出来そうですが、会社のサーバーあたりにcron仕掛けて調べる方が現実的ですね。

