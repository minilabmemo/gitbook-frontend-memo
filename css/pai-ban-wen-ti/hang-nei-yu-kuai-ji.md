---
description: 行內與塊級
---

# 行內與塊級

預設是 inline 的標籤, 行內元素 (inline element)



MDN [List of "inline" elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline\_elements#list\_of\_inline\_elements)

input/img/button

#### Q img到底是行內還是塊級

[Element/img#styling\_with\_css](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#styling\_with\_css)

{% hint style="info" %}
`<img>` 是一个[可替换元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced\_element)。它的 [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 属性的默认值是 `inline`，但是它的默认分辨率是由被嵌入的图片的原始宽高来确定的，使得它就像 `inline-block` 一样。你可以为 `<img>` 设置 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border)/[`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius)、[`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)/[`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin)、[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)、[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 等 CSS 属性。
{% endhint %}



ref

|                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [你知道CSS中的替换元素吗？](https://blog.csdn.net/m0\_47901007/article/details/127240751)                           | <p> <code>&#x3C;img></code>、<code>video</code>、<code>iframe</code>或者表单元素<code>textarea</code>和<code>input</code>都是替换元素。<br><br>content 属性改变的仅仅是视觉呈现，当我们以右键或其他形式保存这张图片的时候，所保存的还是原来 src 对应的图片。<br><br>很多替换元素在没有明确尺寸设定的情况下:</p><p>其默认的尺寸（不包括边框）是 300 像素×150 像素，如<code>video</code>、<code>iframe</code>或者<code>canvas</code>等;</p><p>图片替换元素为 0 像素;</p><p>表单元素的替换元素的尺寸则和浏览器有关;<br><br><strong>替换元素都是内联元素</strong></p><p>替换元素和替换元素、替换元素和文字都是可以在一行显示的。</p>                |
| [可替换元素 MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced\_element)                          | 在 CSS 中，可替换元素（replaced element）的展现效果不是由 CSS 来控制的。这些元素是一种外部对象，它们外观的渲染，是独立于 CSS 的。                                                                                                                                                                                                                                                                                                                                                                                   |
| [行内元素和块级元素的区别，为何img、input等行内元素可以设置宽高??（夯实基础）](https://blog.csdn.net/zhouzuoluo/article/details/81064168) | <p>行内元素设置宽高无效（<mark style="background-color:orange;"><strong>但是行内置换元素可以设置宽高</strong></mark>，下面有详细解释）、设置上下margin无效，设置上下padding类似无效（不影响文档流排列）<br><br>替换元素：替换元素根据其标签和属性来决定元素的具体显示内容，&#x3C;select>&#x3C;select>&#x3C;object>等。替换一般有内在尺寸如img默认的src属性引用的图片的宽高，表单元素如input也有默认的尺寸。img和input的宽高可以设定。</p>                                                                                                                                                                    |
| [HTML 小知識 - 區塊元素 vs 行內元素](https://yanennnnn.github.io/html/20200827/fd7f7d68/)                           | <p></p><h4 id="ke-bian-yuan-su-bao-han">可變元素包含</h4><ul><li>applet - java applet</li><li>button - 按鈕</li><li>del - 刪除</li><li>iframe - 嵌入框架的應用</li><li>ins - 定義標記插入的部份</li><li>map - 圖片區塊</li><li>object - object對象</li><li>script - 嵌入或引用要執行的程式碼<br><br><mark style="background-color:orange;">基本上區塊元素可以包含行內元素和某些區塊元素，行內元素不能包含區塊元素，只能包含行內元素，但有些小特例</mark>，例如:</li><li>a 連結幾乎都能包含，不能包含 a 連結</li><li>p 段落不能包含區塊元素</li><li>li 標籤可以包含 div 以及他的父元素 ul, ol<br></li></ul> |
