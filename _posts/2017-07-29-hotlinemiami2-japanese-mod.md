---
layout: post
title: HotlineMiami2日本語化MOD
---

HotlineMiami2のセリフのみ日本語化MODを作成しました。

<a href="https://blog.ivy-box.net/files/japanmod.zip">ダウンロード</a>  
* 上記をダウンロード＆解凍
* `japanmod.patchwad`を`"ドキュメント/My Games/HotlineMiami2/mods"`配下に配置
* ゲームタイトル→Options→LanguageでJapanmodを選択

## MOD概要
HotlineMiami2 PC版は日本語を選択できませんが、データ内には日本語が存在します。  
ただ、強制的に選択しても日本語に対応したフォントが存在しません。

このMODでは
* 日本語を選択可能に
* 日本語フォント画像の埋め込み
* 雰囲気を重視してセリフ以外は英語  

という対応をしています。

## 日本語化MODの作成手順
もしも、日本語化modを作成する場合以下の手順を参考にしてください。  
※ binファイルは32bit(4Byte)のリトルエンディアンで数値が記録してある点に注意

### 必要なツール
* <a href="https://github.com/TcT2k/HLMWadExplorer/releases" target="_blank">HLM WAD Exploler</a>
* <a href="http://www.angelcode.com/products/bmfont/" target="_blank">bmfont</a>

### 日本語を選択可能にする

1. HLM WAD Explolerで`hlm2_localization.bin`を取り出します。  
2. バイナリエディタで`Japanese`文字列後ろの`0C`を`02`などに書き換える。
3. 書き換えた `hlm2_localization.bin`をHLM wad explolerでReplaceする。

### 日本語フォントの埋め込み
HLM wad explolerで日本語化したいフォントを確認をします。

次に、bmfontで使用するフォントを画像化します。  
1. `Font Options`で種類とサイズの決定
2. hlm2_localizationで使用する文字を列挙したUTF-16のテキストを作成  
3. 上記ファイルを`Select chars from file`で開く
4. `00000 Latin + Lation Supplement`も一応選択  
5. `ExportOptions`フォント画像がpng形式で1ファイルになるように調整
6. 出力

最後にHLM wad explolerで該当のフォントをReplaceします。  
※ XML内のファイル指定は機能していないので同名のファイルにする

### セリフの書き換え
C言語風で書くと以下のような構造になっています（文法的に正しくないです）。
```
struct hlm2_localization{
  int32_t language_length;
  int32_t unknown1;
  struct language_data language_section[language_length];
};
struct language_data{
  int32_t lang_name_length;
  char lang_name[lang_name_length];
  int32_t control_number;//選択の可否とか設定している
  int32_t text_length;
  struct position head_section[text_length];
  struct text body_section{text_length];
};
struct position{
  int32_t text_position;
};
struct text{
  char text[];//head_sectionのtext_positionから次のtext_positionまでの文字列
};
```
上記を考慮して以下のようなスクリプトを作るか  
<a href="https://gist.github.com/RASBORA/6e72d15b9ac841f18e071b1b83b1a0bc" target="_blank">gist</a>  
海外の人が作っているエディタを使えば編集できます。

何か合ったらメールかtwitterまでお願いします。
