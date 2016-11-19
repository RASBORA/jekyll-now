---
layout: post
title: systemdでfactorioのマルチプレイサーバを管理
---

適当な記事です。
factorioをUbuntuのデーモンとして登録します。

# 環境
Ubuntu16

# 手順
以下のディレクトリにfactorio.serviceを作成  

/etc/systemd/system/  

内容は以下の通りです
```
[Unit]
Description=Factorio Server
After=network-online.target

[Service]
ExecStart=/srv/factorio/bin/x64/factorio --start-server /srv/factorio/playground01.zip
WorkingDirectory=/srv/factorio
Restart=always
User=root
Group=root

[Install]
WantedBy=multi-user.target
```

デーモン起動
```
systemctl start factorio
```

デーモン登録
```
systemctl enable factorio
```
