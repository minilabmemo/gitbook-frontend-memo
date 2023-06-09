# 函式

### `Function Statement`(函式陳述句)與`Function Expression`(函式表達式、表示式、 運算式)

* 陳述式：會執行一些程式碼，可能是幾個單詞或是一個片段（但不會是單一個字母），但最大的特徵是**不會回傳結果**。
  * 宣告（var、function）流程控制（block、if…else）迴圈（for、for…in）等等
* [<mark style="color:red;">表達式：最大的特徵在於</mark><mark style="color:red;">**會回傳結果**</mark>](#user-content-fn-1)[^1]。

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

## CPS風格與回調(Callback)

* CPS用的是明確地移轉控制權到下一個函式中，也就是使用"延續函式"的方式，一般稱它為"回調函式"或"回調(Callback)"。回調是一個可以作為傳入參數的函式，用於在目前的函式呼叫執行最後移交控制權，而不使用函式回傳值的方式。
*

    ```js
    //CPS風格
    function func(x, cb) {
      cb(x) //將本來應該要回傳的值(不限定只有一個)，傳給下一個延續函式，繼續下個函式的執行:
    }
    ```
* 相較直接風格的程式碼是最常被使用與教學，因為它容易被學習與理解
* JavaScript中會大量使用CPS風格來設計事件異步處理的模型，用於配合異步回調函式的執行使用。

{% hint style="info" %}
[Callback 回調· 從ES6開始的JavaScript學習生活](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/callback.html)

複雜的情況是在於CPS風格使用callback(回調)來移往下一個函式執行，當你開始撰寫一個接著一個執行的流程，也就是一個特定工作的函式呼叫後要接下一個特定工作的函式時，就會看到所謂的"<mark style="color:red;">回調地獄</mark>"的結構 「<mark style="color:red;">`callback`</mark> <mark style="color:red;"></mark><mark style="color:red;">一多，縮排就會很醜</mark>」

<pre><code><strong>
</strong><strong>step1(x, function(value1){
</strong>  //do something...
  step2(y, function(value2){
    //do something...
    step3(z, function(value3){
        //do something...
    })
  })
})
<strong>那為何為不使用直接風格？而一定要用這麼不易理解的程式流程結構。上面已經有講為什麼JavaScript中會大量的使用CPS的原因:
</strong>因為有些I/O或事件類的函式，用直接風格會造成阻塞，所以要寫成異步的回調函式，也就是一定要用CPS
</code></pre>

現在已經有很多協助處理的方式，回調地獄可以用例如Promise、generator（少用了？）、async/await之類的語法結構，或是Async、co外部函式庫等，來改善或重構原本的程式碼結構，在往後維護程式碼上會比較容易，這些才是你現在應該就要學習的方式。
{% endhint %}



[^1]: 
