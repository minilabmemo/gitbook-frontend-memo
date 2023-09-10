---
description: 基礎設定
---

# CSS基礎

### 寬度與長度

```
width: auto 這是預設值，自身的（content+margin+padding+border）相加為父元素的width大小
width: 100%; 的時候，基本上該物件寬度將會等於是父層"內容的可運用"空間
*內容可運用空間？其實就是 padding 以內的空間

width: 100vw; 的時候，該物件的大小將會等於是百分之百的「視窗」寬度
另外還有 CSS3 max/min-content及fit-content等width值
```

`width: 100vw` 很容易造成視窗出現橫向卷軸的問題，所以一般我們在開發網頁時多會使用 `width: 100%` 而非 `width:100vw`

width:100%；会强制将元素变成和父元素一样的宽，并且添加额外的空间到这个元素的width上。就是因为这个，会导致很多问题。

使用width:100%永远都不是一个好主意。这个属性容易让人产生你正在定义一个元素可视大小，其实，你是在对这个元素的状态做了巨大的改变。



比較：[https://codesandbox.io/s/css3-width-x23ykr](https://codesandbox.io/s/css3-width-x23ykr)

### 行高

寫法是 `line-height:1.8;`，行高會依照(該元素設定的文字大小 x 1.8)的結果作計算。



### 滑鼠的 cursor ​

可以​禁用

```
  cursor: not-allowed;​
```



### 語法sess ​中＆用法

＆符號是什麼意思

```
bordered {
  &.float {
    float: left; 
  }
  .top {
    margin: 5px; 
  }
}
等同于：

.bordered.float {
  float: left; 
}
.bordered .top {
  margin: 5px;
}
.bordered.float 是串联选择器，作用在同一标签上
.bordered .top 是后代选择器，作用在不同标签上

```

### 背景

```css
ackground-repeat: round. 
//我有一張圖，超級大，但是我設定了滿版效果，試圖填滿螢幕
但發現超出去的地方不見了，而我用了這個設定，它就自動縮小填滿了

使用縮放或變形的方式，讓背景圖片在不裁切的情況下填滿空間。
```

### animation

縮寫順序：

```diff
animation: 
name | duration | timing-function | delay | iteration-count direction | fill-mode | play-state;

+duration 在delay之前，有的會建議你不要縮寫
```

* JS. DOM [Style animationDelay Property](https://www.w3schools.com/jsref/prop\_style\_animationdelay.asp)
