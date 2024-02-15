---
description: 媒體查詢
---

# 媒體

### 不一定要用媒體查詢，可以用grid/flex來做。



國際化

save for later

為了配合不同的書寫模式進行調整，請避免使用方向left/right屬性。請改用邏輯屬性。

\
\


## 文字

根據預設，文字會自動換行，且不含任何其他樣式。

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

save for later



## 圖片

```
img {
  max-inline-size: 100%;   //對應 max-width
  block-size: auto;  //對應height
 aspect-ratio: 2/1;   x/y 指定的 width / height 比率
  object-fit: cover; //會裁切
  object-position: top center; 保留焦點位置
}
```

[逻辑尺寸属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS\_logical\_properties\_and\_values/Sizing)

### 尺寸提示 <a href="#sizing_hints" id="sizing_hints"></a>

如果您知道圖片尺寸，請加入 `width` 和 `height` 屬性。即使圖片是以不同大小顯示 (因為 `max-inline-size: 100%` 規則)，瀏覽器依然知道寬度和高度的比例，並且能夠設定正確的空間量。這樣一來，當圖片載入時，其他內容就會停止跳轉。

### 正在載入提示

使用 `loading` 屬性，指示瀏覽器是否要延遲載入圖片，直到圖片位於可視區域範圍內或靠近可視區域。如果是需捲動位置圖片，請使用 `lazy` 的值。瀏覽器要等到使用者向下捲動網頁，直到圖片即將顯示圖片為止，才會載入延遲圖片。如果使用者從未捲動畫面，圖片就不會載入。

對於不需捲動位置的主頁橫幅，請勿使用 `loading`。如果您的網站自動套用 `loading="lazy"` 屬性，通常可以透過設定 `eager` 屬性 (此為預設值) 來避免套用上述屬性：

\


\
