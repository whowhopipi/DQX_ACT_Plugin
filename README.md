# DQX_ACT_Plugin
Advanced Combat Tracker Plugin for DQX  
DQX の戦闘ログを ACT で解析するためのプラグインです。


## 注意

このプラグインは、「DQX の」とはいうものの、
直接的に DQX と関係するものではなく、
一定のフォーマット(このプラグインのために定義された独自のもの)で
記述された戦闘ログを解析する汎用のプラグインであり、
*特定のゲームの規約に抵触するような機能は持ちません*。


## ログについて

このプラグインには、
*DQX のゲームからログファイルを生成する機能はありません*。
利用者は別の手段でログファイルを作成してください。
例えば、以下のような方法があります。

* ゲームの戦闘ログ画面を見ながら、手で入力する
* ゲームの戦闘ログ画面をスクリーンキャプチャして、OCR でテキスト化する

ゲームのネットワーク入出力やメモリを参照してログファイルを生成する方法は、
規約違反の可能性があることにご注意ください。


## インストール

DQX_ACT_Plugin.cs を適当なフォルダーに置いて ACT で plugin 登録してください。


## 設定

Options -> Main Table/Encounters -> General -> Number of seconds... は
オフにしたほうが良いでしょう。


## 実行

ログファイルを Import/Export -> Select File から読み込ませてください。


## ログファイルのフォーマット

UTF-8 文字コードの TSV (タブ区切り) としてください。
一行は以下のフォーマットで構成されます。\<t\> はタブ文字です。

yyyy/mm/dd hh:mm:ss\<t\>行番号(10進数可変桁)\<t\>フラグ(16進数8桁、先頭は0x)\<t\>キャラID1\<t\>キャラID2\<t\>キャラ名1\<t\>キャラ名2\<t\>ログ文字列

例えば、以下のようになります。

2016/01/51 11:32:23\<t\>2280\<t\>0x60001215\<t\>AA000-016\<t\>AA000-030\<t\>エックス\<t\>アンルシア\<t\>こんにちわ！

このうち、行番号・キャラID1・キャラID2 は、
このプラグインでは使用しませんので、適当な文字列でも構いません。
フラグは、0x00000008 以下の場合にのみ戦闘ログとして扱います。

より具体的な詳細は、sample.log をご覧ください。
