# html

1. 在 Input 使用的是 HTML 的 [datalist 元素](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist)，這個元素和傳統的 `<select>` 很類似，但不一樣的地方在於，使用者不只可以從下拉選單去做選擇，還可以在這個 `<input>` 裡面輸入文字進行搜尋，對使用者的體驗較友善，有興趣的話可以再參考 MDN 上關於 [datalist](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist) 的說明：

```
<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />

<datalist id="ice-cream-flavors">
  <option value="Chocolate"></option>
  <option value="Coconut"></option>
  <option value="Mint"></option>
  <option value="Strawberry"></option>
  <option value="Vanilla"></option>
</datalist>
```
