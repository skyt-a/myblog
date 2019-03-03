---
title: NetlifyとGitHubを連携させてIonic Appをデプロイしてみる
description: NetlifyとGitHubを連携させてIonic Appをデプロイしてみます
date: 2019-03-03T03:39:13.055Z
image: /images/uploads/netlify5.png
categories:
  - 技術紹介
  - netlify
tags:
  - 技術紹介
  - netlify
comments: true
---
## はじめに
現在開発しているSNS「Coopet」ですが、<a href="">PWA</a>で作成しようと考えているので、スマートフォンでの実際の動作を確認するためにテストデプロイ環境がほしいなーと思っていました。<br>
そこで、このブログもデプロイしている、<a href="https://www.netlify.com/">Netlify</a>というサービスを利用することにしました。<br>
今回はNetlifyにIonicで開発したプロジェクトをデプロイする過程を解説したいと思います。<br>

## Netlifyとは
<a href="https://www.netlify.com/">Netlify</a>は基本無料で利用できる静的ホスティングサービスです。<br>
以下のような特徴があります
### 高パフォーマンス
パフォーマンスがとにかく高く、ビルド・ホスティング・デプロイまで<span class="strong-str">長くても１分程度</span>で完了します。<br>
日本にもちゃんと拠点もありますし、サーバーは完全にスケーラブルとのことです。<br>

### GitHub、GitLab、Bitbucketと連携可能
GitHubのようなプロジェクト管理サービスと連携できます。<br>
GitHubに<span class="strong-str">ソースコードをコミットするだけ</span>で、Netlifyが勝手にビルド・デプロイ・ホスティングしてくれて、サービスを更新できるので非常に便利です。<br>
また今回は解説しませんが、デプロイの完了をSlackに通知することも可能です。<br>

### 無料でSSL/HTTPS
完全無料のSSL/HTTPSがワンクリックで実現できます。</br>
PWAはHTTPS環境でないとその機能を発揮しないので、非常にありがたいです。<br>

## デプロイしてみる
まずは<a href="https://www.netlify.com/">Netlify</a>にアクセスします
<img src="/images/uploads/netlify.png" style="width:100%;" />
「Get Started for free」を押下します。<br>
<img src="/images/uploads/netlify2.png" style="width:100%;" />

そうするとサインアップ方法を選択する画面が表示されます。<br>
今回はGitHubを選択します。<br>
<img src="/images/uploads/netlify3.png" style="width:100%;" />
するとGitHubへのサインインを求められるので入力します。<br>
<img src="/images/uploads/netlify4.png" style="width:100%;" />
サインインするとNetlifyとGitHub連携の認証を求められるので「Authorize netlify」を押下して認証します。</br>
<img src="/images/uploads/netlify5.png" style="width:100%;" />

するとNetlify側に戻ってきます。<br>
QuickStart Guideを読み飛ばして...
<img src="/images/uploads/netlify6.png" style="width:100%;" />

「New Site from Git」をクリックします。<br>
<img src="/images/uploads/netlify7.png" style="width:100%;" />

どのサービスと連携してデプロイするかを選択する画面に移動するので、「GitHub」をクリックします。<br>

<img src="/images/uploads/netlify8.png" style="width:100%;" />

すると新しいウィンドウでGitHubのリソースにNetlifyがアクセスことを許可するための画面が表示されるので、「Authorize Netlify By Netlify」ボタンをクリックして許可します。<br>

<img src="/images/uploads/netlify9.png" style="width:100%;" />

するとNetlify連携にどのリポジトリを連携するかを選択する画面が表示されます。<br>
全てのリポジトリを連携してもいいですが、個別のリポジトリに限定したい場合はOnly select repositoriesを選択して連携したいリポジトリを選びましょう。<br>
選択したら「Install」をクリックします。<br>
