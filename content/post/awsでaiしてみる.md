---
title: AWSでAIに触れてみる
description: |
  AWS(Amazon Web Service)のサービスを使ってAIを触ってみようと思います
date: 2019-03-07T11:35:29.164Z
image: /images/uploads/aws_ai.jpg
categories:
  - 技術紹介
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
今回は機械学習以外のAIサービスについてご紹介します。<br>
（機械学習系は次回以降やります）
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


アプリケーションからも呼び出して使うことができそうです。<br>
(<a href="https://docs.aws.amazon.com/ja_jp/polly/latest/dg/examples-python.html">こちらのURL</a>など参照していただければ)

### Amazon Rekognition

<img src="/images/uploads/aws_rec.png" 
style="width:100%;"/>

APIで利用できる画像解析ソリューションです。<br>
物体と背景の検出や顔認識が行えるみたいです。<br>

デモページが提供されていて、手軽に試すことができます。<br>

<img src="/images/uploads/aws_rec1.png" 
style="width:100%;"/>

試しにスティーブ・ジョブズの画像をアップロードしてみると...<br>

<img src="/images/uploads/aws_rec3.png" 
style="width:100%;"/>

Crowd(群衆)やAudience(聴衆)のスコアが高いのが気になりますが、Person・Human(人間)であることや、Speech・Lectureなどスピーチをしていることも読み取れているようですね。<br>

APIのレスポンスとしては以下のようなJSONが受け取れるようです。<br>
```
{
    "LabelModelVersion": "2.0",
    "Labels": [
        {
            "Confidence": 99.79688262939453,
            "Instances": [],
            "Name": "Crowd",
            "Parents": [
                {
                    "Name": "Person"
                }
            ]
        },
        {
            "Confidence": 99.79688262939453,
            "Instances": [
                {
                    "BoundingBox": {
                        "Height": 0.915002703666687,
                        "Left": 0.050240013748407364,
                        "Top": 0.05236506834626198,
                        "Width": 0.8705257177352905
                    },
                    "Confidence": 97.955322265625
                }
            ],
            "Name": "Person",
            "Parents": []
        }, ...
```

例えばCoopetの開発においては、動物の写真であるかを判断して無関係な画像のアップロードを禁止することもできそうですね(本当にやるのはちょっと怖いですが...)。

### Amazon Lex

自然言語理解と対話を行うサービスです。チャットボットってやつですね。<br>
残念ながら、現状は日本語対応はしていないようです。<br>

<img src="/images/uploads/aws_lex.png" style="width:100%;"/>

いくつか用意されているサンプルを開いてみた画面です。<br>
詳しくは説明できませんが、受け答えの設定を左側のエリアに設定して、Buildをすると右側のエリアでテストができるみたいですね。<br>
ざっと眺めた程度ですが、実装はなかなか難しそうな印象です。<br>

## おわりに
今回はAWSが提供するAI関連サービスのうち、機械学習以外のサービスについてご紹介しました。<br>
機械学習については別途記事を設け、簡単なアプリケーションを作って、勉強会の討論のネタにしようかなと思っています。<br>
それでは、今回はこの辺で。ここまで読んでいただき、ありがとうございました！


