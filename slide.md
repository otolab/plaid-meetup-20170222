name: Naoto Kato
layout: true
class: center, middle, inverse

---

# Docker社が買った会社たち
### ~ 買収から見えるもの ~

株式会社プレイド  
加藤 尚人

(github: @otolab / twitter: @otoan52)

???

0:20

* PLAID エンジニアの加藤です。

* いまはデータ分析
* Dockerからはちょっと遠ざかっているが、使っている歴は長め
* Dockerは2014年から

* ネタない？ということでLTに。

* Dockerいろいろ買ってるなーという印象
* エコシステム→統合システムへの方向転換

* 気になっていたので調べた

---

layout: false

# Agenda

1. 背景にあるもの
2. 買収された企業
  * Orchard Laboratories
  * Koality
  * SocketPlane
  * Kitematic
  * tutum
  * Unikernel Systems
  * Conductant
  * Infinit
3. 参考/引用記事

???

0:40

* LTなのでシンプルに
* 引用記事が多い。コメントなど
* 最後に付録として付けます

---

class: center, middle, inverse

# 背景にあるもの

???

一連の買収の背景とは？

---

## vs Kubernetes?

[2013/3] Docker オープンソース化

[2014/6/10] Google AppEngine での Docker 正式サポート、Kubernetes の公開

[2014/7/10] Kubernetes コミュニティに参加

[2014/12/4] Docker Machine、Swarm、Compose の発表

[2014/6/9] Docker 1.0 リリース

[2015/06/22] Docker、CoreOS、AWS、Googleら、コンテナ標準化団体OCPを立ち上げ

[2015/7/21] Kubernetes 1.0 リリース

???

1:00

* 結論から言うと、Kubernatesへの対抗では
* Google社内のシステムがベース。Dockerにはのっているが、用語などが別。
* kubernatesが6月
* 最初の買収が7/23。
* 運用されはじめるとオーケストレーションが注目ポイントに
* 一気に進んでしまった？

