---
layout: post
title: \OC\Memcache\Redisエラーの対処方法
---

redisをインストールして、ownCloudのconfig.phpにredisの設定を追加してページにアクセスした所。

```
\OC\Memcache\Redis
```

がどうたらというエラーメッセージが表示された。
  
原因はphp-redisのインストールを忘れていた事だった。   
Ubuntuの場合以下の様にしたら解決。

```
apt-get install php-redis
```
