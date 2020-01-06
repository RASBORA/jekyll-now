---
layout: post
title: td-agentにプラグインがインストールできない
---

## 概要
アクセス分析にfluentd(td-agent) + elasticsearch + kibanaを使いたいと思った。
* Ubuntu 16

## エラー内容
インストールを行ったはずだが、プラグインが無いとfluentdが言ってくる。  
どうやら、fluentdで使用しているrubyとOSにインストールされているrubyは別の物らしい。
```
td-agent[32339]: Starting td-agent: 2017-04-12 17:22:16 +0900 [error]: fluent/supervisor.rb:373:rescue in main_process: config error file="/etc/td-agent/td-agent.conf" error="Unknown output plugin 'elasticsearch'. Run 'gem search -rd fluent-plugin' to find plugins"
```

## 対処方法
答えを探すのに多少手こずった。  
どうやら
```
gem install fluent-plugin-elasticsearch
```
でも  
```
fluent-gem install fluent-plugin-elasticsearch  
```
でもなく
```
/opt/td-agent/embedded/bin/fluent-gem install fluent-plugin-elasticsearch
```
が正しいようだ.

### 追記
以下でも上手く行くようだ.
```
td-agent-gem install fluent-plugin-elasticsearch
```

## 参考資料
https://github.com/fluent/fluentd/issues/369
