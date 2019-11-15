# Macシステム関係の設定に関するあれこれ

## 外部ディスプレイ

Dell U3014の外部ディスプレイをmacosに接続するとうまく表示されない。
これは複数の問題により生じている模様。

1. U3014をテレビだと認識して、カラーモードをテレビ用にしてしまう。
2. リフレッシュレートをNTSC(これもテレビ用？)に強制される。

そんなわけで、この2つを修正する必要がある。

### 1. U3014用のカラーモードの生成

適当にググれば出てくるが、U3014用のカラーモード生成のためのスクリプトが落ちているので、
それを実行して、生成されたディレクトリを以下の場所に保存する。(スクリプトはpatch-edid.rb)

> cp -r DisplayVendorID-10ac /System/Library/Displays/Overrides/

ただし、コピー先はrootでも書き込み不可とされている領域なので、csrutilコマンドで
disableしておく必要がある。

参考:

1. [スクリプトとその手順(http://www.ispcolohost.com/2013/07/11/connecting-a-dell-ultrasharp-u3014-to-a-mac-ugh/)](http://www.ispcolohost.com/2013/07/11/connecting-a-dell-ultrasharp-u3014-to-a-mac-ugh/)
2. [csrutilの使い方](https://applech2.com/archives/46435268.html)

### 2. 文字をキレイに表示

上記の設定を行っても、文字がキレイに出力されない場合がある。これはリフレッシュレートがNTSCになっているためである。これはディスプレイ側の設定を変更することで回避が可能。

ディスプレイのシャープネスを0にしてしまえばよい。

参考:

1. [Blurry Text On Dell UltraSharp U3014](https://discussions.apple.com/thread/5049049)

# 開発環境に関するあれこれ

-> DEV.mdへ

## python

デフォルトでインストールされているバージョン以外にもいろいろ使いたい。
仕事毎にpythonのライブラリの環境も分けたい。
という要望があったので、pyenv + virtualenvで環境構築

### pyenvのインストール

### virtualenvのインストール

### pyenv + virtualenvによるディレクトリ毎の環境構築

virtualenvにより既存環境をコピーして新規環境を作成して、カレントディレクトリでその環境を有効にする。

```
$ pyenv virtualenv 3.6.3 XXXX
$ pyenv local XXXX
```

#### mojaveのときに躓いた点

mojaveにアップデートしたらpyenv経由でpythonをインストールできなくなった。xcodeやxcodeのコマンドラインツールを再インストールしてもだめだった。
結局、xcodeのコマンドラインツールのヘッダファイルにパスが通っていないのが原因だったので以下のようにしてあげればOK.

```
$ CFLAGS="-I$(xcrun --show-sdk-path)/usr/include" pyenv  install 3.5.2
```

これでzlibがないとかのエラーはなくなる。

### python + tcltk

pythonでtcltkを用いてUIを作成するには事前にtcltkのライブラリをインストールしてから、pythonをコンパイルする必要がある。
事前にtcltkのライブラリをインストールしないとtcltkのpythonラッパー？であるtkinterがインストールされない。
tcltkに関しては本家サイトからMacOSX用のパッケージをダウンロードしてインストールすればOK。


## node.js

node.jsでもpyenv + virtualenvのようなことをやりたいのでいろいろ調べてセットアップ。

# Windows10システム設定あれこれ

## 外付けキーボードだけUS配列に変更

できない…ノートPC付属の

## 外付けキーボードだけctrl<->capsを交換

同様に無理

## キーボードを英語に
設定からハードウェアキーボードを英語に変更すればOK
## キーボードのctrl<->capsを入れ替え
レジストリを書き換えればOK