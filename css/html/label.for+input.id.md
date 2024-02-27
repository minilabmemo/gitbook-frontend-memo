# label.for+input.id

[https://www.fooish.com/html/label-tag.html](https://www.fooish.com/html/label-tag.html)\
\<label> 用來給表單的控制元件一個說明標題，可以搭配 \<label> 的像是 input, textarea, select, button, meter, output, progress 這些表單元件。

\
\
\
\<label> 還有一個常見的用途，是用來增加表單元件的可點擊範圍，什麼意思呢？就是當你點 label 的文字時，等於你同時點擊了 label 關聯的表單元件。

而我們是利用 label 的 `for` 屬性，將 for 的屬性值設定為某表單元件的 `id` 值，藉此來建立關聯。

語法範例：

```html
<label for="emailadd">Email address: </label>
<input type="email" name="emailadd" id="emailadd">
```

如果你不想麻煩的還要設定 for 和 id，還有另外一種簡便的方法，就是將表單元件直接包在 `<label></label>` 裡面，也可以有一樣的效果。

例如：

```html
<label>Do you like peas?
  <input type="checkbox" name="peas">
</label>
```
