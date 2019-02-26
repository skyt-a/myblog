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

```shell
ionic start [プロジェクト名] [オプション]
```
※使用できるオプションは以下のページなど参考にしてください<br>
<a href="https://ionicframework.com/docs/cli/commands/start#options">ionic start
</a>

私は以下のコマンドを実行しました。<br>

```shell
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

```shell
ionic serve
```
起動が完了すると、自動的にブラウザのウィンドウが開かれて画面が表示されます。<br>

<img src="/images/uploads/ionic_5.png" style="width:100%;"/>

おおー、結構ちゃんとしてる。<br>
今回選択したのは「sidemenu」なのでもちろんサイドメニューもありますね。<br>
開くとこんな感じです。<br>
<img src="/images/uploads/ionic_6.png" style="width:100%;"/>

もちろんListを選ぶと他の画面へ遷移します。<br>

<img src="/images/uploads/ionic_7.png" style="width:100%;"/>

## ソースを読んでみる

作成されたプロジェクトのソースに軽く目を通してみましょう。<br>

### package.json

<img src="/images/uploads/ionic_8.png" style="width:100%;"/>

package.jsonを確認してみるとAngularは最新版の7、@ionic/angularは4ですね。<br>
今回はプロジェクト作成時に--type=angularを指定したのでこの構成になっていますが、他にも設定できる値があり、それ次第でこの辺の構成は変わるみたいですね。<br>

<img src="/images/uploads/ionic_9.png" style="width:100%;"/>

devDependenciesの方も確認すると、@angular/cliにも依存していることがわかります。<br>
試しにng serveコマンドも実行してみましたが、問題なく起動でき、ionic serveで起動したときと同じページにアクセスできました(あえてこちらを使う意味はないでしょうが...)<br>
その他@angular/cliではおなじみのKarma+Jasmineのテスト環境も使えるみたいですね。<br>

### app.component.html

Angularをベースにしていることもあり、ファイル構成などは@angular/cliで作成できるプロジェクトと似通っています。<br>
/src/app/app.component.htmlも存在していて、以下のような記述がなされています。<br>

<img src="/images/uploads/ionic_10.png" style="width:100%;"/>

Ionicが提供する、ion-で始まる独自タグによってアプリケーション構造が記述されています。<br>
ここでは主にメインコンテンツのルーティング(22行目,ion-router-outlet)の記述と、サイドメニュー(11～18行目)の記述がなされていますね。<br>

ルーティング設定は/src/app/app-routing.module.tsに記述されており、Angularの仕組みに従った記述がなされています。<br>

<img src="/images/uploads/ionic_11.png" style="width:100%;"/>

### list.page.spec.ts

<img src="/images/uploads/ionic_12.png" style="width:100%;"/>


package.jsonにはJasmineに依存している記述があったので、当然のごとくテストコードもサンプルに含まれていました。
npm testコマンドを実行することでテストを実行することももちろんできました。<br>

<img src="/images/uploads/ionic_13.png" style="width:100%;"/>

## おわりに

今回はIonic CLIを使って、プロジェクトの新規作成、サーバーの起動と動作確認及びソースコードを軽く確認するということをやってみました。<br>
ざっと読んだ印象だと、Ionic2と比較してめちゃくちゃ大きく変わったということもなさそうな雰囲気なので学習コスト少なめで進めていけそうです。<br>
ペットとつながるSNS「Coopet」の開発に関しては、このブログで記事を通してお伝えしていければと思います。<br>

感想やご意見等ございましたら、<a href="https://twitter.com/RinGoku98">私のTwitter</a>までお気軽にどうぞ。
