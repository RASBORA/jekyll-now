---
layout: post
title: systemdでfactorioのマルチプレイサーバを管理
---

適当な記事です。
factorioをUbuntuのデーモンとして登録します。

# 環境
Ubuntu16

# 手順

# factorioサーバーファイルを配置
/srv/の中に作成しました。
セーブデータ名はplaygound01.zipで作りました

# factorio.serviceを作成  
以下のディレクトリに作ります
```
/etc/systemd/system/
``` 

内容は以下の通りです  
```
[Unit]
Description=Factorio Server
After=network-online.target

[Service]
ExecStart=/srv/factorio/bin/x64/factorio --start-server /srv/factorio/playground01.zip
WorkingDirectory=/srv/factorio
Restart=always
User=factorio
Group=factorio

[Install]
WantedBy=multi-user.target
```

## デーモン起動
```
systemctl start factorio
```

## デーモン登録
```
systemctl enable factorio
```

# 参考資料
[http://wikiwiki.jp/factorio/?%A5%DE%A5%EB%A5%C1%A5%D7%A5%EC%A5%A4](http://wikiwiki.jp/factorio/?%A5%DE%A5%EB%A5%C1%A5%D7%A5%EC%A5%A4)
