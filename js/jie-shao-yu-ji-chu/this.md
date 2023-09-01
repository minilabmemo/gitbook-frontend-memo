# this

### this&#x20;

* [淺談 JavaScript 頭號難題 this：絕對不完整，但保證好懂](https://blog.techbridge.cc/2019/02/23/javascript-this/)
  * JavaScript 裡的 this (在任何地方都可以存取到 this)跟其他程式語言慣用的那個 this (它代表的就是在物件導向裡面，那個 instance 實例本身。)有差異
  *

      1. 嚴格模式底下就都是`undefined`
      2. 非嚴格模式，瀏覽器底下是`window`
      3. 非嚴格模式，node.js 底下是`global`


* [this · 從ES6開始的JavaScript學習生活](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/this.html)
  * `this`的指向的是目前呼叫函式或方法的擁有者(owner)物件，也就是說它與函式如何被呼叫或調用有關

```
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
```



* [學好this 前，先搞清楚this 做什麼| 卡斯伯Blog - 前端，沒有極限](https://www.casper.tw/development/2020/09/27/why-this/)
  * 導入物件的概念以後，就需要使用 `this` 來取得或呼叫物件中彼此之間的方法與資料
  * 也因此 `this` 是一個取得本地元件屬性的方法（觀念非常多，但實戰中只會用到一招而已）
