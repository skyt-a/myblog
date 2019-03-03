---
title: NetlifyとGitHubを連携させてIonic Appをデプロイしてみる
description: NetlifyとGitHubを連携させてIonic Appをデプロイしてみます
date: 2019-03-03T03:39:13.055Z
image: >-
  https://raw.githubusercontent.com/RinGoku/myblog/master/static/images/uploads/1024px-ionic-logo-landscape.svg.png?token=AjCEx9G7L3YGpZ3gMHSk4wH14rq7cYxHks5ce0ybwA%3D%3D
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
そこで、このブログもデプロイしている、<a href="https://app.netlify.com/">Netlify</a>というサービスを利用することにしました。<br>
今回はNetlifyにIonicで開発したプロジェクトをデプロイする過程を解説したいと思います。<br>

## Netlifyとは
<a href="https://app.netlify.com/">Netlify</a>は基本無料で利用できる静的ホスティングサービスです。<br>
以下のような特徴があります
### 高パフォーマンス
パフォーマンスがとにかく高く、ビルド・ホスティング・デプロイまで長くても１分程度で完了します。<br>
日本にもちゃんと拠点もありますし、サーバーは完全にスケーラブルとのことです。<br>

### GitHub、GitLab、Bitbucketと連携可能
GitHubのようなプロジェクト管理サービスと連携できます。<br>
GitHubにソースコードをコミットするだけで、Netlifyが勝手にビルド・デプロイ・ホスティングしてくれて、サービスを更新できるので非常に便利です。<br>
また今回は解説しませんが、デプロイの完了をSlackに通知することも可能です。<br>


