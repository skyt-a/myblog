---
title: Elmを使ってみる（1）
description: フロントエンド関数型言語Elmを使ってみます(今回は概要～導入まで)
date: 2019-03-02T00:33:37.621Z
image: /images/uploads/elm.png
categories:
  - 使ってみるシリーズ
  - 技術紹介
  - Elm
tags:
  - 使ってみるシリーズ
  - 技術紹介
  - Elm
comments: true
---
## はじめに
自分が見聞きして使ってみたいなと思った技術を一旦触りだけやってみることで、色々な技術を使う心理的なハードルを下げたいなと思っています。<br>
（例えばプログラミング言語ならHello,World書いて～みたいな）<br>
また新しいことをするのは、視野も広がるし、いい気分転換にもなるということで定期的にやっていけたらなーと思います。<br>
というわけで今回はこの「使ってみるシリーズ」第3弾として、Elmというプログラミング言語を使ってみようと思います。<br>
今回の記事は技術解説記事というよりは勉強の記録的な意味合いが強いです。(特に後半）<br>
間違った情報なども含まれている可能性もありますので、ご指摘等ございましたら<a href="http://twitter.com/RinGoku98/">私のTwitter</a>に宜しくお願い致します。
## Elmとは

<img src="/images/uploads/elm.png" />

Elmはフロントエンド開発で使用されるプログラミング言語です<br>
以下のような特徴があります。<br>

### コンパイルするとHTML・CSS・JavaScriptに変換される

フロントエンド開発言語といえば、HTML・CSS・JavaScriptですよね。<br>
実際現状ブラウザが読み込んで処理できるのは、これらの言語だけです。<br>
しかしElmを使うとフロントエンド開発ができるというのはどういうことでしょうか。<br>
実はElmはコンパイルすると<span class="strong-str">HTML・CSS・JavaScriptに変換される</span>のです。<br>

### JavaScriptの拡張...というわけではない

先程、ElmはコンパイルするとHTML・CSS・JavaScriptに変換されると、説明しました。<br>
ここから連想されるのはコンパイルするとJavaScriptに変換されるという特徴を持つAltJSに似ているというところではないでしょうか。<br>
しかし、ElmはAltJSとは似て非なる特徴を備えています。<br>
AltJSはあくまでJavaScriptをベースに拡張的に機能追加したものです(例えばTypeScriptなら静的型の概念を付与するとか)。
一方でElmでは<span class="strong-str">JavaScriptやCSSの機能を直接呼び出したりすることはできません。</span><br>
あくまでElmが提供しているやり方でJavaScriptやCSSを操作するという開発方法になります。<br>

### 不変性
不変性とはどういうことでしょうか。<br>
例えばElmでは以下のコードはエラーになります。<br>
```
a = 2
a = 3
```
再代入は許さないということですね。<br>
JavaScriptではES6から「const」が導入され、同じようなことができると思うかもしれませんが、constはあくまで不変性を意識した書き方ができるだけに過ぎません。letを使えば、再代入も可能ですし、そもそもvarもまだ使えますしね。<br>
一方でElmでは<span class="strong-str">再代入可能な変数を宣言することはそもそもできません。</span>これはなんだか息苦しいようにも感じますが、一度宣言した変数の中身は変更されないことが保証されているので、関数の副作用による予期しないバグを完全に防ぐことができます。<br>

プログラマーができることを制限することで、シンプルでバグりにくいプログラミングを可能にすることがElmの目指すひとつのテーマであると感じられます。<br>

### 静的型
Elmは強力な静的型付け言語です。<br>
静的かつ強力な型検査により「<span class="strong-str">事実上一切の実行時例外が起こらない</span>」ということを謳っている言語です。<br>
これによってコンパイル時でのエラーの検出やユニットテストの軽量化など多くのメリットを享受することができます。

### Virtual DOM
<a href="https://elated-blackwell-51e103.netlify.com/admin/#/collections/post/entries/3%E5%A4%A7%E3%83%95%E3%83%AD%E3%83%B3%E3%83%88%E3%82%A8%E3%83%B3%E3%83%89%E3%83%95%E3%83%AC%E3%83%BC%E3%83%A0%E3%83%AF%E3%83%BC%E3%82%AF%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6">前回の記事</a>のReactの項で解説したVirtual DOMも採用されています。<br>
elm/htmlというライブラリによってElmの内部でHTMLやCSSを扱うことができるのですが、その際の更新においてVirtual DOMが使われています。

## 導入
早速Elmを導入してみましょう！<br>
<a href="https://guide.elm-lang.jp/">公式ガイド</a>を参考に進めていきます(日本語あるのが最高)。<br>
今回はWindowsに環境を構築するので上記の公式ガイドにのっている<a href="https://github.com/elm/compiler/releases/download/0.19.0/installer-for-windows.exe" target="_blank">こちらのリンク</a>からWindows用のインストーラーをダウンロードします。<nr>
インストールは特別なことをする必要はなく、基本的に次へを選んでいけば完了します。<br>

次にエディタのElm拡張機能を導入します。<br>
今回私はVisual Studio Codeを使用しますので、<a href="https://github.com/Krzysztof-Cieslak/vscode-elm">このプラグイン</a>を使用します(VS Codeの拡張機能の検索で「Elm」と検索すれば出てきます)。

ここでとりあえず公式のチュートリアルプロジェクトを取得してみます。<br>
以下のコマンドでGitHubからプロジェクトをクローンします。<br>

```
git clone https://github.com/evancz/elm-architecture-tutorial.git
```

またelm reactorというコマンドを使うと、Elmビルド用サーバーを立ち上げて、動作を確認することができます。<br>
@angular/cliでいうng serveみたいなものですね。<br>

これで導入は以上となります。<br>

## Elmのソースコードを読んでみる

クローンしてきたチュートリアル内のソースコードを1つ読んでみます。<br>
まだElmの文法とか何も知らないですけど、現在の知識で予想できるところは予想します。<br>
で、読んで抱いた感想を記録しておきます。ちゃんとElmを理解した後に見返したいと思います。<br>
ただ受動的に学ぶのではなく、あらかじめ疑問点を持って臨むことで記憶の定着につながればなーと(実験的な試みです。効果的なやり方かどうかはわかりません笑)。

#### examples/01-button.elm
```
import Browser
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)


main =
  Browser.sandbox { init = init, update = update, view = view }

-- MODEL

type alias Model = Int

init : Model
init =
  0


-- UPDATE

type Msg = Increment | Decrement

update : Msg -> Model -> Model
update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1


-- VIEW

view : Model -> Html Msg
view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (String.fromInt model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

上のソースで実装された画面はこちら<br>
<img src="/images/uploads/elm1.png">

##### 以下まだ文法を何も知らない状態での感想<br>(後で見返したらトンチンカンなこと言ってるんだろうなー)
・type宣言してるのってその名の通り、型だよな・・・？<br>
・データとデータ操作とViewが完全に分離してていい感じ<br>
・ViewもHTMLを直書きするんじゃなくて、宣言的に書くんだ。<br>
　→ 入れ子構造とか結構ごちゃごちゃしそうだけど大丈夫なのかな<br>
・Msg型はIncrement関数もしくはDecrement関数？<br>
  → 多分これ全部関数なんだよね？MsgっていうクラスにIncrementとDecrementっていう2つのメソッドを定義しているみたいな感じになってるな<br>
・Viewの部分、Model -> Html MsgでMsgとHTMLが紐付けられているのかな<br>
  → Angularでいうテンプレートとコンポーネントクラスの紐づけみたいなものかな？<br>
・Browser.sandbox { init = init, update = update, view = view }ってなんだ？sandbox環境を作るためのものってことはわかるけど、何を設定してるかピンとこない<br>
・update : Msg -> Model -> Model
→ なにこれ？

## おわりに
今回はElmがどんな言語なのかというところとElmの導入について勉強しました。<br>
本当は一つの記事にまとめたかったのですが、1つのプログラミング言語を学ぶというのは当然奥が深く、何回かに分けて記事にしようと思いました。<br>
現時点ではElmの文法などまだ何も知らない状態ですが、ここから合間を見て勉強し、何か試しに作ってみてそれを記事にできたらなと思います。<br>

それでは今回はこのへんで。ここまで読んでいただきありがとうございました！<br>
感想やご意見・質問等ございましたら、<a href="https://twitter.com/RinGoku98">私のTwitter</a>までお気軽にどうぞ。
