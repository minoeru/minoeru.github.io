# ICTSC2021冬の陣

2/26-27に開催された[ICTSC2021冬の陣](https://icttoracon.net/archives/8892)にチーム:mis1yakudoとして参加してきました！

ICTSC2019、ICTSC2020、ICTSC2021夏の陣に続く4度目の出場で、夏の陣に引き続き見事優勝することができました!

<img src="https://minoeru.github.io/markdown/images/ICTSC2021/img.png" width="320">

私は~~CISCO~~ネットワーク問題担当であったため、
- 07 なんでつながらない！？
- 09 pingが通らない
- 13 え、何のネイバー...?

を解き
- 10 インターネットにつながらない！

に協力しました。

この中でも特に印象に残っているのは
**10 インターネットにつながらない！**
です。

この問題はiBGPにBGP unnumberedを使用してネットワークの構築を行なっている問題でしたが、チームメンバにこの技術を触ったことがある人がおらず、FRRにも不慣れであったため最も時間がかかってしまいました。

[BGP in the Data Center](https://resource.nvidia.com/en-us-bgp-datacenter/bgp-datacenter-ebook)を早く読まねば...という気持ちが高まります。

後から思い返すと、最後まで残った問題であったので、チームメンバ全員で問題解決のため意見を出し合い取り組めたのが楽しかったです。


## Write Up(インターネットにつながらない！)
- まずFRRに入ります。
```
user@rt02:~$ sudo vtysh
```
- **rt02# show ip bgp neighbors**でネイバー関係を確認するとiBGPとeBGPどちらもネイバー関係が築けていることがわかります。
- しかし、**rt02# show ip route**で経路を確認すると、経路が広告されていませんでした。
- そこでまず、ルーティングを有効化します。
```
rt02# conf t
rt02(config)# ip forwarding
rt02(config)# ipv6 forwarding
```
- 次に、unmumberedを有効化します。
```
rt02(config)# router bgp 65182
rt02(config-router)# neighbor fc00:1:: capability extended-nexthop
```
- これにより、Router1と経路交換が可能となります。
- この状態で**rt02# show bgp ipv4 summary**で確認を行うと、
```
Neighbor    V     AS  MsgRcvd  MsgSent  TblVer InQ OutQ Up/Down State/PfxRcd  PfxSnt Desc
10.0.0.2    4   65971   1128   1134    0  0  0 00:21:00   (Policy) (Policy) N/A
fc00:1::    4   65182   4684   7411    0  0  0 00:18:30      1    1 N/A
```
- という結果になり、Policyがきな臭い感じがしました。
- そこでチームメンバーにPolicyが怪しい話を投げかけると、以下のコマンドで、eBGPの経路を受信する際に必要なポリシー設定の制約をなくすことと、受け取っていた古い情報を削除できることを見つけてもらえました。
```
rt02(config-router)# no bgp ebgp-requires-policy
rt02(config-router)# do clear bgp 10.0.0.2 soft in
```
- その結果、Router2は必要な経路情報を全て受け取ることができました。
- しかし、Serverからpingを送ってみるとうまくいきませんでした。
- 問題文を読み返していると、Router2が172.16.0.0/24の経路を広告しておらず、帰りの経路情報を渡していないミスをチームメンバに指摘されました。
- そこで、networkコマンドで広告を行うと、無事serverからpingが通るようになりました。
```
rt02(config-router)# network 172.16.0.0/24
```
- 最後に、設定の永続化、forwardingの永続化をやってもらい、終了です。
```
rt02# write memory
/etc/sysctl.confを以下のように書き換える
\- #net.ipv4.ip_forward=1
\+ net.ipv4.ip_forward=1
```


## 感想
弊チームは自分以外のメンバが皆今年度で卒業してしまうため、最後に優勝で終われたのは非常に良かったです。


ICTSCのおかげで初めは何もわからなかったVyOSやFRRに親しみを覚えることができました。普段聞き慣れない技術に触れる機会が何度もあり、楽しかったです。

でもやっぱり参考サイトや知見が少なくて辛い....

夏の陣、冬の陣とairbnbに前後日含めて宿泊しながらICTSCに臨みました。泊まり込みだと当日の移動コストが無く、絶起の可能性も極限まで抑えられるので非常に良い環境でした。

オンラインでの参加のみであったため、実機を触ることができなかったのは少し残念ですが、それを踏まえても最高の大会でした。

運営の皆様、ありがとうございます。

また、何かの機会で関われたら嬉しいと思います。