---
title: フレックスボックス
slug: Learn/CSS/CSS_layout/Flexbox
l10n:
  sourceCommit: 1a2315572d8ae37dd1aeb387922f60cb0c3fe92d
---

{{LearnSidebar}}{{PreviousMenuNext("Learn/CSS/CSS_layout/Normal_Flow", "Learn/CSS/CSS_layout/Grids", "Learn/CSS/CSS_layout")}}

[フレックスボックス](/ja/docs/Web/CSS/CSS_Flexible_Box_Layout) (Flexbox) は、アイテムを行または列に並べるための 1 次元のレイアウト方法です。アイテムがたわんで（伸びて）追加の空間を埋めたり、縮んで小さい空間にに収まったりします。この記事では、すべての基本事項について説明します。

<table>
  <tbody>
    <tr>
      <th scope="row">前提知識:</th>
      <td>
        HTML の基本（<a href="/ja/docs/Learn/HTML/Introduction_to_HTML"
          >HTML 入門</a
        >で学んでください）、および CSS の動作の仕組みの考え方（<a href="/ja/docs/Learn/CSS/First_steps">CSS 入門</a>で学んでください）。
      </td>
    </tr>
    <tr>
      <th scope="row">目標:</th>
      <td>
        フレックスボックスレイアウトシステムを使用して、ウェブのレイアウトを作成する方法を習得する。
      </td>
    </tr>
  </tbody>
</table>

## なぜフレックスボックスなのか

長い間、CSS レイアウトを作成するために利用可能な唯一の信頼できるブラウザー間で互換性のあるツールは[浮動要素](/ja/docs/Learn/CSS/CSS_layout/Floats)と[位置指定](/ja/docs/Learn/CSS/CSS_layout/Positioning)などでした。 これらは問題なく機能しますが、いくつかの点ではかなり限定的でイライラするものです。

次のような単純なレイアウト要件は、このようなツールを使用しても、便利で柔軟な方法で実現するのが困難または不可能です。

- コンテンツのブロックをその親内で垂直方向に中央揃えにする。
- コンテナーのすべての子が、使用可能な幅や高さに関係なく、使用可能な幅や高さについて等しい量を占めるようにする。
- 複数列レイアウトのそれぞれの列に含まれているコンテンツの量が異なっても、高さが同じになるようにする。

以降のセクションで見るように、フレックスボックスは多くのレイアウト作業をずっと簡単にします。 さあ始めましょう！

## 簡単な例の紹介

