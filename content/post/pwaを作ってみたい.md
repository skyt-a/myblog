---
title: PWAを作ってみたい
description: PWAとは何なのか簡単にまとめました
date: 2019-02-22T13:33:16.065Z
thumbnail: /images/uploads/ss1.png
categories:
  - Web
tags:
  - IT学習
---
## はじめに

最近、Web業界でPWA(Progressive Web Apps)というキーワードをよく耳にするようになりました。<br>
直近ですとGoogle Play Storeで配信できるようになったことでも話題になりましたね。<br>
<a href="https://medium.com/@firt/google-play-store-now-open-for-progressive-web-apps-ec6f3c6ff3cc">Google Play Store now open for Progressive Web Apps</a><br>
今後Webを武器にフリーランスとして戦っていく中で、学んでおくべき技術の一つであることは間違いありません。<br>
今回はそんなPWAについて、簡単にですがまとめてみたいと思います。<br>

## PWAとは

端的に言えば、Webアプリケーションでスマホのネイティブアプリにしかない機能を実現できる技術といえます。<br>
具体的には以下のようなことが実現できるようになるみたいです。<br>
・オフライン時での操作
<br>
・全画面表示
<br>
・プッシュ通知 ...etc<br>
ローカルキャッシュを利用したオフライン機能や、URLバーを隠した全画面表示に、アプリを使ってもらう上で大きなアドバンテージになるプッシュ通知は元来のWebアプリケーションでは実現不可能な機能でした。<br>
PWAは何か新しいものを作るというよりは、既存のアプリケーションに機能追加して更に進化させる意味合いが強いようで、その考えがProgressiveの由来になっているとのこと。<br>

## 導入事例

以下のサイトがよくまとまっていました。<br>
<a href="https://www.i3design.jp/in-pocket/5997">モバイルWebの高速表示＆アプリライクな操作性を実現する、AMP＆PWA導入サイト事例8選</a><br>
<a href="https://press.monaca.io/atsushi/3040">PWAで何ができる？国内のPWA対応サイト５選を紹介
</a><br>
InstagramやTwitterなどのSNSをはじめ、中には「アイドルマスターシャイニーカラーズ」といったゲームもあるようです。(実際に触ってみましたが、ほとんどネイティブアプリとの違いを感じられず驚きました)<br>
<br>
<img src="/images/uploads/ss1.png" />
## 対応状況

### Safari(iOS)

以前は未対応だったが、今では以下のような機能も使えるようです(iOS 11.3時点)。<br>
・位置情報
<br>
・方位磁石、速度メーター、ジャイロスコープなどのセンサー
<br>
・カメラ
<br>
・音声出力
<br>
・スピーチ
<br>
・音声合成
<br>
・Apple Pay
<br>
・Payment Request APIを使ってApple Payの起動<br>

### Android

iOSにできない以下のようなこともできるようです。<br>
・音声認識<br>
・バックグラウンド同期<br>
・プッシュ通知
<br>
・Splash screenとデバイスの向きのカスタマイズ<br>
・50MB以上のデータを保存できる<br>
・BLEデバイスからのBluetoothアクセス
<br>

## おわりに

実際にどういう仕組みで上記の機能を実現しているのか、どうやって実装すればよいのかというところが非常に気になるので、今私が開発しようと思っている「ペットでつながるSNS」をPWAで作ってみようと思います。<br>
現在のプロトタイプはPC版を想定していたので、技術選定からやり直す必要がありそうですが、自分のやりたいことをやることを優先してみたいと思います!<br>
