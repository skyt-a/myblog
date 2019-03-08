---
title: Amazon SageMakerを使ってみる【前編】
description: |-
  Amazon SageMakerという機械学習サービスを使ってみます。
  今回は機械学習用の画像データを用意する過程をご紹介します。
date: 2019-03-07T13:50:54.264Z
image: /images/uploads/degu.jpg
categories:
  - 使ってみるシリーズ
  - AWS
tags:
  - IT学習
  - AWS
comments: true
---
## はじめに

社内勉強会の討論ネタの確保のため、<a href="https://elated-blackwell-51e103.netlify.com/post/aws%E3%81%A7ai%E3%81%AB%E8%A7%A6%E3%82%8C%E3%81%A6%E3%81%BF%E3%82%8B/">前回の記事</a>ではAWSが提供している機械学習以外のAI関連サービスについてご紹介しました。<br>
今回はAWSが提供する機械学習サービス「Amazon SageMaker」を使ってみようと思います。<br>
なお、AIは完全初心者で勉強中の身なので、内容に間違いがある可能性があります。<br>
認識違いなどございましたら、ご指摘よろしくお願いします。<br>
(なお今回の作業にあたり、<a href="https://dev.classmethod.jp/cloud/aws/sagemaker-umaibo-object-detection/">こちらの記事</a>を参考にさせていただきました)

## 機械学習の流れ

超大雑把に言えば、学習用のデータを用意して、そのデータをAIのエンジンに読み込ませて学習させて、学習用のデータ以外のデータを渡して精度をチェックして、学習用データを変えてみたり、学習のパラメータを変えてみたりを繰り返していくイメージ。<br>
今回の記事では最初の最初、学習用のデータを用意するところを解説したいと思います。<br>

## そもそもどんな機械学習を行うのか

一口に機械学習といっても、できることは色々ありますが、今回は「物体検出」を行いたいと思います。<br>
物体検出とは、画像の中から定められた物体の位置とその分類を検出することを指します。<br>
そして今回検出するのは、私もペットとして飼育している「デグーマウス」という動物です。<br>

<img src="/images/uploads/degu.jpg" style="width:100%;" />

つまり、対象の画像からこのデグーマウスの位置を検出する機械学習を行おうと思います。<br>

## 学習用データを用意する

物体検出の学習用データは検出する物体が含まれた画像と、その画像内のどこに物体があるのかという正解情報です。<br>
つまり今回行う作業は、デグーマウスの画像を大量に集め、その画像内のどこにデグーマウスが写っているのかをマーキングするというものになります(この作業をタグ付けと呼びます)。<br>

さてそれでは早速、デグーマウスの画像を手に入れるためにGoogle画像検索を見てみましょう。<br>

<img src="/images/uploads/sagemaker0.png" style="width:100%;" />

たくさんの可愛いデグーマウスたちが表示されました。<br>
これらの画像をひとつひとつ保存してもいいのですが、それは大変なので今回はツールを使おうと思います。<br>
今回使用するのは「google-images-download」というコマンドラインツールです。<br>
このツールはPythonで作られており、Pythonのパッケージ管理ツールである「pip」を使ってインストールすることができます。<br>

```
pip install google_images_download

```

インストールが完了したら、以下のコマンドでデグーマウスの画像を取得することができます。<br>

```
googleimagesdownload --keywords "デグーマウス"
```

これを実行すると...<br>
<img src="/images/uploads/sagemaker6.png" style="width:100%;" />
<img src="/images/uploads/sagemaker1.png" style="width:100%;" />
やりました！<br>

このコマンドで取得できた画像は98枚ですが、これではちょっと少ないので水増しします。<br>
以下のPythonコード(<a href="https://dev.classmethod.jp/cloud/aws/sagemaker-umaibo-object-detection/">お借りしました</a>)を使って、１つの画像を回転させた画像を複数生成して水増ししました。<br>

