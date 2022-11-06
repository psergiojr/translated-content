---
title: 基本的な CSS の理解
slug: Learn/CSS/Building_blocks/Fundamental_CSS_comprehension
original_slug: Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension
---

{{LearnSidebar}}{{PreviousMenu("Learn/CSS/Introduction_to_CSS/Debugging_CSS", "Learn/CSS/Introduction_to_CSS")}}

このモジュールで多くをカバーしてきました、最後まで来て気分が良いでしょう！ 次に進む前の最後のステップは、モジュールの評価を試みることです。これには、最終的なデザイン (名刺/ゲーマーカード/ソーシャルメディアプロファイル) を作成するために完了しなければならないいくつかの関連演習が含まれます。

| 前提条件: | この評価を実施する前に、すでにこのモジュールのすべての記事を通して作業しているはずです。 |
| --------- | ---------------------------------------------------------------------------------------- |
| 目的:     | 基本的な CSS 理論、構文、およびメカニズムの理解をテストする。                            |

## 出発点

この評価を開始するには、次のことが必要です。

- [練習用の HTML ファイル](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/fundamental-css-comprehension/index.html)とそれに[関連付けられた画像ファイル](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/fundamental-css-comprehension/chris.jpg)を探して、ローカルコンピュータの新しいディレクトリーに保存します。自身の画像ファイルを使い、自身の名前を記入したいのなら、それも大歓迎です — ちょうど画像が正方形であることを確認してください。
- [CSS リソースのテキストファイル](https://github.com/mdn/learning-area/blob/master/css/introduction-to-css/fundamental-css-comprehension/style-resources.txt)を入手してください。これには、評価の一部に答えるために検討して組み合わせる必要がある一連の未加工のセレクタとルールセットが含まれています。

> **メモ:** 代わりとして、[JSBin](https://jsbin.com/) や [Thimble](https://thimble.mozilla.org/) のようなサイトを使って評価することもできます。HTML を貼り付けて CSS をこれらのオンラインエディタのいずれかに入力し、この URL を使用して `<img>` 要素を画像ファイルに向けることができます。使用しているオンラインエディタに別の CSS パネルがない場合は、それをドキュメントの先頭の `<style>` 要素に自由に配置してください。

## プロジェクト概要

生の HTML と画像が提供されているので、これにスタイルを設定するのに必要な CSS を気の利いた小さなオンライン名刺に書く必要があります。これは、おそらくゲーマーカードやソーシャルメディアのプロファイルを兼ねるでしょう。次のセクションではする必要があることについて説明します。

基本設定:

- まず最初に、HTML と画像ファイルと同じディレクトリーに新しいファイルを作成してください。それを `style.css` のような本当に想像力豊かなものと呼びます。
- `<link>` 要素を介して CSS を HTML ファイルにリンクします。
- CSS リソースファイルの最初の 2 つのルールセットは無料です。幸運を祈って楽しんだら、コピーして新しい CSS ファイルの先頭に貼り付けます。これらをテストとして使用して、CSS が HTML に正しく適用されていることを確認してください。
- 2 つの規則の上に、CSS コメントをその中にテキストを追加して、これがページ全体の一般的なスタイルのセットであることを示します。「一般的なページスタイル」でも構いません。また、CSS ファイルの下部にさらに 3 つのコメントを追加して、カードコンテナの設定に固有のスタイル、ヘッダーとフッターに固有のスタイル、およびメインの名刺の内容に固有のスタイルを示します。 今後、スタイルシートに追加された後続のスタイルは適切な場所に編成される必要があります。

CSS リソースファイルで提供されているセレクタとルールセットに注意してください。

- 次に、4 つのセレクタを見て、それぞれの詳細度を計算してください。CSS の上部にあるコメントなど、後で見つけられる場所にこれらを書き留めてください。
- では、正しいセレクタを正しいルールセットに配置しましょう。CSS リソースには、4 組のセレクタとルールセットがあります。今すぐこれを行い、それらを CSS ファイルに追加してください。必要があるのは：

  - メインカードコンテナの幅と高さ、背景色、ボーダー、ボーダー半径 (角丸) などを固定します。
  - ヘッダーに、濃い色から明るい色への背景グラデーションと、メインカードコンテナに設定された丸みのある角に合う丸みのある角を付けます。
  - フッターには、明るいものから暗いものまでの背景のグラデーションと、メインカードコンテナに設定された丸みのある角に合う丸みのある角を付けます。
  - 画像をメインの名刺の内容の右側に貼り付け、最大の高さを 100％にします (どの高さになるかにかかわらず、親コンテナと同じ高さを維持するために拡大/縮小することを保証する巧妙なトリック) 。

- 注意してください。提供されているルールセットには 2 つのエラーがあります。知っている任意のテクニックを使用して、これらを見つけ出して進む前に修正してください。

書く必要がある新しいルールセット：

- カードヘッダーとカードフッターの両方を対象としたルールセットを作成し、計算された合計の高さは 50 ピクセル (コンテンツの高さ 30 ピクセル、パディングは全側面で 10 ピクセル) を両方に指定します。
- ブラウザーが `<h2>` 要素と `<p>` 要素に適用するデフォルトのマージンは、私たちのデザインを妨げるので、これらすべての要素をターゲットにしてそれらのマージンを 0 に設定するルールを書きましょう。
- 画像がメインの名刺の内容 (`<article>` 要素) からはみ出ないようにするには、特定の高さを指定する必要があります。`<article>` の高さを 120 px に設定します。ただし、`em`s で表します。また、背景色を半透明の黒にすると、やや濃い色になり、背景の赤い色も少し明るくなります。
- `<h2>` に 20 px の有効フォントサイズ (ただし `em`s で表示) とそれをヘッダーのコンテンツボックスの中央に配置するための適切な行の高さを指定するルールセットを作成します。やる前にコンテンツボックスの高さは 30 px でなければならないことを思い出してください — これで行の高さを計算するのに必要なすべての数が揃います。
- フッターの内側の `<p>` を 15 px の有効フォントサイズ (ただし `em`s で表示) とフッターのコンテンツボックスの中央に配置するための適切な行の高さを指定するルールセットを作成します。やる前にコンテンツボックスの高さは 30 px でなければならないことを思い出してください — これで行の高さを計算するのに必要なすべての数が揃います。
- 最後のちょっとしたタッチとして、`<article>` の内側の段落に適切なパディング値を指定して、その左端が `<h2>` とフッターの段落に揃うようにし、読みやすくなるように色をかなり明るい色に設定します。

> **メモ:** 2 番目のルールセットは `<html>` 要素に `font-size: 10px;` を設定することに注意してください。これは `<html>` のすべての子孫について、em はデフォルトの 16 px ではなく 10 px になることを意味します (これはもちろん、階層内で問題の子孫と `<html>` の間に別の `font-size` が設定されている先祖がいない場合に限ります。これは必要な値に影響を与える可能性がありますが、この単純な例では問題にはなりません)。

その他の考慮事項

- 読みやすくするために CSS を作成すると、各行に個別の宣言を使用してボーナスマークが付けられます。
- 他のコンテンツを大量に含む名刺をページに配置する場合にこれらのルールが他の要素のスタイル設定を妨げないように、すべてのルールのセレクタチェーンの先頭に `.card` を含める必要があります。

## ヒントとコツ

- CSS を HTML に適用する以外は、HTML を編集する必要はありません。
- 特定のピクセル長を表現するために必要な `em` 値を計算する際には、ルート (`<html>`) 要素の基本フォントサイズと、必要な値を得るために乗算する必要があるサイズについて考えてください。少なくともこのような単純なケースでは、em の価値があるでしょう。

## 例

次のスクリーンショットは、完成したデザインの外観の例を示しています。

![A view of the finished business card, show a reader header and footer, and a darker center panel containing the main details and image.](business-card.png)

## 評価

組織的な研修の一部としてこの評価に従っているなら、あなたは採点のためにあなたの教師/メンターに作業結果を提出できるはずです。もし自己学習しているのであれば、[この練習問題についてのディスカッションスレッド](https://discourse.mozilla.org/t/fundamental-css-comprehension-assessment/24682)、または [Mozilla IRC](https://wiki.mozilla.org/IRC) の [#mdn](irc://irc.mozilla.org/mdn) IRC チャンネルで尋ねることで、非常に簡単に採点ガイドを入手できます。最初にエクササイズをしてみてください — 不正をすることによって得られるものは何もありません！

{{PreviousMenu("Learn/CSS/Introduction_to_CSS/Debugging_CSS", "Learn/CSS/Introduction_to_CSS")}}

## このモジュール

- [CSS の仕組み](/ja/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works)
- [CSS の構文](/ja/docs/Learn/CSS/Introduction_to_CSS/Syntax)
- [CSS セレクタ](/ja/docs/Learn/CSS/Introduction_to_CSS/Selectors)
- [単純セレクタ](/ja/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors)
- [属性セレクタ](/ja/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors)
- [擬似クラスと擬似要素](/ja/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements)
- [コンビネーターとセレクタリスト](/ja/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors)
- [CSS の値と単位](/ja/docs/Learn/CSS/Introduction_to_CSS/Values_and_units)
- [カスケードと継承](/ja/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)
- [ボックスモデル](/ja/docs/Learn/CSS/Introduction_to_CSS/Box_model)
- [CSS のデバッグ](/ja/docs/Learn/CSS/Introduction_to_CSS/Debugging_CSS)
- [基本的な CSS の理解](/ja/docs/Learn/CSS/Introduction_to_CSS/Fundamental_CSS_comprehension)