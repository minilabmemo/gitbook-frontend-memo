---
description: 從aja到fetch
---

# 從AJAX到fetch

## AJAX

{% hint style="info" %}
**非同步 JavaScript 及 XML（Asynchronous JavaScript and XML，AJAX）** 並不能稱做是種「技術」，而是 2005 年時由 Jesse James Garrett 所發明的術語，描述一種使用數個既有技術的「新」方法。這些技術包括 [HTML](https://developer.mozilla.org/zh-TW/docs/Web/HTML) 或 [XHTML](https://developer.mozilla.org/zh-TW/docs/Glossary/XHTML)、[層疊樣式表](https://developer.mozilla.org/zh-TW/docs/Web/CSS)、[JavaScript](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript)、[文件物件模型](https://developer.mozilla.org/zh-TW/docs/Web/API/Document\_Object\_Model)、[XML (en-US)](https://developer.mozilla.org/en-US/docs/Web/XML)、[XSLT (en-US)](https://developer.mozilla.org/en-US/docs/Web/XSLT) 以及最重要的 [`XMLHttpRequest`](https://developer.mozilla.org/zh-TW/docs/Web/API/XMLHttpRequest) 物件。當這些技術被結合在 Ajax 模型中，Web 應用程式便能快速、即時更動介面及內容，不需要重新讀取整個網頁，讓程式更快回應使用者的操作。

是以[XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using\_XMLHttpRequest)物件(簡稱為**XHR**)為主要核心的實作。

它是用於**客戶端對伺服器端送出httpRequest(要求)的物件**，使用的資料格式是XML格式(但後來JSON格式才是最為流行的資料格式)。流程即是建立一個XMLHttpRequest(XHR)物件，打開網址然後送出要求，成功時最後由回調函式處理伺服器傳回的Response(回應)。
{% endhint %}

* [AJAX MDN](https://developer.mozilla.org/zh-TW/docs/Web/Guide/AJAX/Getting\_Started)

```diff
<script>
  (function () {
    var httpRequest;
    document
      .getElementById("ajaxButton")
      .addEventListener("click", makeRequest);

    function makeRequest() {
+      httpRequest = new XMLHttpRequest();

      if (!httpRequest) {
        alert("Giving up :( Cannot create an XMLHTTP instance");
        return false;
      }
+      httpRequest.onreadystatechange = alertContents;
+      httpRequest.open("GET", "test.html");
+      httpRequest.send();
    }

    function alertContents() {
+     if (httpRequest.readyState === XMLHttpRequest.DONE) {
+        if (httpRequest.status === 200) {
檢查傳回的 HTTP 狀態碼後，要怎麼處理傳回的資料就由你決定了
          alert(httpRequest.responseText);
        } else {
          alert("There was a problem with the request.");
        }
      }
    }
  })();
</script>


// JSON的處理
var response = JSON.parse(httpRequest.responseText);
      alert(response.computedString);
```



## jQuery

{% hint style="info" %}
使用像jQuery的函式庫來撰寫AJAX相關功能，**解決不同瀏覽器中的不相容問題，或提供簡化語法**。jQuery它擴充了原有的XHR物件為jqXHR物件，並**加入類似於Promise的介面與Deferred Object(延遲物件)的設計**。
{% endhint %}

```
$.ajax({
    url:'test',//請求的網址
    data:{//請求的資料
        id:'123'
    },
    type: 'GET',//請求的Type
      dataType: 'json',  //資料形式
})
    .done(function(json){//成功時執行
    })
    .fail(function(xhr, status, errorThrown){//失敗時執行
    })
    //不論失敗成功皆執行
    .always(function(xhr, status){

    })
```



## Fetch API

**Fetch**是近年來號稱要取代XHR的新技術標準，它是一個HTML5的API，並非來自ECMAScript標準。



{% hint style="info" %}
[Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch\_API) 提供了一種 JavaScript Interface 來操作 HTTP pipeline，比方 request 和 response。同時它也提供了 global 的 fetch`()` method，使得在網路上非同步地 fetch resources 這件事變得簡單易懂。

* 有點像 `XMLHttpRequest` ，但這個新的 API 提供了更強更彈性的功能。
* &#x20;`fetch` 和 `jQuery.ajax()` 有差異- [Use Fetch](https://developer.mozilla.org/zh-TW/docs/Web/API/Fetch\_API/Using\_Fetch)
* `fetch()` 回傳的 promise <mark style="color:green;">**不會 reject HTTP 的 error status**</mark><mark style="color:blue;">，</mark>就算是 HTTP 404 或 500 也一樣。相反地，它會正常地 resolve，並把 `ok` status 設為 false。<mark style="color:orange;">**會讓它發生 reject 的只有網路錯誤或其他會中斷 request 的情況。**</mark>
* 現今瀏覽器都已自帶 Fetch, 連Library都不用引入就可以使用
{% endhint %}

* <mark style="color:red;">**Fetch API 回傳會是個 Promise 物件**</mark>&#x20;

```
fetch('https://xxx/api/')
    .then((response) => {
        console.log(response); 
    })
    .catch((error) => {
        console.log(`Error: ${error}`);
    })
```

#### 等待多個回傳結果範例：

* <mark style="color:red;">`async/await`</mark> <mark style="color:red;"></mark><mark style="color:red;">函式的目的在於簡化同步操作 promise 的表現(</mark>ES7的寫法，可以讓非同步call back寫法看起來像同步的順序去執行)，以及對多個 `Promise` 物件執行某些操作，可以與promise組合技使用。

{% hint style="info" %}
<mark style="background-color:yellow;">**Promise 是用來優化非同步的語法，解決callback hall**</mark>

<mark style="background-color:yellow;">**而 Async、Await 可以基於 Promise 讓非同步的語法的結構類似於 “同步語言”，更易讀且好管理。**</mark>
{% endhint %}

{% hint style="danger" %}
注意，await 一定得運行在 async function 內！await 的錯誤會讓 async 拋出錯誤，而不會造成終止。
{% endhint %}

* Promise.all()，其背後操作則是使用陣列將多個 promise 函式打包，當全部執行完成後回傳陣列結果。 但是一旦有 Promise 物件失敗，將回傳失敗那個物件回傳的結果

```diff
useEffect(() => {
+    //只要 function 標記為 async，就表示裡頭可以撰寫 await 的同步語法
+   const fetchData = async () => {

+//而 await 顧名思義就是「等待」，它會確保一個 promise 物件都解決或出錯後才會進行下一步，
+// STEP ：使用 Promise.all 搭配 await 組合技 來等待兩個 API 都取得回應後才繼續
+      const data = await Promise.all([
        fetchCurrentWeather(), //Fetch API 改成回傳資料
        fetchWeatherForecast(),//Fetch API 改成回傳資料
      ]);
      
      console.log('data', data);
    };

    // STEP ：呼叫 fetchData 這個方法
    fetchData();
  }, []);
```



#### 在fetch.then中再呼叫另一個fetch

* [https://stackoverflow.com/questions/40981040/using-a-fetch-inside-another-fetch-in-javascript](https://stackoverflow.com/questions/40981040/using-a-fetch-inside-another-fetch-in-javascript)

\-----

##



### reference



[AJAX與Fetch API](https://eyesofkids.gitbooks.io/javascript-start-from-es6/content/part4/ajax\_fetch.html)

[你今天 Promise 了嗎](https://5xruby.tw/posts/promise)&#x20;

[簡單理解 JavaScript Async 和 Await](https://www.oxxostudio.tw/articles/201908/js-async-await.html)

[如何用 Promise 解决回调地狱](https://juejin.cn/post/7065129481513467941) 看起來只是把嵌套回调，修改为了链式调用

