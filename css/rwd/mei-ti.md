---
description: 媒體查詢
---

# 媒體

### 不一定要用媒體查詢，可以用grid/flex來做。



## 文字

```
html {
  font-size: clamp(1rem, 0.75rem + 1.5vw, 2rem);
}
```

### 文行長度 <a href="#line_length" id="line_length"></a>

請勿使用固定單位 (例如 `px`) 設定行長度。使用者可以縮放字型，而線條長度也應隨之調整。使用[相對單位](https://web.dev/learn/css/sizing?hl=zh-tw#relative\_lengths)，例如 `rem` 或 `ch`。

```
article {
  max-inline-size: 66ch;
}
```

### 行高 <a href="#line_height" id="line_height"></a>

較短的文字行有較大的 `line-height` 值。

請在 `line-height` 宣告中使用無單位值。這可確保行高是相對於 `font-size`。

```
article {
  max-inline-size: 66ch;
  line-height: 1.65;
}
blockquote {
  max-inline-size: 45ch;
  line-height: 2;
}
```

### 正在載入字型 <a href="#font_loading" id="font_loading"></a>

TBD
