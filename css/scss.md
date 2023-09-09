# scss

## scss

### 檔案架構

[https://sass-guidelin.es/#architecture](https://sass-guidelin.es/#architecture)

There are [a lot of popular architectures](https://www.sitepoint.com/look-different-sass-architectures/) for CSS projects: [OOCSS](https://www.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/), [Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/), [Bootstrap](https://getbootstrap.com/)-like, [Foundation](https://get.foundation/)-like… They all have their merits, pros and cons.

**A Look at Different Sass Architectures**

[https://www.sitepoint.com/look-different-sass-architectures/](https://www.sitepoint.com/look-different-sass-architectures/)

裡面介紹多種架構 我比較喜歡 Style prototypes 不過不太確定裡面具體長樣？//TODO

**A Modern Sass Folder Structure**

[https://dev.to/dostonnabotov/a-modern-sass-folder-structure-330f](https://dev.to/dostonnabotov/a-modern-sass-folder-structure-330f)

結構一 `@import` 單一檔案 一個一個加入這樣

結構二 另一個是包入整個資料夾，不過看起來都要再寫index 我不喜歡這種用法

In `_index.scss` file, there should be only `@forward`,If you want to use all files within `abstracts/` folder, you can "use" them

**鐵人賽 20 - Sass 資料夾結構**

[https://www.casper.tw/css/2016/12/20/sass-folder/](https://www.casper.tw/css/2016/12/20/sass-folder/)

|– base/ | |– \_reset.scss # Reset/normalize

***

### **Variables**

[https://sass-guidelin.es/#variables](https://sass-guidelin.es/#variables)

在vscode時可以安裝SCSS intellisense 來移到上方看設定，不需要一直去檔案裡面上。

### **mixin**

**新手也可以輕鬆玩轉 SASS - @mixin and @include**

[https://5xruby.tw/posts/play-sass-mixin-and-include](https://5xruby.tw/posts/play-sass-mixin-and-include)

* 發現自己在 CSS 裡一直寫著重複的樣式。
* 網頁元件可以歸納出共同的特性時 (可能按鈕都有陰影、或是每個文章區塊都有邊框...等等)。

用法一 按鈕

用法二 參數

用法三 參數與預設值 就像是上面的混合用法

[https://sass-lang.com/guide/#mixins](https://sass-lang.com/guide/#mixins)

SCSS fotmat

在vscode格式化時他一直幫我換行，我把這功能關掉

**SCSS › Format: Newline Between Selectors**

以新行分隔選取器。
