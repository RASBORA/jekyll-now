---
layout: post
title: mdadmの警告をTwitterに通知する
---

## 概要
mdadmでRAIDアレイを構築したものの、アラートを設定していなかった。  
ただ、この２０１７年にメールクライアントの設定するのはとてもだるかったため、Twitterのアカウントに通知を行いたくなった。

## mdadmのアラート
mdadmにはprogramという引数があり、どうやら警告が発生した時にその引数で指定されたプログラムが実行されるらしい。  
下のサイトによると、programに指定されたプログラムに２，３個の引数を渡すと書いてある。  
[https://linux.die.net/man/5/mdadm.conf](https://linux.die.net/man/5/mdadm.conf)

適当に作成したプログラムを指定してみるとリビルド終了時に以下の引数が送られてきた。
```
program.py RebuildFinished /dev/md0
```

## Twitterクライアントの作成
数行でTwitterクライアントが作れるTweepyというPythonライブラリを使用して作成した。  
[https://github.com/RASBORA/mdadm-twitter-alert](https://github.com/RASBORA/mdadm-twitter-alert)
```
#!/usr/bin/env python3
# -*- coding:utf-8 -*-
import tweepy
import sys
import os.path

CONSUMER_KEY = 'bHvXbznxDz0UhaKz7q1BHetOY'
CONSUMER_SECRET = 'tC5RNt2d9lLW9PT9M2qVyi8kz28U2fRyVBI3oKfRarodUU0GuC'

app_path = os.path.dirname(os.path.abspath(__file__))

ACCESS_TOKEN = open(os.path.join(app_path,'ACCESS_TOKEN'), 'r').read()
ACCESS_SECRET = open(os.path.join(app_path,'ACCESS_SECRET'), 'r').read()

# Authorize
auth = tweepy.OAuthHandler(CONSUMER_KEY, CONSUMER_SECRET)
auth.set_access_token(ACCESS_TOKEN, ACCESS_SECRET)
api = tweepy.API(auth)

# Create tweet
TWEET_HEADER = u'' # example: u'@user'
TWEET_FOOTER = u'#Alert'

text = TWEET_HEADER + u' \n'
for arg in sys.argv[1:]:
    text += arg + u'\n'

text += TWEET_FOOTER

# Send tweet
api.update_status(status=text)
```

## テストメッセージ送信
```
mdadm --monitor --scan --oneshot --test
```

