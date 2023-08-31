# 立即函式IIFE

[IIFE (Immediately Invoked Function Expression) ](https://developer.mozilla.org/zh-TW/docs/Glossary/IIFE)是一個定義完馬上就執行的 JavaScript function



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

