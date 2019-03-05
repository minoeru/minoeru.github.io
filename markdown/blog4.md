### セキュリティをツールやサービスから学ぶ【サポーターズCoLab勉強会】に参加してきた！
##### はじめに
　今回は、渋谷スクエアで2月25日(月)に行われた「セキュリティをツールやサービスから学ぶ【サポーターズCoLab勉強会】」に参加してきました。セキュリティに使われている技術などは本やWebから学ぶことはあったのですが、実際に技術者が使用しているアプリケーションについての知識は皆無でしたので参加してみました。<br>
　今回のイベントでは、(木幡周平)さんがセキュリティについて話してくれました。今まで知らなかったペネトレーション用ツールについて知れたので良い経験になりました。ありがとうございます。
##### 概要
今回の内容は以下の通りでした。
* ペネトレーションに用いるもの
* ペネトレーションに特化したOS

##### 勉強会
　勉強会では、まず、ペネトレーションに用いるものについての紹介がありました。
今回取りあげられたものは以下の4つです
###### ローカルプロキシ
 - ツールを経由するパケットの読み書きや解析を可能にし、挙動の確認を行える。
 - ex)Fiddler,BurpSuite

###### OSINT
 - 対象の情報を集め、所得した情報からさらなる情報の取得を行う。IPアドレスから空いているポートを判別することができる。
 - ex)maltego,SHODAN

###### エクセプロイトコード生成ツール
 - サーバに対し脆弱性を突いて攻撃するコードを生成する。
 - ex)BeEF,sqlmap,Metasploot Framework

###### 脆弱性スキャナ
 - 検査対象の任意のポートに対してパケットを送信し脆弱性の有無を確認、またその内容をレポートとして送信する。選択できるポートの種類は使用するものによって異なる。
 - ex)OpenVAS,OWASP ZAP,Nessus

　その後、ペネトレーションテストに特化したOSについての紹介がありました。
* Kali Linux
* BlackArch Linux

　これらのOSはそれぞれ300以上のペネトレーション用ツールや2100以上のペネトレーションツールが入っています。実際にはバージョンが対応おらず使用できないツールも多くあるので製作者の遊び気分が感じられます。

##### 懇親会
　今回は、学生が半数を占めており懇親しやすかったので個人的に楽しかったです。また、全体の人数も少なく、全体で交流する形になったりもしたのでよかったです。技術的な話もできるようになるためもう少し引き出しを増やして行けるように精進します。

##### 最後に
　今回のイベントでは今まで聞いたことのなかったツールについて知る機会となったのでとても良かったです。また、セキュリティについて発信しているニュースサイトなどの情報も教えてもらえたのでみていきたいです。話を聞いて、簡単に攻撃が行えてしまう状況であることが認識できたので、セキュリティに関する知識はある程度はつけておくのが良いなと感じました。
　