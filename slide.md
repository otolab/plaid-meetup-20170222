name: inverse
layout: true
class: center, middle, inverse

---

# CI に Wercker を使うべき
# 5つの理由
### ~ Wercker で始める Docker 入門 ~


株式会社プレイド  
Engineer/Hunter

山内雅浩  
.blue-text[@algas]

---

layout: false

# Agenda

1. サービス紹介
2. 弊社のDocker導入状況
3. CIアンチパターン
4. Wercker を使うべき5つの理由
5. Werckerの実践的な使い方
6. Werckerのイケてないところ
7. 発表のまとめ

---

class: center, middle, inverse

# サービス紹介

---


（動画）

---

class: center, middle, inverse

# 弊社のDocker導入状況

---

## システム構成図

---

## ビルドとデプロイの仕組み

---

## Docker導入率

10％くらい  
まだ全然できてない！


---

class: center, middle, inverse

# CIアンチパターン

CI アンチパターンを3つ紹介します。

---

## CIアンチパターン1

### 責務が多すぎる

テストがコケたのでデバッグしよう！
「CIが何をしているのか良くわからない」

CIを設定した人しかCIがやっていることの全容を把握できない。(Jenkinsおじさんの職人芸)  
以下、よくCI/CDに設定されやすい責務の具体例。

1. OSの基本設定
2. 実行ユーザの作成/アクセス権限の設定
3. 基本OSパッケージのインストール
4. データベースのインストール
5. 言語のインストール
6. リポジトリの展開
7. フレームワーク/ライブラリのインストール
8. アプリの設定とビルド
9. テスト実行環境の設定
10. テストデータの導入
11. ユニットテストの実施
12. e2eテストの実施
13. アプリの配布
14. チャット/メールでの通知

---

## CIアンチパターン2

### 開発環境とCI実行環境が異なる

テストがコケたのでデバッグしよう！
「CIと同じ環境を構築できない」

多くのプロジェクトでは少なくとも4つの異なる環境になりえる。  
環境ごとにOSが異なるために、OSパッケージやライブラリのバージョンが異なる。

1. 開発環境 (Mac/Windows)
2. 検証環境 (社内インフラが適当に運用してるCentOS)
3. CI/CD (OS 不明の謎の Linux)
4. 本番環境 (Amazon Linux)

インフラエンジニアにしか再現できない各種環境

---

## CIアンチパターン3

### CI で発生した問題の再現ができない

テストがコケたのでデバッグしよう！
「解決するための問題を再現できない」

- CIと同じ環境を用意できない(CIアンチパターン2)
- CI用に独自のビルドスクリプトやデプロイスクリプト
- 問題の再現ができない(ローカルだと動くけどCIでは動かない)
- 解決してもCIを動かさないと動作を確認できない

---

class: center, middle, inverse

# Wercker を使うべき5つの理由

5つもなかった。ごめんなさい！  
3つです！

---

## Wercker の基本

（ロゴ）

- 基本無料
- stackshare の Continuous Integration ランキングで6位
https://stackshare.io/continuous-integration
- 設定を wercker.yml に書いて github, bitbucket のリポジトリと連携するだけで使える

---

## Wercker を使うべき理由 1

### タスクを実行するのにDockerコンテナを使う

Wercker は Docker を使うことが前提となっていて Docker コンテナの上でタスクを実行するようになっています。  
Dockerfile を書く必要はありません。他のCIと同様にymlを書くだけです。
Docker をベースにしているので Docker コンテナの起動が早い。

---

## Wercker を使うべき理由 2

### ローカルでタスクを実行できる

Wercker Client を使ってローカルの Docker 環境でリモートと全く同じタスクを実行できます(後ほど詳しく紹介)。
リモートで動かすために wercker.yml に書いたスクリプトをそのままローカル(Docker)で動かせます。
デバッグが非常に簡単です。

---

## Wercker を使うべき理由 3

### 複数のDockerコンテナをCIから利用可能

Wercker Service という機能でデータベースなどを使うことができます(後ほど詳しく紹介)。  
wercker.yml にデータベースのインストール設定を書く必要はありません。  
Service の機能も Docker コンテナで実行されます。  
事前に自前で用意したデータベースなどの Docker コンテナを使うこともできます。

---

## それ以外にも使える Wercker の機能

- タスクのワークフローの作成/変更が簡単
- 他サービスとの連携

---

## Wercker のイケてないところ

- スペルが難しい  
初めは間違えずに入力できない。  
10回ほど間違えた後に何も見ずに正しく"wercker"と書けるようになったら中級者。

- タスクのトリガーが不自由  
一度も実行されてないタスクはGUI(Web Interface)からは実行できない。

- Dockerfileのビルドに向いてない  
DockerHub, Quay.io を使いましょう。

- 直近でダイナミックな機能変更があった  
Wercker が box を Docker に切り替えたために下位互換性がなくなった。  
wercker関連の古いブログはほとんど役に立たないので、参考にする際には記事の作成日時を確認してください！

---

class: center, middle, inverse

# Wercker の実践的な使い方

---

## Wercker をローカルで動かす
### Wercker client のインストール

---

## Wercker をローカルで動かす
### Wercker client の実行

wercker.yml
(デモ？)

---

## Werckerで複数のサービスを使う
### メインコンテナに mysql-server を入れる
service を使わない場合の一般的な構成  
(構成図)  
wercker.yml

---

## Werckerで複数のサービスを使う
### service で mysql-server を使う
service を使う場合の構成  
(構成図)  
wercker.yml

---

class: center, middle, inverse

# 発表のまとめ

---

## まとめ

Wercker を導入すると以下のことができるようになる

- CI と同じ環境を構築できる
- CI と同じタスクを実行できる
- Dockerfile を書かずに Docker を導入できる

Dockerfile が書けるようになったら Wercker を卒業しよう！

---

## エンジニア募集中！

発表したのはこんな人  
株式会社プレイド Engineer/Hunter  
山内雅浩 [@algas](https://github.com/algas)  

- 東京大学大学院理学系研究科 博士課程中退。主に人工衛星の開発を担当。
- 2007年未踏本体採択開発者。
- ゲーム開発ベンチャー、アプリ開発会社CTOを経て、2016年からプレイドに。
- 趣味はハンティング。

### プレイドは一緒に未来を創るエンジニアを募集しています！
