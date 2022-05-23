---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "本当に最低限のvimrc入門 #vim"
subtitle: ""
summary: ""
authors: []
tags: 
  - 'Vim'
  - 'vimrc'
  - '新人vimmer応援'
categories: []
date: 2016-12-17T18:24:53+09:00
lastmod: 2022-05-23T18:24:53+09:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
# 本当に最低限のVim入門

この記事は[Vim Advent Calendar 2016](http://qiita.com/advent-calendar/2016/vim)の17日目の記事です. 

先日は[todashuta](http://qiita.com/todashuta)さんで, [Vim 8で便利になった組み込みMRU](http://qiita.com/todashuta/items/1362654c6276e5b69abc)でした. こんな便利な機能があったんですね(無知ですみません...).

## 対象読者

以下のような読者を想定しています.

- Vimを使ってみたいけど何から始めればいいか分からない人
- Vimをそっ閉じした経験がある人(そっ閉じすら出来なかった人も含む)
- サーバーを触っていてVimを触らざるを得なくなった人
- 友人にキチガイじみたVimmerがいる人(←new)

## はじめに

Unix系OSやLinuxの場合は標準でインストールされている事がほとんどですが, もし入っていなかった場合はパッケージマネージャーからインストールして下さい.  

### Debian系Linuxの場合

```bash 
$ sudo apt-get install vim
```

### RedHat系Linuxの場合

```bash 
$ sudo yum install vim
```

### Fedora22以降の場合

```bash 
$ sudo dnf install vim
```

### ソースからコンパイルする場合

```bash 
$ git clone https://github.com/vim/vim.git
$ cd vim/src
$ make
```

Windows10の場合は, Bash on Windowsを使えば上記Ubuntuと同じようにインストールできます. それ以外のバージョンのWindowsの場合は, [KaoriYaさんのホームページ](https://www.kaoriya.net/software/vim/)からダウンロードできるので, それを使えばいいかと思います.  

## 起動と終了

Terminalでvimコマンドを実行して下さい.  

```bash 
$ vim
```

Vimが起動しましたね.  
では次に終了の仕方です. 以下のように打ち込んでEnterを押して下さい.

```vim 
:q
```

終了しましたか？  
もし終了しなかった場合は, `Esc`を連打してからもう1度試してみて下さい.  

## 設定ファイルの作成
Terminalでvimコマンドを実行する際に引数にファイル名を与える事で, そのファイルをVimで開く事ができます. また, まだ存在しないファイル名を指定すると新規ファイルを作成する事ができます.  
今回は, 皆さんが今後1番Vimで編集する事になるであろう, Vimの設定ファイルを作成しましょう. Vimの設定ファイルの名前は**.vimrc**です. ホームディレクトリに保存します.  
以下のように設定ファイルを新規作成しましょう.  

```bash 
$ vim ~/.vimrc
```

何も書かれていないファイルが開いたと思います(環境によっては初めから何か書かれている可能性があります).  
では最初の設定を書き込みましょう.  
今の状態では文字を入力することはできません. Vimを文字入力入力できる状態にするには, 挿入モードに切り替える必要があります.  
Vimはデフォルトではノーマルモードになっています. ノーマルモードから挿入モードに切り替えるには, `i`と入力して下さい. すると文字が入力できるようになります.  
以下のように入力してみて下さい. 

```vim 
syntax on
```

次に, 保存の方法です. 保存を行うにはノーマルモードに戻す必要があります.  
ノーマルモードに戻るには`ESC`か`Ctrl+[`を押します. US配列のキーボードを使っている人は後者の方が楽かと思います. 今後よく分からない状態になってしまった場合は, とりあえず`ESC`を連打してみましょう. 大体なんとかなります.  
保存は以下のように入力することで行います.  

```vim 
:w 
```

## 設定の反映

では次に設定を反映してみましょう. Vimを再起動することによっても反映することができますが, 以下のコマンドを入力すると再起動なしに設定の反映が行なえます. 

```vim 
:source ~/.vimrc
```

色が付いたら成功です.

## 設定の追加

更に設定を追記します.
`o`を入力して下さい. すると改行して挿入モードに切り替わります.
以下を入力してみて下さい. 

```vim 
set number
```

`ESC`でノーマルモードに戻って下さい.
次に, この行を複製します. まず`yy`を入力して下さい.
そのまま`p`を入力して下さい. すると先程の行がペーストされます. 
次にVimのカーソル操作です. Vimでは`h`で左, `j`で下, `k`で上, `l`で右に移動できます.
`set number`のnの上までカーソルを移動させます. 
次に連続置換です. そこで`R`を押して下さい. カーソル位置から連続で置換をすることができます.
`cursorline`と入力して`ESC`でノーマルモードに戻って下さい.
以下のようになると成功です.

```vim 
set cursorline
```

## 保存して終了
最後に保存して終了です. `:wq`を入力してエンターを押して下さい.

## 終わりに
以上で本当に最低限のVim入門を終わります. 
これ本当に最低限か？全然足りねえよ, むしろ最低限ならそれ要らないだろ, 偏りすぎだ, 等の意見が多方面から聞こえて来そうですが...
(こんな記事を書いてから言うのも何ですが, シェル上でvimtutorコマンドを叩いてみると主要な機能を網羅した素晴らしいチュートリアルが始まります. 30分ぐらいの時間の余裕があるならそっちをやる事をおすすめします)

Vimのコミュニティでは, 毎週土曜日23時から[vimrc読書会](http://vim-jp.org/reading-vimrc/)というものを行っています. ここでは毎週強いVimmerの方々が色んな人の設定ファイルを読んで意見交換をしています. もっとVimの設定に関して知りたい方は, これに参加すると良いかと思います. 
vimrc読書会のロゴを作らせて頂きました. こういう形でしか力になれなくて申し訳ないですが...

<blockquote class="twitter-tweet" data-lang="ja"><p lang="ja" dir="ltr">ロゴ作ってみました<a href="https://twitter.com/hashtag/vimrc%E8%AA%AD%E6%9B%B8%E4%BC%9A?src=hash">#vimrc読書会</a> <a href="https://t.co/o0QGcGDkzD">pic.twitter.com/o0QGcGDkzD</a></p>&mdash; Tatsuki@Vim (@ttk_vim) <a href="https://twitter.com/ttk_vim/status/792409759311798272">2016年10月29日</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

明日は[mattn](http://qiita.com/mattn)さんの記事です. どんな記事なのか楽しみですね.

