# Sourcetree使い方、Git関連

[Sourcetreeインストールガイド(Mac版)](https://minoeru.github.io/markdown/mis_sourcetree.html)でSourcetreeのインストール方法はわかったでしょうか？
今回はSourcetreeの使い方を見ていきます。


- 目次
 - 個人での開発
 - 複数人での開発
 - オススメサイト

### 個人での開発

まず、Githubでリポジトリを作成していきましょう
(GitHubの使い方がわからない方は[GitHubアカウント作成](https://minoeru.github.io/markdown/mis_github.html)を参考にしてください)

![](https://minoeru.github.io/markdown/images/sourcetree/s2_1.png)

リポジトリの作成が終了すると、以下のような画面になるので、画面に表示されているURLをコピーして下さい。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_2.png)

Sourcetreeに戻ったら、新規ボタンから「URLから　クローン」を選択してください。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_3.png)

「リポジトリをクローン」の画面が出てくるので、必要事項を入力してください。
 - ソースURL:先ほどコピーしたリポジトリのURLです
 - 保存先のパス:ローカル環境(自分のパソコンのなか)のどこに保存するかです
 - 名前:保存したファイルの名前になります

![](https://minoeru.github.io/markdown/images/sourcetree/s2_4.png)

このように、保存先のパスで指定した場所を確認すると、しっかりとクローンができていることが確認できます。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_5.png)

次に、Sourcetreeに戻って操作方法を学びましょう。
クローン直後なので今は何も操作できません。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_6.png)

先ほどコピーしたローカルのファイルにファイルを追加しましょう。
適当なテキストファイルを追加しました。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_7.png)

Sourcetreeを確認してみると、ファイルに変更があったことが確認できます。(右の❶)

![](https://minoeru.github.io/markdown/images/sourcetree/s2_8.png)

クリックして開くと、大画面左に変更したファイル一覧、大画面右にその変更内容が確認できます。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_9.png)

左上の「コミット」ボタンを押すことで、コミットメッセージの記入とコミットを行うことができます。
(コミットとは、前回の変更から今回の変更までのひとかたまりの処理の結果を確定することです。
  今回の例を用いると、hoge.txtの追加を確定する。ということになります)
※コミットメッセージはできるだけ内容がわかるようにしましょう

![](https://minoeru.github.io/markdown/images/sourcetree/s2_10.png)

コミットボタンを押すことで、コミットが終了します。ブランチ(今までのgitの履歴を表すもの)を確認すると、コミットがうまく行ったことが確認できます。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_11.png)

コミット終わったら、次はローカルの変更履歴をリモートと共有しましょう。
プッシュボタンを押すことで今回の変更をアップロードすることができます。
こうすることで、リモートの状態をローカルの状態と同期させることができます。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_12.png)

![](https://minoeru.github.io/markdown/images/sourcetree/s2_13.png)

これでプッシュは完了です。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_14.png)

GitHubに行って結果を確認してみましょう。
このように、リモートのリポジトリにも変更が適用され、ローカルと同じ状態になったことが確認できました。
これでSourcetreeでGitを使用する基礎はできるようになったと思います。

![](s2_15.png)

### 複数人での開発

一人で開発を行う際は上に書いた通りにやっていけば良いのですが、複数人で集団開発を行う場合では少し足りないことがあります。
全ては書ききれないので、簡単なもの二つに絞り書いていきます。
- プル
プルとは、リモートリポジトリの内容をローカルに書き加えることです。プルを行うことで、他の人が変更した場所を共有することができます。

- プルリクエスト
プルリクエストとは、変更を他の人に伝えるものです。~~~の変更を行ったのでこの変更を受け入れて下さい。といった感じで使います。

これらの動作は実際に集団開発を行う際に経験するのが良いと思うので、ここではプルリクエストのやり方の紹介に留めておきます

まずはhoge.txtを若干編集しました

![](https://minoeru.github.io/markdown/images/sourcetree/s2_16.png)

ブランチタブから、プルリクエストを作成をクリックしましょう。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_17.png)

以下のような画面が出てくるので、Web上でプルリクエストを作成をクリックしましょう

![](https://minoeru.github.io/markdown/images/sourcetree/s2_18.png)

今回は個人開発状態なので何も出てきませんが、本来はここでプルリクエスト用のコメントを書く欄が出てくるので、そこで記入、送信をします。

![](https://minoeru.github.io/markdown/images/sourcetree/s2_19.png)

### オススメサイト

以下にgitの勉強ができるオススメサイトを載せていきます。

[hegehege](#)
[hegehege](#)
[hegehege](#)
[hegehege](#)
[hegehege](#)
