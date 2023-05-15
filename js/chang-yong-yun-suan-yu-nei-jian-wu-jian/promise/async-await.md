# async, await

當 [`async`](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/async\_function) 函式被呼叫時，它會回傳一個 `Promise`。如果該 `async` 函式回傳了一個值，`Promise` 的狀態將為一個帶有該回傳值的 resolved。如果 `async` 函式拋出例外或某個值，`Promise` 的狀態將為一個帶有被拋出值的 rejected。

async 函式內部可以使用 [`await`](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/await) 表達式，它會暫停此 async 函式的執行，並且等待傳遞至表達式的 Promise 的解析，解析完之後會回傳解析值，並繼續此 async 函式的執行。



{% hint style="info" %}
[Async function / Await 深度介紹| 卡斯伯Blog - 前端](https://www.casper.tw/development/2020/10/16/async-await/)

`promise` 函式呼叫時可以使用 `then` 來接收 `resolve` 的結果，當要串接兩個 `promise` 函式時可以使用 `return` 來做 “鏈接”。

基於 Promise 的方法相當單純，就是不斷的呼叫 Promise 函式以及使用 `then` 來進行鏈接，`Promise` 可以解決過巢及串接 `callback function` 語法不一致等問題，<mark style="color:red;">但它依然在 JS 的同步語言中插入了一段非同步的片段。</mark>



以 `async` 函式改寫方式如下：

1. 定義非同步函式（`async function`）
2. 透過 `await` 暫停 `promiseFn`，直到回傳後再繼續向下

```
async function getData() {
  const data1 = await promiseFn(1); // 因為 await，promise 函式被中止直到回傳
  const data2 = await promiseFn(2);
  console.log(data1, data2); // 1, 成功 2, 成功
}
getData();
```

結果與使用 `then` 是一致的，但就結構上更加平整，在 這個函式中都是以 “**同步**“ 的方式運行，不會產生同步、非同步程式碼混合的狀況。
{% endhint %}

範例比較

```
function waitASecond(task,second) {
  console.log("waitASecond:"+task);
  return new Promise((resolve, reject) => {
    setTimeout(function () {
      resolve(task);
    }, second);
  });
}

// waitASecond("task1",1000)
//  .then( ()=>{return waitASecond("task2",1000)})  //回傳 new Promise。這邊是非同步片段
//  .then( ()=>{return waitASecond("task3",1000)}) //回傳 new Promise 
//  .then((task) => {
//     console.log("last than:"+task);
//   });
  
const demo = async () => {
    const data1= await waitASecond("task1",1000); //接走resolve內容值
    await waitASecond("task2",1000);  //1
    const data3= await waitASecond("task3",1000);//接走resolve內容值
    console.log(data3);
};
//這樣程式碼看起來比較有waitASecond(0)->waitASecond(1)->waitASecond(2)感

demo();


// 結果 以下都等待一秒才出現
// waitASecond:task1
// waitASecond:task2
// waitASecond:task3
// last than:task3
```

* 註： async的最後如果有return也是可以用demo.than接值, 另外也可以用catch 接錯誤 (跟原概念一樣）

{% hint style="danger" %}
注意，await 一定得運行在 async function 內！await 的錯誤會讓 async 拋出錯誤，而不會造成終止。
{% endhint %}

&#x20;    &#x20;
