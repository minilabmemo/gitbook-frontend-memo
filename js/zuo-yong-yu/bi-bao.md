---
description: 閉包
---

# 閉包

## 資料參考

* [ＭＤＮ 閉包](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Closures)
* 閉包（Closure）是函式以及該函式被宣告時所在的作用域環境（lexical environment）的組合。
* [\[JS\] 深入淺出 JavaScript 閉包（closure）](https://pjchender.dev/javascript/js-closure/)
  * 不使用閉包跟使用閉包的差異比較
  * **當你看到一個 function 內 return 了另一個 function，通常就是有用到閉包的概念**。
  * 圖解：分成 函式內要用到變數/真正要執行函示/把這個函示回傳出去。

###

***

### 語法作用域（Lexical scoping）

```
function makeFunc() {
  var count = 0// count 是個由 init 建立的局部變數
  function add() {// add() 是內部函式，一個閉包
     count=count+1// 使用了父函式宣告的變數
     console.log(count);
  }
  return add;
}

var myFunc = makeFunc();
myFunc();  //print 1
myFunc(); . //2
myFunc(); . //3
```

### 例子2：使用相同定義卻獨立不同環境

* add5 與 add10 都是閉包。他們共享函式的定義，卻保有不同的環境：
* 變數間也都是獨立的執行環境不會干擾

```
function makeAdder(x) {
  return function (y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2)); // 7
console.log(add10(2)); // 12
```

