# 開発環境構築に関するあれこれ
## python

### pyenv インストール

### pyenv virtualenv インストール

### pyenv virtualenv による個別環境構築

```
$ pyenv versions
* system (set by /pathto/.pyenv/version)
  3.5.4
  3.6.3
$ pyenv virtualenv 3.6.3 foo
$ pyenv versions
* system (set by /pathto/.pyenv/version)
  3.5.4
  3.6.3
  foo
$ pyenv local foo
$ pyenv uninstall foo
```

## typescript

### nodebrew インストール(nodejs)

### typescriptのインストール

```
 $ npm install -g typescript
```

### 開発環境構築

まずはプロジェクト用ディレクトリの作成．

```
 $ mkdir <Project Name>
 $ cd <Project Name>
```

#### package.jsonの作成

まずはnpmの設定を行う？

```
 $ npm init
```

#### tsconfig.jsonの作成

Makefileのようなものらしい．

```
 $ tsc --init
```

tsconfigの詳細な説明については以下を参照すること．

tsconfig - https://www.typescriptlang.org/docs/handbook/tsconfig-json.html

#### 型定義ファイル管理

型定義ファイルの導入は以下の通り．
自分で作成して管理するにはtypingsというツールを使うのが一般的なの？

```
 $ npm install --save-dev @types/<モジュール名>
```

typingsについては後で．

#### トランスパイル

-> コンパイルのこと．

vscodeでは"Command + Shift + p"でコマンドパレットから"Configure Task Runner"で
TypeScriptプロジェクトをビルドでやる模様．

ただし，webpackを使うのでこれは使わない？

#### webpack