この記事では、フレックスボックスがどのように機能するのかを理解するのに役立つ一連の演習を進めていくようにします。 まず始めに、github リポジトリーから最初のスターターファイル [flexbox0.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/flexbox0.html) のローカルコピーを作成し、最新のブラウザー（Firefox や Chrome など）にロードして、コードエディターでコードを確認してください。 ここでも[ライブで見る](https://mdn.github.io/learning-area/css/css-layout/flexbox/flexbox0.html)ことができます。

![フレックスボックスチュートリアルのスタート地点を示す画像](bih741v.png)

内部に最上位の見出しを持つ {{htmlelement("header")}} 要素と、 {{htmlelement("section")}} 要素があり、その中に 3 つの {{htmlelement("article")}} を含むます。 これらを使用して、かなり標準的な 3 列のレイアウトを作成しましょう。

## 柔軟な箱としてレイアウトする要素を指定

まず最初に、どの要素を柔軟な箱 (flexible box) としてレイアウトするかを選択する必要があります。 これを行うために、影響を与えたい要素の親要素に {{cssxref("display")}} の特別な値を設定します。 この場合、 {{htmlelement("article")}} 要素をレイアウトしたいので、これを {{htmlelement("section")}} に設定します。

```css
section {
  display: flex;
}
```

これによって、 \<section> 要素が**フレックスコンテナー**となり、その子は**フレックスアイテム**になります。その結果、以下のような感じになるでしょう。

![1行目に1列、2行目に3列のレイアウトを含む2列のコンテナで、ウェブページが内容に応じて異なるレイアウトに分けられることを示すもの](flexbox-example2.png)

それで、このたった一つの宣言が必要なものすべてを与えてくれます。信じられないでしょう？ 同じ幅の列を持つ複数列のレイアウトがあり、列の高さはすべて同じです。 これは、フレックスアイテム（フレックスコンテナーの子）に与えられる既定値が、このような一般的な問題を解決するために設定されているためです。 それらについての詳細は後で。

はっきりさせるために、ここで何が起こっているのかをもう一度説明しましょう。{{cssxref("display")}} の値として `flex` を指定された要素は、ページの他の部分とやり取りする方法についてはブロックレベル要素のように動作しますが、その子要素はフレックスアイテムとしてレイアウトされます。次の節では、この意味をより詳しく説明します。なお、ある要素の子要素をフレックスアイテムとしてレイアウトしたいが、その要素はインライン要素のように取り扱いたい場合は、 `display` 値として `inline-flex` を使用することができます。

## フレックスモデル

要素が柔軟な箱として配置されるとき、それらは次のように 2 つの軸に沿って配置されます。

![左から右に記述された 3 つのフレックスアイテムが、フレックスコンテナーの中に横に並んでいる。主軸（フレックスアイテムが配置される方向のフレックスコンテナーの軸）は水平である。この軸の両端は主始点と主終点と呼ばれ、それぞれ左側と右側にある。交差軸は垂直で、主軸に直交している。交差始点と交差終点はそれぞれ上部と下部にある。主軸に沿ったフレックスアイテムの長さ、この場合は幅を主サイズと呼び、交差軸に沿ったフレックスアイテムの長さ、この場合は高さを交差サイズと呼ぶ。](flex_terms.png)

- 主軸 (**main axis**) は、フレックスアイテムが配置されている方向に走る軸です（例えば、ページを横切る行、またはページ下の列として）。 この軸の始点と終点は、主始点 (**main start**) と主終点 (**main end**) と呼ばれます。
- 交差軸 (**cross axis**) は、フレックスアイテムが配置されている方向に対して垂直に走る軸です。 この軸の始点と終点は、交差始点 (**cross start**) と交差終点 (**cross end**) と呼ばれます。
- `display: flex` が設定されている親要素（この例では {{htmlelement("section")}}）は、フレックスコンテナー (**flex container**) と呼ばれます。
- フレックスコンテナー内の柔軟な箱としてレイアウトされているアイテムは、フレックスアイテム (**flex item**) と呼ばれます（この例では {{htmlelement("article")}} 要素）。

この後の節を読むときに、この用語を覚えておいてください。使用する用語に迷ったときは、常にこの用語を参照してください。

## 列か行か

フレックスボックスは {{cssxref("flex-direction")}} というプロパティを提供します。 これは主軸が走る方向（フレックスボックスの子がどの方向にレイアウトされるか）を指定します。既定では `row` に設定されていて、ブラウザーの既定の言語が動作する方向（英語のブラウザーの場合は左から右に）にそれらが横一列にレイアウトされます。

次の宣言を {{htmlelement("section")}} のルールに追加してみてください。

```css
flex-direction: column;
```

これにより、 CSS を追加する前と同じように、アイテムが縦一列のレイアウトに戻されます。 先に進む前に、この宣言を例から削除してください。

> **メモ:** `row-reverse` と `column-reverse` の値を使用して、フレックスアイテムを逆方向にレイアウトすることもできます。 これらの値も試してみてください。

## 折り返し

レイアウトの幅や高さが決まっているときに発生する問題の 1 つは、最終的にはフレックスボックスの子がコンテナーをはみ出してレイアウトが壊れることです。 [flexbox-wrap0.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/flexbox-wrap0.html) の例を見て、それを[ライブで見て](https://mdn.github.io/learning-area/css/css-layout/flexbox/flexbox-wrap0.html)みてください（この例に沿って進めたい場合は、このファイルのローカルコピーを取ってください）。

![サンプルのフレックスボックスの例では、すべてのフレックスアイテムがフレックスコンテナーの単一の行にレイアウトされています。8 つ目のフレックスアイテムはブラウザーウィンドウからはみ出し、ページには水平方向と垂直方向のスクロールバーが表示されますが、これは前の 7 つのフレックスアイテムがビューポート内で使用できる空間を占めているため、ウィンドウ幅に収まらないためです。既定値では、ブラウザーは、 flex-direction を row に設定した場合はすべてのフレックスアイテムを単一の行に、 column に設定した場合は単一の列に配置しようとします。](flexbox-example3.png)

ここでは、子要素が実際にコンテナーからはみ出してることがわかります。これを修正させる一つの方法は、 {{htmlelement("section")}} ルールに以下のような宣言を追加することです。

```css
flex-wrap: wrap;
```

また、 {{htmlelement("article")}} のルールに次の宣言を追加してください。

```css
flex: 200px;
```

試してみてください。 これが含まれていると次のようにレイアウトがはるかに良く見えることがわかります。

![フレックスアイテムは、フレックスコンテナー内に複数列でレイアウトされます。フレックスコンテナーでは flex-wrap プロパティが 'wrap' に設定されており、前の行のフレックスアイテムがフレックスコンテナーからはみ出した場合、新しい行にフレックスアイテムが表示されます。各フレックスアイテムには 200 ピクセルの幅が指定されました。すべての項目は同じ高さになるように伸張され、最も多くの内容を含むフレックス項目の高さと同じになります。](flexbox-example4.png)

現在、複数の行があります — 多くのフレックスボックスの子が各行に納められているので、オーバーフローは次のラインに移動します。 `article` に設定した `flex: 200px` の宣言は、それぞれが少なくとも 200px 幅になることを意味します。 このプロパティについては後で詳しく説明します。 また、最後の行の最後の数個の子がそれぞれ幅広になっているので、依然として行全体がいっぱいになっていることに気付くかもしれません。

しかし、ここでできることは他にもあります。 まず最初に、 {{cssxref("flex-direction")}} プロパティの値を `row-reverse` に変更してみてください。 これで、まだ複数行のレイアウトがあることがわかりますが、ブラウザーウィンドウの反対側の隅から開始して逆方向に流れます。

## flex-flow 一括指定

ここで、 {{cssxref("flex-direction")}} と {{cssxref("flex-wrap")}} には {{cssxref("flex-flow")}} という一括指定が存在することに注目する価値があります。 例えば、次のように置き換えることができます。

```css
flex-direction: row;
flex-wrap: wrap;
```

を

```css
flex-flow: row wrap;
```

## フレックスアイテムの柔軟なサイズ変更

それでは、最初の例に戻って、フレックスアイテムの占めるスペースの割合を制御する方法を見てみましょう。 ローカルコピーの [flexbox0.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/flexbox0.html) を起動するか、新しい出発点として [flexbox1.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/flexbox1.html) のコピーを入手してください（[ライブで見る](https://mdn.github.io/learning-area/css/css-layout/flexbox/flexbox1.html)）。

まず、CSS の一番下に次のルールを追加します。

```css
article {
  flex: 1;
}
```

これは、各フレックスアイテムが主軸に沿って使用可能なスペースのうちどれだけを占めるかを決定する、無単位の割合値です。 この場合、各 {{htmlelement("article")}} 要素に 1 の値を与えています。 つまり、パディングやマージンなどを設定した後の残りの予備スペースのうちから、すべてが同じ量を占めます。 これは割合であり、各フレックスアイテムに 400000 の値を指定してもまったく同じ効果があることを意味します。

それでは、前のルールの下に次のルールを追加します。

```css
article:nth-of-type(3) {
  flex: 2;
}
```

リフレッシュすると、3 番目の {{htmlelement("article")}} が他の 2 つの幅の 2 倍の幅を占めます。 合計で 4 割合単位が使用可能です。 最初の 2 つのフレックスアイテムはそれぞれ 1 単位ずつ持つため、それぞれ使用可能なスペースの 1/4 を占めます。 3 つ目は 2 単位を持っているので、それは使用可能なスペースの 2/4（または 1/2）を占めます。

`flex` の値内に最小サイズ値を指定することもできます。 既存の `article` のルールを次のように更新してみてください。

```css
article {
  flex: 1 200px;
}

article:nth-of-type(3) {
  flex: 2 200px;
}
```

これは基本的に「各フレックスアイテムには最初に 200px の使用可能なスペースが与えられます。 その後、残りの使用可能なスペースは割合単位に従って共有されます。」と述べています。 リフレッシュしてみると、スペースの共有方法に違いが見られます。

![Sample flexbox の例のフレックスコンテナーには、3 つのフレックスアイテムが保有されています。すべてのフレックスアイテムの最小幅は 200 ピクセルであり、 'flex' を使用して設定されています。最初の 2 つのフレックスアイテムのフレックス値は 1、3 番目のアイテムのフレックス値は 2 です。これにより、フレックスコンテナー内の残りの空間が 4 つの割合の単位に分割されます。最初の 2 つのフレックスアイテムに 1 単位、 3 番目のフレックスアイテムに 2 単位が割り当てられ、 3 番目のフレックスアイテムの幅は、同じ幅の他の 2 つのアイテムよりも広くなります。](flexbox-example1.png)

フレックスボックスの真の価値は、その柔軟性/応答性に見ることができます。ブラウザーウィンドウのサイズを変更したり、別の {{htmlelement("article")}} 要素を追加したりしても、レイアウトは問題なく機能します。

## flex: 一括指定対個別指定

{{cssxref("flex")}} は、最大 3 つの異なる値を指定できる一括指定プロパティです。

- 上記で説明した無単位の割合値。 これは {{cssxref("flex-grow")}} 個別指定プロパティを使用して個別に指定できます。
- {{cssxref("flex-shrink")}} というフレックスアイテムがコンテナーをオーバーフローしているときに有効になる、2 番目の無単位の割合値。 これは、各フレックスアイテムのサイズからオーバーフローする量を取り除き、それらがコンテナーからオーバーフローするのを防ぐために指定します。 これはかなり高度なフレックスボックスの機能で、この記事ではこれ以上説明しません。
- 上記で説明した最小サイズ値。 これは、{{cssxref("flex-basis")}} の個別指定値を使用して個別に指定できます。

本当に必要な場合以外は、個別指定の flex プロパティを使用しないことをお勧めします（例えば、以前に設定したものを上書きする場合など）。 それらは多くの余分なコードが書かれることにつながり、多少混乱するかもしれません。

## 水平方向と垂直方向の配置

フレックスボックスの機能を使用して、主軸または交差軸に沿ってフレックスアイテムを整列させることもできます。 新しい例である [flex-align0.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/flex-align0.html) を見て（[ライブも見る](https://mdn.github.io/learning-area/css/css-layout/flexbox/flex-align0.html)）、これを調べてみましょう。 これは、きちんとした柔軟なボタン/ツールバーに変わります。 現時点では、いくつかのボタンが左上隅に詰まった水平のメニューバーが表示されます。

![](flexbox-example5.png)

まず、この例のローカルコピーを取ります。

それでは、例の CSS の最後に次のものを追加してください。

```css
div {
  display: flex;
  align-items: center;
  justify-content: space-around;
}
```

![Smile, Laugh, Wink, Shrug & Blush というラベルを持つ 5 つのボタンが、フレックスコンテナーの中に一列に並べられています。 align-items プロパティを center に設定することで、フレックスアイテムは交差軸の中心に配置されています。 justify-content プロパティを space-around に設定すると、フレックスアイテムは主軸に沿って等間隔に配置されます。](flexbox_center_space-around.png)

ページをリフレッシュすると、ボタンが横方向と縦方向に中央揃えになっていることがわかります。 これを 2 つの新しいプロパティを介して行いました。

{{cssxref("align-items")}} は、フレックスアイテムが交差軸上のどこに配置されるかを制御します。

- 既定では、この値は `stretch` です。 これは、すべてのフレックスアイテムを交差軸の方向に親を埋めるように引き伸ばします。 親が交差軸方向に固定幅を持っていない場合、すべてのフレックスアイテムは最長のフレックスアイテムと同じ長さになります。 これが最初の例が既定で同じ高さの列を得た方法です。
- 上記のコードで使用した `center` の値により、アイテムは固有の寸法を維持しますが、交差軸の中心に配置されます。 これが、この例のボタンが縦方向に中央揃えされている理由です。
- `flex-start` や `flex-end` のような値を持つこともできます。 これは、すべてのアイテムをそれぞれ交差軸の始点や終点に揃えます。 詳細については {{cssxref("align-items")}} を参照してください。

{{cssxref("align-self")}} プロパティを適用することで、個々のフレックスアイテムの {{cssxref("align-items")}} のふるまいを上書きできます。 例えば、CSS に次のコードを追加してみてください。

```css
button:first-child {
  align-self: flex-end;
}
```

![Smile, Laugh, Wink, Shrug, Blush というラベルを持つ 5 つのボタンが、フレックスコンテナの中に一列に並べられています。最初のものを除くすべてのフレックスアイテムは、 align-items プロパティを center に設定することで、交差軸の中心、つまり垂直方向の中心に配置されています。最初のアイテムは、 align-self プロパティを flex-end に設定して、フレックスコンテナーの底面、交差軸の端に面一に配置されています。フレックスコンテナーのアイテムは、コンテナーの主軸（幅）に沿って等間隔に配置されます。](flexbox_first-child_flex-end.png)

これがどのような影響を与えるのかを見て、終了したらもう一度削除します。

{{cssxref("justify-content")}} は、フレックスアイテムが主軸上のどこに配置されるかを制御します。

- 既定値は `flex-start` です。 これにより、すべてのアイテムが主軸の始点に配置されます。
- それらを終点に配置させるために `flex-end` を使うことができます。
- `center` は `justify-content` のための値でもあり、フレックスアイテムを主軸の中心に配置します。
- 上記で使用した値、`space-around` は便利です。 両端に少しのスペースを残して、すべてのアイテムを主軸に沿って均等に配置します。
- もう 1 つの値、`space-between` があります。 これは、両端にスペースを残さないという点を除けば、`space-around` にってもよく似ています。

[`justify-items`](/ja/docs/Web/CSS/justify-items) プロパティはフレックスボックスレイアウトでは無視されます。

続ける前に、これらの値を使用してそれらがどのように機能するかを確認することをお勧めします。

## フレックスアイテムの順序付け

フレックスボックスには、ソース順に影響を与えずにフレックスアイテムのレイアウトの順序を変更する機能もあります。 これも従来のレイアウト方法では不可能なことです。

このコードは簡単です。 ボタンバーのサンプルコードに次の CSS を追加してみてください。

```css
button:first-child {
  order: 1;
}
```

リフレッシュすると、 "Smile" ボタンが主軸の終点に移動したことがわかります。 これがどのように機能するかについてもう少し詳しく説明しましょう。

- 既定では、すべてのフレックスアイテムの {{cssxref("order")}} の値は 0 です。
- 大きな `order` の値が設定されているフレックスアイテムは、小さな `order` の値を持つアイテムよりも表示順序の後半に表示されます。
- 同じ `order` の値を持つフレックスアイテムは、ソース順で表示されます。 そのため、2、1、1、0 の `order` の値がそれぞれ設定された 4 つのアイテムがある場合、それらの表示順序は 4、2、3、1 となります。
- 3 番目のアイテムは 2 番目の後に表示されます。 これは、同じ `order` の値を持ち、ソース順でそれより後にあるためです。

負の `order` の値を設定して、0 が設定されているアイテムよりも早くアイテムを表示することができます。 例えば、次のルールを使用して、\[Blush] ボタンを主軸の始点に表示させることができます。

```css
button:last-child {
  order: -1;
}
```

## ネストしたフレックスボックス

フレックスボックスを使ってかなり複雑なレイアウトを作成することは可能です。 フレックスアイテムをフレックスコンテナーとしても設定して、その子も柔軟な箱のようにレイアウトできるようにしてもまったく問題ありません。 [complex-flexbox.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/complex-flexbox.html) を見てください（[ライブも見る](https://mdn.github.io/learning-area/css/css-layout/flexbox/complex-flexbox.html)）。

![サンプルフレックスボックスの例では、 3 つのフレックスアイテムの子を並べて保有しています。最初の 2 人は同じ幅で、3 人目は少し広くなっています。 3 つ目のフレックスアイテムはフレックスコンテナーでもあります。これには、 2 列に並んだボタンのセットと、それに続くテキストがあります。最初の行には 4 つのボタンがあり、一列に並んでいます。ボタンは同じ幅で、コンテナの幅いっぱいに保有されています。 2 つ目の行には、単一のボタンがあり、それ自体で行の幅をすべて保有しています。このように、フレックスアイテムがいくつかある複雑なレイアウトは、フレックスコンテナーとして扱われます。](flexbox-example7.png)

このための HTML はかなり単純です。 3 つの {{htmlelement("article")}} を含む {{htmlelement("section")}} 要素があります。 3 番目の {{htmlelement("article")}} には 3 つの {{htmlelement("div")}} が含まれています。

```
section - article
          article
          article - div - button
                    div   button
                    div   button
                          button
                          button
```

レイアウトに使用したコードを見てみましょう。

まず、{{htmlelement("section")}} の子を柔軟な箱として配置するように設定します。

```css
section {
  display: flex;
}
```

次に、{{htmlelement("article")}} 自体にいくつかの `flex` の値を設定します。 ここで 2 番目のルールに特に注意してください — 3 番目の {{htmlelement("article")}} は、その子もフレックスアイテムのようにレイアウトするように設定していますが、今回はそれらを `column` のようにレイアウトしています。

```css
article {
  flex: 1 200px;
}

article:nth-of-type(3) {
  flex: 3 200px;
  display: flex;
  flex-flow: column;
}
```

次に、最初の {{htmlelement("div")}} を選択します。 最初に `flex: 1 100px;` を使用して効果的にそれの最小の高さを 100px にしてから、その子（{{htmlelement("button")}} 要素）もフレックスアイテムのように配置されるように設定します。 ここでそれらをラッピングする行にレイアウトし、先ほど見た個々のボタンの例で行ったように、それらを使用可能なスペースの中央に配置します。

```css
article:nth-of-type(3) div:first-child {
  flex: 1 100px;
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: space-around;
}
```

最後に、ボタンにサイズを設定します。今回は、 flex 値として 1 auto を指定しました。これはとても興味深い効果があり、ブラウザーのウィンドウ幅を変更してみるとわかります。ボタンはできるだけ多くの空間を占有しようとします。できる限り同じ行に配置しようとしますが、それを超えると新しい行に移動します。

```css
button {
  flex: 1 auto;
  margin: 5px;
  font-size: 18px;
  line-height: 1.5;
}
```

## ブラウザー間の互換性

フレックスボックスは、Firefox、Chrome、Opera、Microsoft Edge、IE 11、Android / iOS の新しいバージョンなど、ほとんどの新しいブラウザーで利用できます。 ただし、フレックスボックスに対応していない古いブラウザー（または、対応しているものの、本当に古い、時代遅れのバージョンに対応しているもの）もあります。

学習や実験をしている間は、これはあまり重要ではありません。しかし、実際のウェブサイトでフレックスボックスを使用することを検討している場合は、テストを行い、できるだけ多くのブラウザーで使い勝手が許容範囲内になることを確認する必要があります。

フレックスボックスはいくつかの CSS 機能よりも少しトリッキーです。 例えば、ブラウザーに CSS ドロップシャドウがない場合でも、サイトを利用することはできます。しかし、フレックスボックス機能をサポートしていないと、レイアウトが完全に壊れて利用できなくなる可能性があります。

[クロスブラウザーのテスト](/ja/docs/Learn/Tools_and_testing/Cross_browser_testing)のモジュールでは、ブラウザー間の対応の問題を解決するための戦略について説明します。

## スキルをテストしましょう!

この記事の最後まで達しましたが、最も大事な情報を覚えていますか？次に移動する前に、この情報を保持しているか検証するテストがあります — [Test your skills: Flexbox: フレックスボックス](/ja/docs/Learn/CSS/CSS_layout/Flexbox_skills) を見てください。

## まとめ

これで、フレックスボックスの基本についてのツアーは終了です。 私たちはあなたが楽しみを持って、学習と共に前進するにつれてそれと一緒に良い遊びがあることを願っています。 次に、CSS レイアウトのもう 1 つの重要な側面、CSS グリッドについて見ていきます。

## 関連情報

- [CSS-Tricks Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) — フレックスボックスのすべてを視覚的にわかりやすく説明した記事です。
- [Flexbox Froggy](https://flexboxfroggy.com/) — フレックスボックスの基本を学び、理解を深めるための教育ゲームです。

{{PreviousMenuNext("Learn/CSS/CSS_layout/Normal_Flow", "Learn/CSS/CSS_layout/Grids", "Learn/CSS/CSS_layout")}}

## このモジュール内の文書

- [CSS レイアウト入門](/ja/docs/Learn/CSS/CSS_layout/Introduction)
- [通常フロー](/ja/docs/Learn/CSS/CSS_layout/Normal_Flow)
- [フレックスボックス](/ja/docs/Learn/CSS/CSS_layout/Flexbox)
- [グリッド](/ja/docs/Learn/CSS/CSS_layout/Grids)
- [フロート](/ja/docs/Learn/CSS/CSS_layout/Floats)
- [位置指定](/ja/docs/Learn/CSS/CSS_layout/Positioning)
- [段組みレイアウト](/ja/docs/Learn/CSS/CSS_layout/Multiple-column_Layout)
- [レスポンシブデザイン](/ja/docs/Learn/CSS/CSS_layout/Responsive_Design)
- [メディアクエリーの初心者向けガイド](/ja/docs/Learn/CSS/CSS_layout/Media_queries)
- [過去のレイアウト方法](/ja/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods)
- [古いブラウザーのサポート](/ja/docs/Learn/CSS/CSS_layout/Supporting_Older_Browsers)
- [基礎的なレイアウトの理解](/ja/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension)