---
description: 作用域
---

# 作用域

#### 不太懂

```
塊級作用域 (Block Level Scope) 是一種更小的作用域。只存在於 {} 中
let func = (() => {
    let number = 999; {
        console.log(number); // 999
    }
    console.log(number); // 999
})()
console.log(number); // ReferenceError: number is not defined



```

{% hint style="info" %}
上面這段程式碼，使用了 let 宣告變數 number；所以 number 在 {} 內擁有塊狀作用域。**number 只成立於宣告它時它位於的 {} 內，以及它的子 {} 內。**
{% endhint %}



| ref                                                                                                                                              | memo                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [\[JS\] Scope 作用域](https://medium.com/take-a-day-off/js-scope-%E4%BD%9C%E7%94%A8%E5%9F%9F-ee536640963b) medium                                   | <p>全域執行環境 (Global Execution Context)<br>全域變數不管是在函式內，還是函式外被使用，都是有效力的。<br>Function Level Scope 變數如果是在函式內 (函式的 {} 內) 被宣告。他的影響就只限於這個函式最外層的 {} 中出了 {} 就完全沒用了 (記憶體會被回收)。想要使用它會出現 ReferenceError</p><p></p><p><br>塊級作用域 (Block Level Scope) 是一種更小的作用域。只存在於 {} 中。最常出現在 Function Scope 中的 {} 中(像是 if、for 等語法)。聰明的你也許會想，是不是也可以將 Function Scope 看成是 Block Scope 的一種？是的<br><br>在 ES6 後，宣告變數還是建議只使用 const 或者 let 哦<br><br></p><p>var 的缺點：</p><p>允許重複宣告</p><p>不支援區塊作用域 (Block Scope)</p><p>不支援常數 (Constant) 特性<br><br>於 Javascript，只要暸解它是採用靜態作用域 (Static Scope) 或是所謂的語彙作用域 (Lexical Scope) 就可以了。<br><br>這樣的行為 — 由內到外的這條找尋鏈，我們就稱呼它為<strong>作用域鏈</strong>。</p> |
| [JavaScript全局作用域、函数作用域和块级作用域的区别](https://blog.csdn.net/m0\_46846526/article/details/118071919)                                                   | <p>全局作用域：函数外部的作用域</p><p>函数作用域；函数内部的作用域</p><p>块级作用域：{ } 包裹着的代码</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [Scope 作用域](https://ithelp.ithome.com.tw/articles/10206604) ithelp                                                                               | <p>全域環境是我們一開始在執行JavaScript，瀏覽器所建立的環境，也是最外層的環境。<br><br>在JavaScript中即使不以var宣告，一樣可以執行，但就算在涵式內也視為全域變數，更進一步來說，是window全域物件的屬性。</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [JS 宣告變數， var 與 let / const 差異](https://www.programfarmer.com/articles/2020/javascript-var-let-const-for-loop)                                   | <h3>var 與 let ，for 迴圈的綁定（bind）差異</h3><h3>var 的提升與 let / const 不同</h3><p></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [Javascript 的作用域 (Scope) 與作用域鏈 (Scope Chain) 是什麼?](https://www.explainthis.io/zh-hant/interview-guides/javascript/what-is-scope-and-scope-chain) | 簡單描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |



