---
description: 介紹
---

# 介紹

### **直譯式** (**interpreted** )與\*\*編譯式 (compiled)\*\*

JavaScript 是直譯式語言。在直譯式程式語言中，程式碼由上到下執行，而且執行的結果是立即回應得到的。在瀏覽器執行前，你不需要將程式轉換為其它的形式。程式碼的內容是以對程式人員友善的形式並直接能夠運作。大多數現代的 JavaScript 直譯器實際上會使用一種稱為\*\*即時編譯（just-in-time compiling）\*\*的技術來提升執行表現。 JavaScript 被使用時，原始程式會被編譯成更快的二進位格式，讓它們能更有效率的運行。然而，[ <mark style="color:red;">JavaScript 仍然被認為是一種直譯式的程式語言，因為編譯動作是在程式運作時，而不是事先完成。</mark>](#user-content-fn-1)[^1]



### 物件導向語言與 FP（Functional Programming）？ <a href="#javascript" id="javascript"></a>

{% hint style="info" %}
### JavaScript 是一種物件導向語言嗎？ <a href="#javascript" id="javascript"></a>

JavaScript 是個特殊的語言，嚴格說起來它是 Prototype-based[^2] 的語言，但它寫起來有 FP（Functional Programming）的味道，卻也可以「假裝」成物件導向語言

[我要學會JS(一)：JavaScript 簡介](https://noob.tw/javascript-introduction/)
{% endhint %}



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



[^1]: 

[^2]: 

[^3]: 
