---
layout: post
title: BATTLEFIELD1でフレームレート（FPS）表示する方法
---

# ・概要
BATTLEFIELD3やBATTLEFIELD4でおなじみのcfgファイルを利用してフレームレート（FPS）を表示する方法です。  
  
BATTLEFIELD1ではゲーム内メニューからいじれない設定を、コンソールというものでいじることができます(半角全角キーで呼び出されるめんどいやつ)。  
コンソールでの設定内容をuser.cfgというテキストファイルに保存する事で、コンソールを呼び出す事無く特殊な設定を適応することができます。


# ・設定方法

### ゲームのインストール先を開く
ゲームのインストールフォルダを開いてuser.cfgを配置します。  
Originデフォルトでは以下のディレクトリにインストールされていると思います。

```
C:\Program Files (x86)\Origin Games\Battlefield 1\
```

### user.cfgファイルを配置
以下のファイルをダウンロードして配置するか  
[user.cfg]({{ site.baseurl }}/files/user.cfg)  

```
右クリック→新規作成→テキストファイル→ファイル名をuser.cfg
```
でuser.cfgを作成します。  
  
後者を選んだ場合は以下に進んでください。  
前者の場合は設定終了なので、Battlefield1を起動してみてください。

### user.cfgファイルの中身を編集
以下の設定内容を記述

```
PerfOverlay.DrawFps 1
```
ほかの設定を追加したい場合は以下のサイトなどを参考に  
[Here Are All Battlefield 1 Console Commands](https://diaryofdennis.com/2016/08/31/here-are-all-battlefield-1-console-commands/)  

今作は右上に小さく表示されるので注意です(他の設定足すことで表示を変更すること可能)。  
以上です。

# ・参考文献
[How to Create a Config File for Battlefield 1](https://diaryofdennis.com/2016/08/11/how-to-create-a-config-file-for-battlefield-1/)  
[Here Are All Battlefield 1 Console Commands](https://diaryofdennis.com/2016/08/31/here-are-all-battlefield-1-console-commands/)  

