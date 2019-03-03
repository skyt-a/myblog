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
