---
layout: post
title: Python subprocess.check_outputで使用できる最大文字数
---

Pythonのsubprocess.check_outputで使用できる文字数を調査した。  
Bashの環境変数'ARG_MAX'の数値とは関連がないようです。  

```
import subprocess

i = int(100000000)
n = 0
while True:
    try:
        n += i
        text = 'b' * n
        command = 'echo "{text}"'.format(text=text)
        subprocess.check_output(command,shell=True)
    except OSError:
        print("Fail: ",n)
        if i == 1:
            print("LENGTH: ", n -1 + 7)
            break
        n -= i
        i //= 10
```

## Ubuntu 16 (Python 3.5.2)
131071文字

## CentOS6 (IUS Python 3.6.1)
131071文字

## OSX (Python 3.6.0)
260624文字
