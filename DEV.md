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

## npm

### nodebrew