* [Docker 誕生から現在までの過程を俯瞰する 1 (2013/3～2014/10)](http://qiita.com/Arturias/items/c12441c87f4de3102ea7)

から抜粋

---

class: center, middle, inverse

# 買収された企業

---

## DOCKER MILESTONES

https://www.docker.com/company

- March 3, 2016: Docker Acquires Conductant
- January 21, 2016: Docker Acquires Unikernel Systems to Extend the Breadth of the Docker Platform
- October 20, 2015: Docker Acquires Tutum to Accelerate Production Deployments of Dockerized Distributed Applications
- March 12, 2015: Docker acquires Kitematic
- March 4, 2015: Docker acquires SocketPlane
- October 7, 2014: Docker acquires Koality
- July 23, 2014: Docker acquires Orchard (Fig)

???

1:20

* 公式のリスト。コレをちょっと深ぼったもの
* Infinitがまだ載っていない
* いずれも発音がよくわからないのでいい加減

---

## Orchard Laboratories

2014/07/23

* Fig ... `fig.yml` / `fig up`
* Orchard ... コンテナをホストするサービス → close

* "OrchardとFigはいずれも、パズルの小さなピースにすぎない。Figは人気を博したが、Orchardはそれほどではない。したがって、当社はこれを10月23日で終了する。移行ガイドがあり、..."

* Fig => Docker Compose

???

1:40

* fig.yml, fig　up見覚えアリますよね。
* 2ラインの内、Orchardはクローズ。
* その時のOrchardのブログ。「小さなピース」と呼んでいるのが印象的

---

## Koality

2014/10/07

* テストツールなど継続的統合ソリューション技術を開発するベンチャー企業

* “人材獲得が主な目的だ。彼らはデベロッパに対する直観が優れているし、デベロッパのライフサイクルを熟知している。クラウドとオンプレミス両方の経験知識があるが、うちが彼らのプロダクトを統合するつもりはない。統合するのは、チームだ”

* => Docker Hub Enterprise

???

2:00

* オンプレミスでのノウハウなど。
* ターゲットは4名ほど？

---

## SocketPlane

2015/03/04

* Software-Defined Networkingの技術を開発してきたスタートアップ

* "DockerにおけるSocketPlaneチームの明確な焦点は、パートナーコミュニティとの連係によってリッチなネットワークAPI群を完成させ、ネットワーク管理者やシステム管理者、アプリケーションデベロッパーのニーズを満たすことにある。"

* => Docker Swarm
  - overlay

???

2:20

* flannel（フランネル）なども有名
* LinuxのブリッジのIFを使わない
* overlayモード。1.9で有効に

---

## Kitematic

2015/03/12

* VirtualBoxとboot2dockerのフロントエンドツール

* => Docker Toolbox / Docker for Mac

???

2:40

* イメージやコンテナをwebapp可視化して管理
* Docker Toolboxの一部として提供を継続
* Docker for Macでも使えるメニューからダウンロードと呼び出しができる

---

## Tutum

2015/10/22

* コンテナをクラウド上のサーバで実行・管理するサービス

* "Dockerに加わると決定した理由の1つとして、開発者があらゆるインフラ上であらゆるアプリケーションを構築して動かすことを実現するという点で一致したためだ。これはわれわれが2年前に設定したゴールであり、Dockerがやっていることでもある"

* tutum => Docker Cloud

???

3:00

* クラウド環境の管理APIを叩いて、クラスタ作成やコンテナの管理をサポート
* Docker Cloudに。
試しにアカウント取って一ヶ月くらい後に

---

## Unikernel Systems

2016/02/04

* カスタマイズされたカーネルをハイパーバイザ上で高速起動する

* “Dockerプラットホームがスタックのずっと下の方〔カーネルレベル〕でも問題解決に向けてきわめてアグレッシブであることを、お分かりいただけるだろう” “今回の買収はわれわれに、これらの問題を解決するための、さらに多くの能力を与える”

* => ?

???

3:20

* 「一連の買収の中では地味だが、大きな一歩」
* コンテナイメージ毎にカスタマイズされたKernelをコンパイルし、HVで高速起動する？
* LXCを置き換えるもの
* どこに組み込まれるかは不明

---

## Conductant

2016/03/03

* twitterでApache Auroraの開発チーム

* "このプロジェクトによって弊社は、Docker DNAの基本的な部分を強化していく。弊社はつねに、自分たちのソフトウェアの運用のプロでもなければならない"

* => Docker Swarm?

???

3:40

* twitterが開発してApacheに寄贈、開発者チームが独立
* 社名は知られていなかったが、Apache Auroraの開発者
* 自分は詳しくないのだけど。
* クラスタを一つのマシンとして管理する
* Docker Swarmを強化するとされている

---

## Infinit

2016/12/08

* P2Pファイル転送アプリ

* "Infinit の技術を使えば、我々はこれまでに無かったセキュアな分散型ストレージを提供でき、ユーザは Docker を使って、ステートフルなサービスやレガシーなエンタープライズアプリをデプロイするのがさらに容易になるだろう。このしくみは、オープンなモジュール設計の形で提供されるので、オペレータは簡単に既存のストレージシステムを統合したり、高度な設定を調整したり、その機能を無効にしたりすることができるだろう。"

* => ?

???

4:00

* InifitはOSS化
* Storage Driver?

---

class: center, middle, inverse

# 参考/引用記事

---

## 参考/引用記事 1

* 参考
  - [Docker 誕生から現在までの過程を俯瞰する 1 (2013/3～2014/10)](http://qiita.com/Arturias/items/c12441c87f4de3102ea7)

???

4:10
* 買収にとどまらない流れを把握するのに良い記事。３まである

---

## 参考/引用記事 2

* Orchard Laboratories
  * [Dockerの構成管理「Fig」で開発環境を整備しよう](http://knowledge.sakura.ad.jp/tech/2661/)
  * [Docker、コンテナ管理技術の新興企業Orchard Laboratoriesを買収](https://japan.zdnet.com/article/35051296/)

* Koality
  * [Dockerが人材獲得を目的としてKoalityを買収…ハイブリッドクラウド技術を充実](http://jp.techcrunch.com/2014/10/08/20141007docker-acquires-koality-in-engineering-talent-grab/)

???

* 古いツール名の記事でも参考になる情報が出てきたりします

4:20

---

## 参考/引用記事 3

* SocketPlane
  * [Docker、Software-Defined NetworkingのSocketPlaneを買収。Dockerネイティブなネットワーク機能を構築へ](http://www.publickey1.jp/blog/15/dockersoftware-defined_networkingsocketplanedocker.html)
  * [Docker, Inc.に買収されたSocketPlaneに関する雑多な話](http://fstn.hateblo.jp/entry/2015/03/31/004319)
  * [Docker Overlay Networking](http://windsock.io/docker-overlay-networking/)

* Kitematic
  * [Docker Buys Kitematic, Which Simplifies Docker on Mac](http://www.datacenterknowledge.com/archives/2015/03/12/docker-buys-kinematic-which-simplifies-docker-on-mac/)
  * [Docker ToolboxでMac OSXにDocker環境を最速で構築する](http://blog.takanabe.tokyo/2015/11/22/1510/)

???

4:40

* Ki **t** ematic。
* Docker Buys Kitematicの記事のリンク、ヘッドタグ内のタイトルがkinematicになっています。

---

## 参考/引用記事 4

* tutum
  * [DockerがTutumを買収してコンテナアプリケーションの稼働管理サービスを充実](http://jp.techcrunch.com/2015/10/22/20151021docker-acquires-cloud-startup-tutum-for-container-shipping-and-management/)
  * [Docker Cloud 1.0登場へ。買収したTutumをリブランドしDocker Hub と統合](http://www.publickey1.jp/blog/16/docker_cloud_10.html)

* Unikernel Systems
  * [DockerがUnikernelを買収。1秒以下で起動しハイパーバイザで安全に分離されるUnikernelが新たなコンテナの仲間入り](http://www.publickey1.jp/blog/16/docker_unikernel.html)
  * [コンテナを超えてマイクロサービス技術の広い世界を目指すDockerがUnikernel Systemsを買収](http://jp.techcrunch.com/2016/01/22/20160121docker-acquires-unikernel-systems-as-it-looks-beyond-containers/)

???

4:50

* Unikernel調べて勉強になった

---

## 参考/引用記事 5

* Conductant
  * [DockerがAuroraによるオーケストレーションサービスのConductantを買収、「運用経験は良質な開発のベース」](http://jp.techcrunch.com/2016/03/04/20160303docker-acquires-conductant-as-it-looks-to-help-businesses-run-large-scale-systems/)
  * [Docker、Apache Aurora開発者らのチームを買収。Swarmとの統合によるオーケストレーション機能の強化でMesosやKubernetesと競合する方向へ](http://www.publickey1.jp/blog/16/docker_apache_aurora.html)

* Infinit
  * [Dockerが分散ストレージのInfinitを買収。Dockerに欠けていた最後のピースであるストレージが埋まった](http://www.publickey1.jp/blog/16/dockerinfinitdocker.html)
  * [コンテナ型仮想化技術の「Docker」、P2Pファイル転送アプリの「Infinit」を買収しオープンソース化へ](http://thebridge.jp/2016/12/docker-acquires-file-syncing-and-sharing-app-infinit-will-open-source-the-software)

???

5:00

* 「Kubernetesと競合する方向へ」という記事名がでてきた

---

class: center, middle, inverse

## ありがとうございました！


