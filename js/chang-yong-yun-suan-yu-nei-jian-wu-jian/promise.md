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

### 範例

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

{% hint style="warning" %}
但是我們在某個階段裏面發生錯誤時，該階段下一個是 `then` 的話就不會執行，會直接跳到 `catch`。

其實 `catch` 執行完畢後，還是可以繼續使用 `then` 串接，但在實務上我們很少會這麼做（我的測試是發現無論成功失敗這個cathc後面的then都會執行, 跟想像不一樣,還是少用好！）

```javascript
.then((res) => { return 某個錯誤promise行為 ) 
.then((res) => {console.log(res)}) // 不執行
.catch((err) => {return err+ '準備'})//跳到這邊
```
{% endhint %}



### 參考

* MDN JavaScript 參考文件=>標準內建物件=>[Promise](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global\_Objects/Promise)
* [你今天 Promise 了嗎？](https://5xruby.tw/posts/promise)
