---
layout: post
title: MacでEclipse 4.6 Neonのメモリを設定
---

従来のMac版Eclipseではメモリの設定を行う場合、以下の設定ファイルで設定できた。

```
Eclipse.app/Contents/MacOS/eclipse.ini
```

Eclipse 4.6 Neonではeclipse.iniが移動したため、以下のファイルを修正する必要がある。

```
Eclipse.app/Contents/Eclipse/eclipse.ini
```

変更する内容は以前と同じくxmx,xmsを修正すれば良い。  
今回は以下の様に修正した。

```
-xmx2048m
-xms1024m
```

Eclipseのヒープメモリを見ると設定が反映されたかわかるとと思う。  
設定していない場合以下の様に設定すると右下あたりに表示される。

```
環境設定 -> 一般 -> ヒープ ステータスを表示
```
