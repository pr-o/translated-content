---
title: HTMLImageElement.width
slug: Web/API/HTMLImageElement/width
page-type: web-api-instance-property
tags:
  - API
  - HTML
  - HTML DOM
  - HTMLImageElement
  - 画像
  - プロパティ
  - リファレンス
  - size
  - width
browser-compat: api.HTMLImageElement.width
translation_of: Web/API/HTMLImageElement/width
---
{{APIRef("HTML DOM")}}

**`width`** は {{domxref("HTMLImageElement")}} インターフェイスのプロパティで、画像が画面やプリンターなどの視覚媒体に描画または表示される場合は {{Glossary("CSS pixel", "CSS ピクセル")}}で、それ以外は画像のピクセル密度補正後の幅を表します。

## 値

画像の幅を表す整数値です。幅を定義する方法は、画像が画面やプリンターのような視覚的媒体にレンダリングされるかどうかに依存します。

- 画像が視覚媒体にレンダリングされる場合、幅は {{Glossary("CSS pixel", "CSS ピクセル")}}で表現されます。
- 画像が視覚媒体にレンダリングされない場合、画像の幅は、 {{domxref("HTMLImageElement.naturalWidth", "naturalWidth")}} で示される表示密度用に調整された自然の（固有の）幅で表わされます。

## 例

この例では、 {{htmlattrxref("srcset", "img")}} 属性を使って、時計の画像に 2 種類の大きさの画像を用意しています。ひとつは幅 200px、もうひとつは幅 400px です。 {{htmlattrxref("sizes", "img")}} 属性は、ビューポートの幅を考慮して画像を描画する幅を指定するために提供されています。

### HTML

幅 400px までのビューポートでは、 200px の幅で描画されます。
それ以外の場合は、 400px で描画されます。

```html
<p>画像の幅: <span class="size">?</span>px (リサイズで更新)</p>
<img src="/en-US/docs/Web/HTML/Element/img/clock-demo-200px.png"
      alt="Clock"
      srcset="/en-US/docs/Web/HTML/Element/img/clock-demo-200px.png 200w,
          /en-US/docs/Web/HTML/Element/img/clock-demo-400px.png 400w"
      sizes="(max-width: 400px) 200px, 400px">
```

### JavaScript

JavaScript は `width` プロパティを調べて、その時点での画像の幅を決定します。これはウィンドウの {{domxref("Window.load_event", "load")}} と {{domxref("Window.resize_event", "resize")}} イベントハンドラーで行われるので、常に最新の幅情報を利用することができます。

```js
var clockImage = document.querySelector("img");
let output = document.querySelector(".size");

const updateWidth = event => { output.innerText = clockImage.width; };

window.addEventListener("load", updateWidth);
window.addEventListener("resize", updateWidth);
```

### 結果

{{EmbedLiveSample("Example", 640, 450)}}

この例は{{LiveSampleLink('Example', '独自のウィンドウ')}}で試してみるとわかりやすいかもしれません。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
