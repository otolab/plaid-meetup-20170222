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

「KARTE」

![KARTE](https://karte.io/commons/images/index/video_func_01.gif)

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
これから本格導入を進めていきます


---

class: center, middle, inverse

# CIアンチパターン

CI アンチパターンを3つ紹介します。

---

## CIアンチパターン1

### 責務が多すぎる

テストがコケたのでデバッグしよう！  
　　　　　　⇓  
「CIが何をしているのか把握できない」

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
　　　　　　⇓  
「CIと同じ環境を構築できない」

1. 開発環境 (Mac/Windows)
2. 検証環境 (インフラエンジニアが適当に運用してる新しい Linux)
3. CI/CD (情報不明の謎の Linux)
4. 本番環境 (運用開始から更新されていない Linux)

(＊弊社の環境ではありません)

---

## CIアンチパターン3

### CI で発生した問題の再現ができない

テストがコケたのでデバッグしよう！  
　　　　　　⇓  
「問題が再現できない」

1. CIと同じ環境を用意できない
2. CI用に独自のビルド・デプロイスクリプトを使ってる
3. 問題の原因が特定できない(環境の問題か、実装の問題か)
4. 解決してもCIを動かさないと動作を確認できない

---

class: center, middle, inverse

# Wercker を使うべき5つの理由

5つもなかった。ごめんなさい！  
3つです！

---

## Wercker の基本

.logo[
![wercker logo](https://raw.githubusercontent.com/wercker/wercker-identity/master/wercker_logo_green.png)
]

- 基本無料
- stackshare の Continuous Integration ランキングで6位
https://stackshare.io/continuous-integration
- 設定を wercker.yml に書いて github, bitbucket のリポジトリと連携するだけで使える

---

## Wercker を使うべき理由 1

### Docker ネイティブプラットホーム

.logo[
![Containers](https://www.wercker.com/hs-fs/hubfs/container_native_purple_215x125.png?t=1487153244593&width=216&name=container_native_purple_215x125.png)
]

Wercker は Docker を使うことが前提となっています。  
Dockerfile を書く必要はありません。他のCIと同様に yaml を書くだけです。
Docker をベースにしているので Docker コンテナの起動が早いのが特徴です。

---

## Wercker を使うべき理由 2

### ローカルでタスクを実行できる

Client を使ってローカルでリモートと同じタスクを実行できます(後ほど紹介)。  
wercker.yml に書いたスクリプトをローカルで動かせるので、デバッグが非常に簡単です。

```
USAGE:
   wercker [global options] command [command options] [arguments...]

COMMANDS:
   build, b     build a project
   dev          develop and run a local project
   check-config check the project's yaml
   deploy, d    deploy a project
   detect, de   detect the type of project
   login, l     log into wercker
   logout       logout from wercker
   pull, p      pull <build id>
   version, v   print versions
   doc          Generate usage documentation
   help, h      Shows a list of commands or help for one command
```

---

## Wercker を使うべき理由 3

### マイクロサービスに対応している

.logo[
![Microservices](https://www.wercker.com/hs-fs/hubfs/microservices_purple_215x125.png?t=1487153244593&width=214&name=microservices_purple_215x125.png)
]
Wercker Service という機能で複数のコンテナを使うことができます(後ほど紹介)。  
データベースの Docker コンテナをアプリとは別のコンテナとして扱えます。
もちろん Service 用の Docker コンテナを自作することもできます。

---

## それ以外にも使える Wercker の機能

- タスクのワークフローの作成/変更が簡単  
GUI または API で設定・実行できる  
Workflow > Pipeline > Step
- 他サービスとの連携
![customisable and  extensible](https://www.wercker.com/hs-fs/hubfs/Platform_context_diagram.svg?t=1487153244593&width=1000&height=372&name=Platform_context_diagram.svg)

---

## Wercker のイケてないところ

- スペルが難しい  
初めは間違えずに入力できない。  
何も見ずに正しく"wercker"と書けるようになったら中級者。

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
### Wercker client のセットアップ

以下の手順で wercker cli をセットアップします。

1. docker をインストールする(既にセットアップ済みですよね？)
2. wercker cli をインストールする
3. wercker.yml を書く

---

## Wercker をローカルで動かす
### Wercker client の実行

```
wercker dev --pipeline build
```

ローカルにセットアップした docker engine 上で wercker.yml に記述した任意のタスク(pipeline)を実行できます。  
つまり、wercker server 上で実行するのと全く同じタスクをローカル環境で動作させられます。  
どちらも docker 環境で動作するので、原理的には(環境変数以外は)全く同じ挙動をします。

---

## Werckerで複数のサービスを使う
### service を使わない場合
1 Container 2 Services
1つのコンテナに app と db が同居する

```
build:
  steps:
    - install-packages:
        packages: mysql-server libmysqlclient-dev
    - pip-install
    - script:
        name: python build
        code: |
            python build.py
```

---

## Werckerで複数のサービスを使う
### service を使う場合
2 Container 2 Services  
docker link 機能を使って app と db をつなぐ

```
build:
  services:
    - id: mysql:5.7
      env:
        MYSQL_USER: test
        MYSQL_PASSWORD: secret
        MYSQL_DATABASE: user
        MYSQL_RANDOM_ROOT_PASSWORD: yes
  steps:
    - pip-install
    - script:
        name: python build
        code: |
            python build.py
```

---

class: center, middle, inverse

# 発表のまとめ

---

## まとめ

Wercker を導入すると以下のことができるようになります。

- CI と同じ環境を構築できる
- CI と同じタスクを実行できる
- Dockerfile を書かずに Docker を導入できる

Dockerfile が書けるようになったら Wercker を卒業しよう！

今日使った wercker のファイルは以下においてあります。
https://github.com/algas/wercker-turotial

---

## エンジニア募集中！

株式会社プレイド Engineer/Hunter  
山内雅浩 [@algas](https://github.com/algas)  

- 東京大学大学院理学系研究科 博士課程中退。主に人工衛星の開発を担当。
- 2007年未踏本体採択開発者。
- ゲーム開発ベンチャー、アプリ開発会社CTOを経て、2016年からプレイドに。
- 趣味はハンティング。

https://algas.github.io/plaid-meetup-20160222

### プレイドは一緒に未来を創るエンジニアを募集しています！
