---
title: Ionic CLIでIonic4を使ってみる
description: 自作SNSの開発にあたり、Ionic CLIを使ってみます
date: 2019-02-26T12:07:37.437Z
thumbnail: /images/uploads/ionic_4.png
categories:
  - Web
  - 技術紹介
tags:
  - IT学習
  - 技術紹介
  - Coopet開発
comments: true
---
## はじめに
<a href="https://elated-blackwell-51e103.netlify.com/post/2019%E5%B9%B4%E3%81%AB%E9%81%B8%E3%81%B6%E3%81%B9%E3%81%8D%E3%83%A2%E3%83%90%E3%82%A4%E3%83%ABui%E3%83%95%E3%83%AC%E3%83%BC%E3%83%A0%E3%83%AF%E3%83%BC%E3%82%AF%E3%81%AF/">先日の記事</a>で技術選定を行ったとおり、私が開発しようとしている「ペットでつながるSNS」のUIフレームワークはIonicを使うことに決定しました。<br>
今回はIonic開発の第一歩、Ionic CLIを使って見ようと思います。<br>
ちなみに私自身はIonicの業務開発経験はあるのですが、私が使ったことがあるのはIonic2でして、一方最新版のIonicはIonic4です。<br>
Ionic CLIも当時の業務では使用していなかったので、初めてということになります。<br>

## プロジェクト作成

まずはIonic CLIを私の開発PCにインストールする必要があります。<br>
以下のコマンドを実行してインストールします。<br>

```console
npm install ionic -g
```

これでionicコマンドが使えるようになります。<br>

<img src="/images/uploads/ionic_1.png" style="width:100%;"/>

次にIonicプロジェクトを作成してみます。<br>
プロジェクトの新規作成は以下のコマンドを実行して行います。

```console
ionic start [プロジェクト名] [オプション]
```
※使用できるオプションは以下のページなど参考にしてください<br>
<a href="https://ionicframework.com/docs/cli/commands/start#options">ionic start
</a>

私は以下のコマンドを実行しました。<br>

```console
ionic start coopet --type=angular
```

coopetというのは今暫定的に決めているSNSの名前です。<br>
実行すると以下のような選択肢が出ます。<br>
<img src="/images/uploads/ionic_2.png" style="width:100%;"/>

sidemenuやtabsを選ぶと、プロジェクト作成時点でサンプル画面を盛り込んでくれるみたいですね。<br>
今回はどうせならとsidemenuを選んでみました。<br>
その後npmによる依存ライブラリのインストールが行われ、それが完了すると以下のような質問が表示されます。<br>
<img src="/images/uploads/ionic_3.png" style="width:100%;"/>
Ionic Appflowはアプリ開発のプラットフォームみたいなんですが、今回は使わないので、「n」を入力します。
すると、サンプルページのmoduleやcomponentが作成されて...
<img src="/images/uploads/ionic_4.png" style="width:100%;"/>
プロジェクト作成完了しました!

## サーバー起動
それではサーバーを起動して、アプリケーションにアクセスしてみたいと思います。<br>
サーバーを起動するためには以下のコマンドを実行します。

```console
ionic serve
```
起動が完了すると、自動的にブラウザのウィンドウが開かれて画面が表示されます。<br>

