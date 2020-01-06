---
layout: post
title: MacでEclipse 4.6 Neonのメモリを設定
---

従来のMac版Eclipseではメモリ設定を以下のファイルで行う事ができた。

```
Eclipse.app/Contents/MacOS/eclipse.ini
```

Eclipse 4.6 Neonではeclipse.iniが移動したため、以下のファイルを修正する必要がある。

```
Eclipse.app/Contents/Eclipse/eclipse.ini
```

従来通りxmx,xmsを修正すればメモリを調整できる。  
今回は以下の様に修正した。

```
-xmx2048m
-xms1024m
```

Eclipseのヒープメモリステータスを見ると設定が反映された事わかると思う。  
ヒープメモリステータスを表示していない場合以下の様にすると右下あたりに表示される。

```
環境設定 -> 一般 -> ヒープ ステータスを表示
```
