# 立即函式IIFE

[IIFE (Immediately Invoked Function Expression) ](https://developer.mozilla.org/zh-TW/docs/Glossary/IIFE)是一個定義完馬上就執行的 JavaScript function

第一個部分是使用`Grouping Operator` (en-US) `()` 包起來的 anonymous function。這樣的寫法可以避免裡面的變數污染到 global scope。

第二個部分是馬上執行 function 的 expression `()`，JavaScript 引擎看到它就會立刻轉譯該 function。

[https://www.explainthis.io/zh-hant/swe/what-is-iife](https://www.explainthis.io/zh-hant/swe/what-is-iife)\
IIFE 的缺點 不利於重複使用

* JS

```
(function () {
  var aName = "Barry";
})();
// Variable name is not accessible from the outside scope
aName; // throws "Uncaught ReferenceError: aName is not defined"
```

* JS Arrow

```
(() => {
  var aName = "Barry";
})();
```

