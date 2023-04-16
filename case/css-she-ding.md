---
description: 設定
---

# CSS設定

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
