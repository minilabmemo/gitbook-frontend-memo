---
description: 介紹
---

# 介紹

### **直譯式** (**interpreted** )與\*\*編譯式 (compiled)\*\*

JavaScript 是直譯式語言。在直譯式程式語言中，程式碼由上到下執行，而且執行的結果是立即回應得到的。在瀏覽器執行前，你不需要將程式轉換為其它的形式。程式碼的內容是以對程式人員友善的形式並直接能夠運作。大多數現代的 JavaScript 直譯器實際上會使用一種稱為\*\*即時編譯（just-in-time compiling）\*\*的技術來提升執行表現。 JavaScript 被使用時，原始程式會被編譯成更快的二進位格式，讓它們能更有效率的運行。然而，[ <mark style="color:red;">JavaScript 仍然被認為是一種直譯式的程式語言，因為編譯動作是在程式運作時，而不是事先完成。</mark>](#user-content-fn-1)[^1]



### 物件導向語言與 FP（Functional Programming）？ <a href="#javascript" id="javascript"></a>

{% hint style="info" %}
### JavaScript 是一種物件導向語言嗎？ <a href="#javascript" id="javascript"></a>

JavaScript 是個特殊的語言，嚴格說起來它是基於原型 Prototype-based[^2] 的語言，但它寫起來有 FP（Functional Programming）的味道，卻也可以「假裝」成物件導向語言

[我要學會JS(一)：JavaScript 簡介](https://noob.tw/javascript-introduction/)
{% endhint %}

* 因為 Javascript 中的特性，根本上基本都是物件，並沒有 class 的概念，所以使用原型的概念來做出類似 類別(class) 的方法。
* 在 Java 是屬於 **類別繼承，**在類別裡會有個很特別的函式叫做「建構函式」，他會進行實例的初始化，用來設定一些實例的基礎屬性。而 Javascript 則是屬於 **原型繼承**
*

### **原型鏈**

* &#x20;[繼承與原型鏈 mozilla](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Inheritance\_and\_the\_prototype\_chain)
* [原型繼承與原型鏈 ｜ALPHA Camp](https://javascript.alphacamp.co/prototype-prototype-chain.html)
* JavaScript 就只有一個建構子：物件。每個物件都有一個連著其他**原型**（prototype）的私有屬性（private property）物件。原型物件也有著自己的原型，於是原型物件就這樣鏈結，直到撞見 `null` 為止：`null` 在定義裡沒有原型、也是**原型鏈**（prototype chain）的最後一個鏈結。
* JavaScript 物件是一「包」動態的屬性（也就是**它自己**的屬性）並擁有一個原型物件的鏈結，當物件試圖存取一個物件的屬性時，其不僅會尋找該物件，也會尋找該物件的原型、原型的原型……直到找到相符合的屬性，或是到達原型鏈的尾端。
* ES6 開始就有了 `Class` 語法可以使用，但本質上還是原型



### runtime 環境

不同的 runtime 會提供不同的東西，你要很清楚現在是在哪個 runtime

* JavaScript 需要有地方執行，而這個地方就叫做執行環境（runtime），舉個例子，大家最常用的 runtime 就是「瀏覽器」。做的功能自然而然就會受到瀏覽器限制 （資安CORS等等）
* 除了瀏覽器以外，JavaScript 還有另一個 runtime 叫做 Node.js，JavaScript 程式碼可以脫離瀏覽器執行

{% hint style="info" %}
[從「為什麼不能用這個函式」談執行環境（runtime）](https://blog.huli.tw/2022/02/09/javascript-runtime/)

* JavaScript 是在瀏覽器這個 runtime 上執行的，而這個 runtime 會提供給你一些東西使用，例如說 <mark style="color:red;">**DOM（document）、**</mark><mark style="color:red;">**`console.log`**</mark><mark style="color:red;">**、**</mark><mark style="color:red;">**`setTimeout`**</mark><mark style="color:red;">**、**</mark><mark style="color:red;">**`XMLHttpRequest`**</mark> 或是 `fetch`，這些其實[<mark style="color:orange;">**都不是 JavsScript（或是更精確地說，ECMAScript）的一部分。**</mark>](#user-content-fn-3)[^3]

> 以 `atob` 為例，[MDN](https://developer.mozilla.org/en-US/docs/Web/API/atob#specifications) 下方 Specifications 的段落中，你可以看見它的出處是 HTML Standard，並不是 ECMAScript，就代表它並不是 ECMAScript 的一部分

* 當你在使用 JavaScript 時，有些 API 是這個語言本身內建的，例如說 `JSON.parse` 或是 `Promise`，你可以在 ECMAScript 的規格書中找到他們的說明。
* 而有些 API 則是 runtime 提供的，例如說 `atob`、`localStorage` 或是 `document`，就是瀏覽器所提供的 API，一旦脫離了瀏覽器這個 runtime，你就沒有這些 API 可以用。
{% endhint %}

&#x20;

## debug

### 對 JS debug 對 JS <a href="#e5-b0-8d-js-debug-e5-b0-8d-js" id="e5-b0-8d-js-debug-e5-b0-8d-js"></a>

* 先安裝 JavaScript Debugger (Nightly), 後續會用到 node js
* vscode 說明 [Debugging](https://code.visualstudio.com/docs/editor/debugging), 他是教用`${workspaceFolder}\\app.js`
  * 但這樣會報以下錯誤

```
Note: Using the "preview" debug extension
/usr/local/bin/node ./../simple_js_demo\app.js
Process exited with code 1
Uncaught Error Error: Cannot find module '/Users/yiyin/dev/front/javascript/simple_js_demo\app.js'
    at Module._resolveFilename (<node_internals>/internal/modules/cjs/loader.js:885:15)
    at Module._load (<node_internals>/internal/modules/cjs/loader.js:730:27)
    at executeUserEntryPoint (<node_internals>/internal/modules/run_main.js:72:12)
    at <anonymous> (<node_internals>/internal/main/run_main_module.js:17:47)
```

* [variables-reference](https://code.visualstudio.com/docs/editor/variables-reference)
  * ${workspaceFolder} - 在 VS Code 中打開的文件夾的路徑
  * ${fileDirname} - 當前打開文件的文件夾路徑

launch.json 設定如下

* 第一種是要自己先執行,再按下 debug 先開啟瀏覽器,這種方式我覺得跟 debug html 在瀏覽器差不多,有點麻煩
* 第二種 是多資料夾下的`app.js`, 我習慣用這個來執行不同資料夾下的 JS
* 第三種 是本地資料夾放的`app.js`

```
{
  // 使用 IntelliSense 以得知可用的屬性。
  // 暫留以檢視現有屬性的描述。
  // 如需詳細資訊，請瀏覽: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "對 localhost 啟動 Chrome",
      "url": "http://localhost:8080",
      "webRoot": "${workspaceFolder}"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Open JS",
      "program": "${fileDirname}/app.js"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Program ROOT JS",
      "program": "app.js"
    }
  ]
]
}
```

\




[^1]: 

[^2]: 

[^3]: 
