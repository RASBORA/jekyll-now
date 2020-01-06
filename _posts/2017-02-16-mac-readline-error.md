---
layout: post
title: Mac版Pythonで矢印キーが使えない
---

# 概要
Mac版PythonのREPLで矢印キーが使えなくてすごく不便.  
ネットで調べるとreadlineと言うライブラリが関係ある事は確定だが、対処方法や状況は人によってまちまちのようだったので、自分の対処方法も一応記事にしておく。

# 対処方法
ネットでPythonのdmgをダウンロードしてインストール  
[https://www.python.org/downloads/](https://www.python.org/downloads/)  
これで解決

# エラー詳細
import readlineを実行してみたら以下の様なエラーメッセージが出てきた。

```
>>> import readline
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: dlopen(/usr/local/Cellar/python/2.7.11/Frameworks/Python.framework/Versions/2.7/lib/python2.7/lib-dynload/readline.so, 2): Library not loaded: /usr/local/opt/readline/lib/libreadline.6.dylib
  Referenced from: /usr/local/Cellar/python/2.7.11/Frameworks/Python.framework/Versions/2.7/lib/python2.7/lib-dynload/readline.so
  Reason: image not found
```

```
>>> import readline
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: dlopen(/usr/local/Cellar/python3/3.5.1/Frameworks/Python.framework/Versions/3.5/lib/python3.5/lib-dynload/readline.cpython-35m-darwin.so, 2): Library not loaded: /usr/local/opt/readline/lib/libreadline.6.dylib
  Referenced from: /usr/local/Cellar/python3/3.5.1/Frameworks/Python.framework/Versions/3.5/lib/python3.5/lib-dynload/readline.cpython-35m-darwin.so
  Reason: image not found
```

該当のフォルダの中身

```
[/usr/local/opt/readline/lib]
% ls
libhistory.7.0.dylib   libhistory.dylib@      libreadline.a
libhistory.7.dylib@    libreadline.7.0.dylib  libreadline.dylib@
libhistory.a           libreadline.7.dylib@
```

どうやらMacに標準で入っているpython(2.7.11)が読み込むreadlineのバージョンが違ったようだ(readline6系)。  
ダウンロードしたPython(2.7.13)ではlibreadline.7.dylibを読みむようで矢印キーとimport readlineを行うことができた。
