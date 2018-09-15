# GitHubハンズオン(初級)
## やる事
* GitHubのアカウント作成
* Gitのインストール
* Gitの基本操作
  * リポジトリの作成
  * ブランチの作成
  * push、commitなどの基本操作
  * プルリクエストの作成(レビュー、マージ)
* GitHub Pagesを使った静的ページの作成

## 注意点
* 今回は**コマンドライン**から操作をしてもらいます
* なぜコマンドラインでやるか？
  * Gitの操作はコマンドラインが基本になっているから
  * GUIで操作できるのもあるが複雑なことができないので基本のCLIで学ぶ

## GitHubのアカウント作成
* こちらから無料でアカウント作成をします
  * https://github.com

## Gitインストール
* Windowsの人はGit for Windowsをインストール
  * https://gitforwindows.org/
  * 参考：[初心者でもWindowsやMacでできる、Gitのインストールと基本的な使い方](http://www.atmarkit.co.jp/ait/articles/1603/31/news026.html)
  * 以後Git Bashを使います
* Macの人もGitをインストールします
  * インストールの方法はサイトからインストールするかHomebrewを使うやり方があります
    * サイトからインストール
      * https://git-scm.com/
    * Homebrewでインストール
      * ターミナルを起動して以下コマンドを実行します
      * [Homebrew](https://brew.sh/index_ja)をインストール
      ```
      $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
      ```
      * gitをインストール
      ```
      $ brew install git
      ```
      * 参考：[購入直後のMacでGitコマンドを使えるようになるまで](https://qiita.com/furusin_oriver/items/974a7b7fb8c56ad88d6e)
* gitコマンドが入っているか確認します
```
$ git --version
```

## GitHub Pagesとは
* GitHubを使って静的なページを公開することができます
  * [GitHub Pages を使った静的サイトの公開方法が、とても簡単になっていた](https://www.tam-tam.co.jp/tipsnote/html_css/post11245.html)
  * [GitHub Pagesを使ってサクッとWebページを公開する](https://qiita.com/0084ken/items/4acdc7a00bf2e6f41f94)

## GitHubの基本操作
* GithHub Pagesの作成をしながら基本操作を学んで行きます。

### リポジトリの作成
* GitHubのページからリポジトリ作成を行います
  * https://github.com
* 「GitHub-Pages」という名前で作成(好きな名前で作って大丈夫です)
* 以下コマンドをターミナルで実行して作業ディレクトリを作成
```
$ mkdir Hands-on
$ cd Hands-on
```
* 先ほど作ったリポジトリをクローンする
```
$ git clone https://github.com/hikarut/GitHub-Pages.git
```
* ディレクトリに移動してリポジトリ作成のコマンドを実行
```
$ cd GitHub-Pages

echo "# GitHub-Pages" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin 先ほど作ったやつ
git push -u origin master
```

### ブランチの作成(ローカル)
* 現在のステータスを確認(現在はmasterブランチにいることを確認)
```
$ git status
```
* 現在のブランチを確認
```
$ git branch
```
* ブランチの作成(masterブランチを元にdevelopブランチを作成)
```
$ git checkout -b develop master
```
* ステータスを確認するとdevelopブランチにいることがわかる
```
$ git status
```
* ブランチがdevelopに変わったことを確認
```
$ git branch
```

### push、commitなどの基本操作
* index.htmlファイルを作成
```
$ echo "Hello world GitHub Pages" > index.html
```
* ステータスを確認(`-s`短縮した形式で表示するオプション)
```
$ git status -s
```
* 先ほど作ったindex.htmlをgitの管理下に追加
```
$ git add index.html
```
* もう一度ステータスを確認(`??`だったのが`A`になっていればOK`A`は`add`された意味)
```
$ git status -s
```
* ファイルのコミット
```
$ git commit -am "index.htmlの追加"
```
  * `-a`は既知のファイルの変更を全てコミットするオプション
  * `-m`はコミットメッセージを一緒に入力するオプション
* ステータスを確認
```
$ git status -s
```
* ローカルにコミットした内容を確認
```
$ git log
```
* ローカルにコミットしたブランチをリモートにプッシュする(developの部分は作成したブランチ名)
```
$ git push origin develop
```

### プルリクエストの作成
* 先ほどプッシュしたdevelopブランチをmasterにマージするためのプルリクエストを作成します
  * https://github.com/hikarut/GitHub-Pages

### ローカルとリモートの状況を合わせる
* リモートでプルリクエストを作成して、マージをしたのでローカルの情報と差分が出ています
* developブランチにいることを確認
```
$ git branch
```
* masterブランチに切り替え
```
$ git checkout master
```
* masterブランチに確認
```
$ git branch
```
* ローカルのmasterブランチにはREADMEファイルしかないことを確認
```
$ ls
```
* リモートの情報をプルする
```
$ git pull
```
* ローカルのmasterブランチにindex.htmlも追加されたことを確認
```
$ ls
```
* developブランチを削除(`-d`はデリートオプション)
```
$ git branch -d develop
```
* 確認
```
$ git branch
```

## GitHub Pagesの設定
* [GitHub Pagesを使ってサクッとWebページを公開する](https://qiita.com/0084ken/items/4acdc7a00bf2e6f41f94)
* ページを表示
  * https://hikarut.github.io/GitHub-Pages/


## appendix
* ターミナルからファインダー(フォルダ)を表示させる
  * Macの場合以下コマンドで今のディレクトリをファインダーで表示できる
  ```
  $ open .
  ```
  * Windowsの場合は以下コマンド
  ```
  $ explorer .
  ```
* vimを使ったファイル編集
  ```
  $ vim index.html
  ```
* git for Windowsでユーザー名とパスワードを間違えた場合
  * 一度入力したパスワードは内部に保存されるのでそちらを変更する
  * [GIT-CREDENTIAL-WINCREDのユーザー名やパスワードを変える](https://blog.hinaloe.net/2015/03/08/change-name-or-pass-of-git-credential-wincred/)
* windowsでpushしようとするとエラーになる
  * git configでメールアドレスとかを設定する
  * [Gitの設定をgit configで確認・変更](https://note.nkmk.me/git-config-setting/)
