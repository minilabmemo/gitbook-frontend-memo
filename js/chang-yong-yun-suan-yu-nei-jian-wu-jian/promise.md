# Promise

## **`語法`**

**`Promise`** 物件代表一個即將完成、或失敗的非同步操作，以及它所產生的值。是用來優化非同步的語法

<pre class="language-diff"><code class="lang-diff"><strong>+// 語法
</strong><strong>new Promise( /* executor */ function(resolve, reject) { ... } );
</strong>
+// 範例
const myFirstPromise = new Promise((resolve, reject) => {
  // *執行一些非同步作業，最終呼叫:
  //
  //   resolve(someValue); // 實現
  // 或
  //   reject("failure reason"); // 拒絕
});
</code></pre>

* 為一個依序接收兩個參數的函式：`resolve` 及 `reject`（實現及拒絕回呼函式）
* \*通常 executor 函式會發起一些非同步操作
* 成功完成後執行 `resolve` 以完成 promise；或如果有錯誤，執行 `rejects`。 如果 executor 函式在執行中拋出錯誤，promise 會被拒絕（rejected），回傳值也將被忽略。

### 基本範例

```javascript
let myFirstPromise = new Promise((resolve, reject) => {
  // 當非同步作業成功時，呼叫 resolve(...),而失敗時則呼叫 reject(...)。
  // 在這個例子中，使用 setTimeout(...) 來模擬非同步程式碼。
  // 在實務中，您將可能使用像是 XHR 或者一個 HTML5 API.
  setTimeout(function () {
    resolve("Success!"); // 這裡面的參數會傳到then裡
  }, 250);
});

myFirstPromise
  .then((successMessage) => {
    // successMessage 是任何您由上方 resolve(...) 傳入的東西。
    // 在此僅作為成功訊息，但是它不一定是字串。
    console.log("then! " + successMessage);
    return successMessage + 'added at 1st then'
  }
  )
  // 第二個then為接收上一個then的return
  .then((successMessage) => { console.log("2nd then! " + successMessage); })
  
  .catch((err) => { console.log(err) })
  .finally(() => { console.log("ok finally") })
```

* 第二個then為接收上一個then的return, 注意如果第一個忘了retrun 這邊接收到的東西就是undefined,不會有任何錯誤。
* 由於 `Promise.prototype.then()` 以及 `Promise.prototype.catch()` 方法都回傳 promise，它們可以被串接。
* 但如果我們在 `.then` 中是 return 另一個 `new Promise` ，則下一個 `.then` 會等到這個 Promise 中的 resolve 得到值後才執行。且在下一個 `.then` 的 `resolvedCallback` 中，可以得到上一個 `new Promise` 中 `resolve` 的值

{% hint style="warning" %}
但是我們在某個階段裏面發生錯誤時，該階段下一個是 `then` 的話就不會執行，會直接跳到 `catch`。

其實 `catch` 執行完畢後，還是可以繼續使用 `then` 串接，但在實務上我們很少會這麼做

* （我的測試是發現無論成功失敗這個cathc後面的then都會執行, 跟想像不一樣,還是少用好！） 除非有特殊需要，不然 .catch() 通常會放在最後

```
.then((res) => { return 某個錯誤promise行為 ) 
.then((res) => {console.log(res)}) // 不執行
.catch((err) => {return err+ '準備'})//跳到這邊
```
{% endhint %}

### 範例: 帶入參數回傳Promise

```
// 等待一秒執行一次的範例
function waitASecond(second) {
  console.log("waitASecond:"+second);
  return new Promise((resolve, reject) => {
    setTimeout(function () {
      second++;
      resolve(second);
    }, 1000);
  });
}

waitASecond(0)
  .then(waitASecond)  //回傳 new Promise
  .then(waitASecond) //回傳 new Promise
  .then((second) => {
    console.log(second);
  });
  
// 結果 以下都等待一秒才出現
waitASecond:0
waitASecond:1
waitASecond:2
3
```

### Promise.all

```
Promise.all(iterable);
```

* 一個 iterable 物件像是 `Array` 或 `String`。回傳一個以 iterable 其內**所有**值（包含非 promise 值）
* `當任一個陣列成員被拒絕則` `Promise.all` 被拒絕。例如，若傳入四個將在一段時間後被解決的 promises，而其中一個立刻被拒絕，則 `Promise.all` 將立刻被拒絕。

```diff
var p1 = Promise.resolve(3);
var p2 = 1337;
var p3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'foo');
});

Promise.all([p1, p2, p3]).then(values => {
  console.log(values); // [3, 1337, "foo"]. //會等待所有都回傳為止
});

- 需注意假設有一個沒有回 會一直等待下去.... 沒有timeout?

```

#### 其中一個拒絕範例

```
var p1 = new Promise((resolve, reject) => {
  setTimeout(()=>{ resolve("one");console.log("p1");}, 1000);
});
var p2 = new Promise((resolve, reject) => {
  setTimeout(()=>{ console.log("p2");resolve("two")}, 2000);
});
var p3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 3000, 'three');  //等同於resolve('three')
});
var p4 = new Promise((resolve, reject) => {
  setTimeout(resolve, 4000, 'four');
});
var p5 = new Promise((resolve, reject) => {
  reject('reject');
});


// 正常狀況
// Promise.all([p1, p2, p3, p4]).then(values => {
//   console.log("[Promise.all 1~4]:"+values); //[Promise.all 1~4]:one,two,three,four
// }, reason => {
//   console.log(reason)
// });

//一個拒絕
Promise.all([p1, p2, p3, p4, p5]).then(values => {
  console.log("[Promise.all 1~5]"+values);
}, reason => {
  console.log(reason)
});


// 回傳結果
reject // 等到有一個拒絕就馬上先回拒絕
p1  //但其他的等待一秒還是會執行
p2
```

### 參考

* MDN JavaScript 參考文件=>標準內建物件=>[Promise](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global\_Objects/Promise)
* [你今天 Promise 了嗎？](https://5xruby.tw/posts/promise)
