---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 實務狀況

### 盒子模型的邊距折疊問題

關鍵問題：子元素margin-top导致父元素移动的问题，

* [MDN CSS 外边距重叠](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS\_box\_model/Mastering\_margin\_collapsing) 會發生的情況說明
* [子元素margin-top导致父元素移动的问题](https://www.jianshu.com/p/6d9fb5fbbd34) 說明與解法
* [子元素设置margin-top和margin-bottom无效，外边距折叠导致父元素移动](https://blog.csdn.net/aaahuahua/article/details/115288283)

{% hint style="info" %}
塊的上外邊距(margin-top)和下外邊距(margin-bottom)有時合併(折疊)為單個邊距，其大小為單個邊距的最大值，這種行為稱為邊距折疊。
{% endhint %}

## 　當物件設定abosolute之後的置中方式

* [幾個我自己常用的水平置中或垂直置中的方式](https://ithelp.ithome.com.tw/articles/10228762)
  * 講得很好包括Margin置中的缺點/區塊與文字置中背後概念

## 有彈出框的設計卻點了沒反應

設計上有可能彈出框是在上層卻隱藏,點了才會出現,這時如果他佔據了空間且事件,會使你點不到底層,因此隱藏的方式很重要,建議用none隱藏使他完全消失,如果只是透明度隱藏還是存在

* [css隐藏元素 触发点击事件,CSS隐藏元素的方法及区别](https://blog.csdn.net/weixin\_35390057/article/details/119367585)



### 使用了獨立元件包含一個 a link設定,但是卻常常點不到或是要等待

根據你提供的程式碼，你使用了 `position: absolute;` 屬性將 `Brand` 元件定位為絕對位置。這可能會導致點擊問題，因為 `Brand` 元件被絕對定位並且可能覆蓋了 `Link` 元件。

1. 調整層級和定位：檢查你的元件層級和定位方式，確保 `Link` 元件處於上層並能夠接收點擊事件。
2. 調整 CSS 屬性：檢查 `Brand` 元件的 CSS 屬性，特別是 `z-index`、`pointer-events` 等，確保它們不會阻止 `Link` 元件的點擊事件。
3. 使用 `Link` 元件外部包裹：將 `Brand` 元件放在 `Link` 元件之外，以確保 `Link` 元件能夠正確接收點擊事件。



### flex-start的整體置中問題

我有一個內容器不固定大小，且裡面的物件靠左排列，但這樣做的話右邊會多出一線不自然的空間，換spaxe-between等等設定又會讓兩個物件也置中了。

類似問題:[CSS 外容器水平置中、內容器的內物件靠左排列問題。](https://ithelp.ithome.com.tw/questions/10209489)

發現是使用外容器 flex 置中，內容器採 grid 排列就解決了。



