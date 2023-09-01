# this

### 參考文章&#x20;

* [淺談 JavaScript 頭號難題 this：絕對不完整，但保證好懂](https://blog.techbridge.cc/2019/02/23/javascript-this/)
  * JavaScript 裡的 this (在任何地方都可以存取到 this)跟其他程式語言慣用的那個 this (它代表的就是在物件導向裡面，那個 instance 實例本身。)有差異
  * 區分
    1. 嚴格模式底下就都是`undefined`
    2. 非嚴格模式，瀏覽器底下是`window`
    3. 非嚴格模式，node.js 底下是`global`
  * 總結
    1. 在物件以外的 this 基本上沒有任何意義，硬要輸出的話會給個預設值
    2. 可以用 call、apply 與 bind 改變 this 的值:如下

```
'use strict';
function hello(a, b){
  console.log(this, a, b)
}

hello(1, 2) // undefined 1 2
hello.call(undefined, 1, 2) // undefined 1 2
hello.apply(undefined, [1, 2]) // undefined 1 2

'use strict';
function hello(a, b){
  console.log(this, a, b)
}

hello.call('yo', 1, 2) // yo 1 2
hello.apply('hihihi', [1, 2]) // hihihi 1 2

'use strict';
function hello() {
  console.log(this)
}

const myHello = hello.bind('my')
myHello() // my
```

* [this · 從ES6開始的JavaScript學習生活](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/this.html)
  * `this`的指向的是目前呼叫函式或方法的擁有者(owner)物件，也就是說它與函式如何被呼叫或調用有關
  * 對this值來說，它根本不關心函式是在哪裡定義或是怎麼定義的，它只關心是誰呼叫了它。

```javascript
function func(param1, param2){
  console.log(this)
}

const objA = {
  test(){
    console.log(this)
  }
}

func() //undefined
objA.test() //Object(objA)
//func函式在呼叫時的this值是undefined，原本它應該會回傳全域物件，在瀏覽器中就是window物件，
//這是因為babel預設會開啟strict mode(嚴格模式)，為了安全性的理由，原本的全域物件變成了undefined
//objA.test方法在呼叫時的this值就是objA物件本身
//=
const obj = {
  value: 1,
  hello: function() {
    console.log(this.value)
  }
}

obj.hello() // 1
const hey = obj.hello
hey() // undefined
```



* [學好this 前，先搞清楚this 做什麼| 卡斯伯Blog - 前端，沒有極限](https://www.casper.tw/development/2020/09/27/why-this/)
  * 導入物件的概念以後，就需要使用 `this` 來取得或呼叫物件中彼此之間的方法與資料
  * 也因此 `this` 是一個取得本地元件屬性的方法（觀念非常多，但實戰中只會用到一招而已）



* [\[筆記\]-JavaScript bind、call、apply是什麼?關於他們的4個重點](https://jianline.com/javascript-bind-call-apply/)
  * 透過bind、apply、call我們可以改變this的指向，來拿到正確的內容
  * bind會創建一個新的綁定函式，並返回該函式。 apply、call會立即執行綁定的函式。

```javascript
apply與call二者的作用完全一樣，只是第二個參數的接受方式有所區別。
function.call(thisArg, arg1, arg2, ...)
function.apply(thisArg, [argsArray])

call的第2個參數需要把參數依序傳入，就如同函式的參數。
apply的第2個參數則必須是一個 array-like object，也就是參數必須以陣列形式傳入。

function.bind(thisArg, arg1, arg2, ...)
bind是創建一個新的綁定函式，這個函式包裝了原本的函式，並且與第一個參數的this綁定。
經常聽到的currying(柯里化)在使用上經常與bind結合，幫助我們優化許多程式的寫法。
```

