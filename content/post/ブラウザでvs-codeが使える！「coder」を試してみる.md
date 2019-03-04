---
title: ブラウザでVS Codeが使える！「Coder」を試してみる
description: VS Codeが使えるクラウドIDE「Coder」を試してみます
date: 2019-03-04T11:11:49.097Z
image: /images/uploads/coder9.png
categories:
  - 使ってみるシリーズ
tags:
  - 使ってみるシリーズ
  - Coder
comments: true
---
## はじめに
私は普段の業務でもプライベートの開発でも<a href="https://code.visualstudio.com/">Visual Studio Code(VS Code)</a>を使っています。<br>
朝の時間が一番集中できるので、朝早起きして開発をしたりもするのですが、１ヶ月ほど前、出社が遅いことを上司に指摘されたため、しぶしぶ早めに朝出社することにしたのですが、中途半端に作業に切りをつけるのが嫌で、いっそのことめちゃくちゃ早く出社して開発しようと思いました。<br>

そこで問題となったのが自宅と同等の開発環境を職場のPCにも用意する必要があるということなのですが、構築もめんどくさいですし、むやみに色々入れるとそれはそれで何か言われそうなので、どうしたものかなーって思っていました。

そこで白羽の矢を立ったのがクラウドIDEで、その時は<a href="https://codeanywhere.com/">Codeanywhere</a>というクラウドIDEで、１週間ほど使っていたのですが、やはりVS Codeとの違いが気になり、そのうち使わなくなってしまいました。<br>
その後は朝の時間は読書にあてていて、それはそれで捗ったのですが、Coopet(私が開発しているSNS)の開発も考えると、朝の時間をコーディングにあてたいと思うようになりました。<br>
そこで少し調べてみたところ、<a href="https://coder.com/">Coder</a>を見つけたという流れです。<br>

今日は使ってみるシリーズ第4弾ということで(Elmは勉強中です)、クラウドIDE「Coder」を使ってみようと思います。<br>

## クラウドIDEとは

そもそもクラウドIDEとは何かというところから、お話したいと思います。<br>
クラウドIDEはその名の通り、「<span class="strong-str">クラウド上に構築されたブラウザからアクセスできる開発環境</span>」を指します。<br>
普段皆さんが開発する時はもちろん皆さん自身のパソコンの中にパッケージ管理ツールを入れたり、エディタを入れたり、データベースサーバーを立てたりして、開発環境を構築すると思います。<br>
クラウドIDEではそういった環境構築を、皆さんのパソコンの中でするのではなく、クラウド上で行い、そして皆さんのパソコンからブラウザを通して、クラウド上の開発環境にアクセスすることになります。<br>

クラウドIDEには以下のようなメリットがあります。<br>

・開発環境のプリセットが用意されており、それを選ぶだけで容易に開発環境を構築できる<br>

・ソースのビルドやサーバーの起動は自分のパソコンでなく、クラウド上で行われるため、自分のパソコンのリソースの消費を抑えて開発が可能。<br>

・開発端末が変わっても環境構築をやり直す必要がない

特に1点目は初学者の1つ目の壁である環境構築を格段にやりやすくしてくれる点なので、クラウドIDEは初学者にもおすすめのサービスとなっています。<br>

## Coderとは

<a href="https://coder.com/">Coder</a>は端的に言えば「(ほぼ)VS Codeが使えるクラウドIDEサービス」です。現在はアルファ版として公開されています。<br>
実はVS CodeライクなクラウドIDEは他にもあるのですが、Coderが優れているのは、<span class="strong-str">大半のVS Code拡張機能が使用できる</span>点にあります。<br>
<img src="/images/uploads/coder.png" style="width: 100%;"/>

言語サポートはこんな感じになっています。<br>
<img src="/images/uploads/coder2.png" style="width: 100%;"/>

よく目にするようなものは揃っている印象ですね。<br>
とりあえず私の用途では困らなさそうです。<br>
プロジェクトはDockerコンテナ内に作成されるので、ある程度融通も効きそうですしね。<br>
バージョンもボタン一つで切り替えられるとのこと<br>

## 登録してみる

それでは早速使ってみましょう。<br>

<a href="https://coder.com/">公式ページ</a>にアクセスします。<br>

<img src="/images/uploads/Coder3.png" style="width: 100%;"/>

サインアップにはGithub、Google、Emailが選べるみたいですね。<br>
今回はGithubでサインアップしようと思います。<br>

<img src="/images/uploads/Coder4.png" style="width: 100%;"/>

ログインを求められるので、ユーザー情報を入力してログインします。<br>

<img src="/images/uploads/Coder5.png" style="width: 100%;"/>

するとCoderとGitHub連携の認証を求められるので「Authorize codercom」をクリックして認証します。<br>

<img src="/images/uploads/Coder6.png" style="width: 100%;"/>

認証が完了するとCoder側に戻ってきて、ユーザー名と電話番号の入力を求められます。<br>
SMS認証が必要なのは予想外でした。<br>
複数アカウント防止用でしょうか。<br>
入力して「Complete Sign Up」をクリックします。<br>
<img src="/images/uploads/Coder7.png" style="width: 100%;"/>

これにて登録完了です！<br>

## 使ってみる

<img src="/images/uploads/Coder7.png" style="width: 100%;"/>

まずはプロジェクトを作成してみましょう。<br>
左上にある「+ Create Project」をクリックします。<br>
するとプロジェクト名の入力を求められるので、入力します。<br>
私は「Coopet」と入力しました。<br>
<img src="/images/uploads/Coder8.png" style="width: 100%;"/>

するとプロジェクト行が追加されるので、「Open in VSCode」をクリックします。<br>

すると...<br>
<img src="/images/uploads/Coder9.png" style="width: 100%;"/>

おおー！<br>
これはまさにVS Code!<br>
ここまで再現されているとは...<br>

「Ctrl+@」でターミナルもちゃんと開きます。<br>

<img src="/images/uploads/Coder10.png" style="width: 100%;"/>

Emmetも...

<img src="/images/uploads/Coder11.png" style="width: 100%;"/>

<img src="/images/uploads/Coder12.png" style="width: 100%;"/>
使えますね！