```
import os
from PIL import Image, ImageFilter
 
def main():
    data_dir_path = './out/'
    data_dir_path_in = './in/'
    file_list = os.listdir('./in/')
 
    count = 1
    for file_name in file_list:
        root, ext = os.path.splitext(file_name)
        if ext == '.png' or '.jpeg' or '.jpg':
            img = Image.open(data_dir_path_in + '/' + file_name) 
            tmp = img.transpose(Image.FLIP_LEFT_RIGHT)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.transpose(Image.FLIP_TOP_BOTTOM)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.transpose(Image.ROTATE_90)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.transpose(Image.ROTATE_180)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.transpose(Image.ROTATE_270)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.rotate(15)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.rotate(75)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.rotate(135)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1         
            tmp = img.rotate(195)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
            tmp = img.rotate(255)
            tmp.save(data_dir_path + '/' + '{0:04d}'.format(count) +'.jpg')
            count+=1
 
if __name__ == '__main__':
    main()
```
こんな感じで生成されます！560枚に増やせました<br>
<img src="/images/uploads/sagemaker7.png" style="width:100%;" />

次に<a href="https://github.com/Microsoft/VoTT#installation">VoTT（Visual Object Tagging Tool）</a>というツールを使って、この画像ひとつひとつのどこにデグーマウスが写っているのかをタグ付けしていきます。<br>
本来なら場所だけでなく分類付け(白っぽいデグーマウスと茶色のデグーマウスを区別するとか)も可能なのですが、今回は分類はデグーマウスひとつだけで、あくまで位置を検出するだけとします。<br>

こんな画面でタグ付けします。<br>
<img src="/images/uploads/sagemaker4.png" style="width:100%;" /><br>
私はこの矩形選択で位置をタグ付けするという作業を手作業で画像560枚に対して行いました(1時間かかりました)。<br>
もっと効率のいい方法がありそうな気もするので、ご存知の方がおりましたら、教えてください...<br>

そうしてすべての画像のタグ付けが終わると「out.json」というファイルが出力されます。<br>
これが画像のどこにデグーマウスが写っているのか、タグ付けした結果になります。<br>
ただこのままではAmazon SageMakerに読み込ませることはできないみたいですので、以下のPythonコードを使って変換します。<br>
(<a href="https://dev.classmethod.jp/cloud/aws/sagemaker-umaibo-object-detection/">こちらのサイト</a>のものをお借りしましたが、現時点のVoTTのout.jsonを読ませるとエラーが発生したので一部修正しています)<br>

```
import json
 
file_name = './out.json'
class_list = {'Degu':0}
 
with open(file_name) as f:
    js = json.load(f)
 
    for k, v in js['frames'].items():
 
        k = int(k.replace('.jpg',''))
        if len(v) == 0:
            continue
        line = {}
        line['file'] = '{0:04d}'.format(k+1) + '.jpg'
        line['image_size'] = [{
            'width':int(v[0]['width']),
            'height':int(v[0]['height']),
            'depth':3
        }]
 
        line['annotations'] = []
 
        for annotation in v:
 
            line['annotations'].append(
                {
                    'class_id':class_list[annotation['tags'][0]],
                    'top':int(annotation['y1']),
                    'left':int(annotation['x1']),
                    'width':int(annotation['x2'])-int(annotation['x1']),
                    'height':int(annotation['y2']-int(annotation['y1']))
                }
            )
 
        line['categories'] = []
         
        for name, class_id in class_list.items():
 
            line['categories'].append(
                {
                    'class_id':class_id,
                    'name':name
                }
            )
 
        f = open('./json/'+'{0:04d}'.format(k+1) + '.json', 'w')
        json.dump(line, f)
```

完了するとこのようなjsonファイルが出力されます。<br>
<img src="/images/uploads/sagemaker8.png" style="width:100%;" />

これで学習用データの用意ができました！<br>

## おわりに

今回はAmazon SageMakerで使用する、学習用データの用意を行いました。<br>
次回以降の記事で実際に学習をさせてみようと思います。<br>
本当にタグ付けは途中で発狂しそうな作業だったので、誰かもっといい方法をご存知なら、<a href="https://twitter.com/RinGoku98/">私のTwitter</a>で教えてください...<br>

それでは今回はこの辺で。ここまで読んでいただき、ありがとうございました！


