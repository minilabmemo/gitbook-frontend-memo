# RWD

## RWD

my hackme

[https://hackmd.io/fc7Hyyn7RO-SSVC99ze8Rw#%E7%B7%9A%E4%B8%8A%E6%95%99%E5%AD%B8](https://hackmd.io/fc7Hyyn7RO-SSVC99ze8Rw#%E7%B7%9A%E4%B8%8A%E6%95%99%E5%AD%B8)

google RWD

[https://web.dev/learn/design](https://web.dev/learn/design)





### 📑文章

**Day13：小事之 HTML viewport 與 meta tag**

[https://ithelp.ithome.com.tw/articles/10195279](https://ithelp.ithome.com.tw/articles/10195279)

#### **width=device-width**

因為目前手機尺寸非常多，因此，我們就只要設定為 width=device-width 就可以自動符合所有不同手機螢幕他們自己的預設最佳解析度。

#### **initial-scale=1**

設定手機螢幕畫面的初始縮放比例為 100%。

#### **user-scalable=no**

有時候網站會有特殊設定，或者業主有指定不允許使用者改變縮放比例，則會將值設為 no。

若 html 檔的`<head>`區塊中少了這個設定，網頁大概從載入完成時的樣子就會跟自己一開始的想像不同，因為若沒有在 meta 中定義 viewport，瀏覽器會自行定義給予預設值。

### 📑文章

**Responsive Web Design 基礎 : 設定**

[https://medium.com/frochu/html-meta-viewport-setting-69fbb06ed3d8](https://medium.com/frochu/html-meta-viewport-setting-69fbb06ed3d8)

```
因此常見的設定大概是：
// 指定螢幕寬度為裝置寬度，畫面載入初始縮放比例 100%
<meta name="viewport" content="width=device-width, initial-scale=1" >// 以下兩種設定都可以防止使用者做畫面縮放，將畫面鎖在縮放比例 100%
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1" ><meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
```

世大運專案有/無設定viewport頁面排版比較

### 💧影片 金魚

**金魚都能懂網頁設計入門 : RWD入門 - 鐵人賽第二十一天 | RWD教學 | 網頁教學 | RWD網頁 | CSS教學**

RWD 最簡單方式 就是用百分比

例如百分比的寬

1.少考量特別寬的螢幕

2.如果以手機為主

設定一個

max-width:1400px. 或是 1170/1200

1. 接著設定電腦

screen and min-width 768

,.xxx{

disply:flex. 補一下viewport

搞定

然後用開發者模式 點手機圖示看看是正常的

有了flex就可以很偷懶

上面可以去改解析度 例如2000看起來是這樣

看裝置類型，大多數會切分三大類型，手機/平板/桌機，當然也有一些單位的設計師根本要前端通靈，這就比較難處理一點，不論如何，還是盡量減少通靈的機會比較好XD

### 💧參考資料

### 💧參考資料

**瀏覽器尺寸**

**瀏覽器直立或橫放**

[https://pjchender.dev/css/css-media-query/](https://pjchender.dev/css/css-media-query/)

```jsx

@media screen and (min-width: 1024px) {
  /*STYLES*/
}
@media screen and (min-width: 1200px) {
  // 如果使用者之視窗寬度 >= 1200px，將會再載入這裡的 CSS。
}

@media screen and (min-width: 768px) and (max-width: 979px) {
  // 如果使用者之視窗寬度介於 768px ~ 979px，將會再載入這裡的 CSS。
}

@media screen and (max-width: 767px) {
  // 如果使用者之視窗寬度 <= 768px，將會再載入這裡的 CSS。
}

@media screen and (max-device-width: 480px) {
  // 如果使用者之裝置寬度 <= 480px，將會再載入這裡的 CSS。
}

body{background-color:#555}
@media all and (max-width: 1500px) {body {background-color:#cc9 }}
@media all and (max-width: 1024px) { body { background-color:#ff0 }}
@media all and (max-width: 900px) { body { background-color:#900 }}
@media all and (max-width: 610px) { body {background-color:#c90}}
@media all and (max-width: 350px) { body { background-color:#0c6}}
```

💧文章  [**CSS 小技巧分享：em 單位的強大用途**](https://medium.com/%E9%BA%A5%E5%85%8B%E7%9A%84%E5%8D%8A%E8%B7%AF%E5%87%BA%E5%AE%B6%E7%AD%86%E8%A8%98/css-%E5%B0%8F%E6%8A%80%E5%B7%A7%E5%88%86%E4%BA%AB-em-%E5%96%AE%E4%BD%8D%E7%9A%84%E5%BC%B7%E5%A4%A7%E7%94%A8%E9%80%94-457dc30a83b4)

在 CSS 中，em 單位是相對長度單位，它是相對於該元素本身字體大小（font-size 屬性）的值，如果找不到設定就往父元素找，皆無設定，則依照瀏覽器預設值：通常是 16px。

**搭配 Media Queries 的使用，去設定不同字體大小，然後讓他本身的一些padding/margin等等設定1em等相對長度**

```jsx
.container {
 font-size: 20px;
 padding: 1em;  屬性值為 20px = 1 * 20
 margin-top: .5em; 
 border-radius: .2em;
}
```

1. 文章開始時有提到「em」是個「相對長度單位」，因此在做網頁樣式設定時，需要花點時間調整數值，來達到理想中的成果。
2. 但未必所有元素和屬性都必須或適合以此做設定。舉例來說：我認為名片邊框的 `border-width` 屬性值不適合跟著增加或減少，因此改以「px」做為單位，將之固定。

### 實戰

我的MacBook Pro 15-inch, 2017 版本螢幕看網頁 寬是1467px
