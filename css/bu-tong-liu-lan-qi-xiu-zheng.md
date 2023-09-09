---
description: 瀏覽器修正不同
---

# 不同瀏覽器修正



### 重置CSS

每一個瀏覽器所使用的 HTML 預設樣式皆不同，例如table預設是否有線條等等，所以要統一。

* Normalize.css 保留原本預設 HTML 標籤的樣式，僅針對不同瀏覽器與各版本間不相容的標籤微調，且修復瀏覽器bug。
* reset.css 與 normalize.css 擇一使用即可，在一開始就要引入網頁。

### CSS 後處理加上前綴

[浏览器引擎前缀](https://developer.mozilla.org/zh-CN/docs/Glossary/Vendor\_Prefix)：浏览器厂商们有时会给实验性的或者非标准的 CSS 属性和 JavaScript API 添加前缀，这样开发者就可以用这些新的特性进行试验

* Autoprefixer 插件是最流行的 CSS 處理工具之一，用於自動處理瀏覽器兼容性問題



{% hint style="info" %}
之前提到的LESS、SASS、SCSS 是屬於預處理器（Preprocessors）。

PostCSS 後處理器（Postprocessors）是一個使用 JavaScript 轉換 CSS 的工具。
{% endhint %}



