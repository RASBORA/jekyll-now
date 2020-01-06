---
layout: post
title: atomコマンドが見つからない問題
---

![atom command not found](http://blog.ivy-box.net/images/atom-command-not-found.png)

# 概要
MacにエディターAtomをインストールすると/usr/local/bin/atomというコマンドが追加される.

```
Usage: atom [options] [path ...]
```
このコマンドはコマンドラインからAtomを呼び出す事ができて非常に便利だった（ディレクトリごと開く事もできる）.  
ただ以下の様なエラーが出て使えなくなってしまった。

```
$ atom
zsh: command not found: atom
```

# エラー対処
端的に言うとatomが勝手にバージョンアップしたためこのような状態に陥った。  
atomとターミナルを再起動すればatomコマンドが使えるようになる。

# エラー原因
atomのバージョンアップでコマンドが格納されているディレクトリが変わったため、シェルでatomと打ち込んでも存在しないファイルを参照する。  
atomコマンドの実体↓
```
% ll /usr/local/bin/atom
total 8
lrwxr-xr-x 1 user admin 53 22  2    20:02   atom -> /Applications/Atom.app/Contents/Resources/app/atom.sh
```
エラー時は```/Applications/Atom.app/Contents/Resources/app1.12.6/atom.sh```観たいなバージョンアップに伴い削除されたと思わしきディレクトリを参照していた気がする。
