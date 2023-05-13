# 函式

### `Function Statement`(函式陳述句)與`Function Expression`(函式表達式、表示式、 運算式)

* 陳述式：會執行一些程式碼，可能是幾個單詞或是一個片段（但不會是單一個字母），但最大的特徵是**不會回傳結果**。
  * 宣告（var、function）流程控制（block、if…else）迴圈（for、for…in）等等
* 表達式：最大的特徵在於**會回傳結果**。

ref: [JavaScript 表達式觀念及運用 - JS Expression](https://www.casper.tw/development/2020/09/17/js-expression/)



### ES5 函式宣告（Function Declaration）

```javascript

    //function 函式名稱(參數) {
    function Add(A, B) {
        return A + B;
    }
    /* 或 */
    
    // ES5  函式運算式(表達式)（Function Expressions）
    // var 函式名稱 = function (參數) {
    var Add2 = function (A, B) {//匿名函式
        return A + B;
    }
    var Add3 = function add3(A, B) {//#1 非匿名函式
        console.log(typeof add3);//#1 但只在自身有效
        return A + B;
    }
    console.log(Add(1, 2))//3
    console.log(Add2(1, 2))//3
    console.log(Add3(1, 2))//3
    //console.log(add3(1, 2))//#1 ReferenceError: add3 is not definedr
```

### ES6 宣告型態

```diff
+//ES6 : var 函式名稱 = (參數) => {return XX; }
    var Add4 = (A, B) => {
        return A + B;
    }
+  //縮寫 如果只有return 可以去掉{}與return
    var Add5 = (A, B) => A + B;

+   //縮寫 如果只有一個參數 可以去掉（）
    var AddS1 = (A) => A;
    var AddS2 = A => A;

    console.log("ES6:" + Add4(1, 2))//3
    console.log("ES6:" + Add5(1, 2))//3
```
