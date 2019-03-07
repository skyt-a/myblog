---
title: AWSでAIしてみる
description: AWS(Amazon Web Service)のサービスを使ってAIを触ってみようと思います
date: 2019-03-07T11:35:29.164Z
image: /images/uploads/aws_polly1.png
categories:
  - 技術紹介
  - AWS
tags:
  - IT学習
  - AWS
comments: true
---
## はじめに
私は1ヶ月に1度、社内で開催される勉強会に参加しているのです。<br>
そして次の討議テーマが「AI」についてなんです。<br>
なのでとりあえず気軽にAIに触れられるようなサービスはないかなーと探していたところ、Coopetの開発でも使っているAWSにもAI関連のサービスがいくつかあるということがわかりました。<br>
今回はそんなAWSのAI関連サービスを紹介したいと思います。<br>
(AWSのアカウント作成方法は今回は説明しません。機会があればそれも記事にしたいと思います)

## サービス紹介
### Amazon Polly
<img src="/images/uploads/aws_polly1.png" style="width:100%;"/>

AmazonPollyは24ヶ国語に対応し多言語文章を自然な音声で読み上げてくれるサービスです。<br>

こんな画面にテキストを入力することで試すことができます。<br>
男性声、女性声も選べるみたいですね。<br>

<img src="/images/uploads/aws_polly.png" 
style="width:100%;"/>

またレキシコンという機能を使うと、発音をカスタマイズできるみたいです。<br>

<img src="/images/uploads/aws_polly2.png" 
style="width:100%;"/>

AWS CLIというCUIツールでコマンドラインから実行することも可能です。<br>
例えば、以下のコマンドで「こんにちは」と女性の声で話すmp3ファイルが生成されます。<br>

```
aws polly synthesize-speech --output-format mp3 --voice-id Mizuki --text 'こんにちは' hello.mp3
```
実際に生成されたデータがこちらです。<br>
<audio src="/images/uploads/hello.mp3" controls></audio>


Webアプリからも呼び出して使うことができそうです。<br>
(<a href="https://docs.aws.amazon.com/ja_jp/polly/latest/dg/examples-python.html">こちらのURL</a>など参照していただければ)

### Amazon Polly

