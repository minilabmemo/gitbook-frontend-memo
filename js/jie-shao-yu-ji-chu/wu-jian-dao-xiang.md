---
description: 物件導向
---

# 物件導向





### 物件導向語言與 FP（Functional Programming）？ <a href="#javascript" id="javascript"></a>

{% hint style="info" %}
### JavaScript 是一種物件導向語言嗎？ <a href="#javascript" id="javascript"></a>

JavaScript 是個特殊的語言，嚴格說起來它是基於原型 Prototype-based[^1] 的語言，但它**寫起來有 FP（Functional Programming）的味道，卻也可以「假裝」成物件導向語言**

[我要學會JS(一)：JavaScript 簡介](https://noob.tw/javascript-introduction/)
{% endhint %}

* 因為 Javascript 中的特性，根本上基本都是物件，並沒有 class 的概念，所以使用原型的概念來做出類似 類別(class) 的方法。
* 在 Java 是屬於 **類別繼承，**在類別裡會有個很特別的函式叫做「建構函式」，他會進行實例的初始化，用來設定一些實例的基礎屬性。而 Javascript 則是屬於 **原型繼承**
*

### **原型鏈**

* &#x20;[繼承與原型鏈 mozilla](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Inheritance\_and\_the\_prototype\_chain)
* [原型繼承與原型鏈 ｜ALPHA Camp](https://javascript.alphacamp.co/prototype-prototype-chain.html)
* JavaScript 就只有一個建構子：物件。每個物件都有一個連著其他**原型**（prototype）的私有屬性（private property）物件。原型物件也有著自己的原型，於是原型物件就這樣鏈結，**直到撞見 `null` 為止：`null` 在定義裡沒有原型、也是原型鏈（**prototype chain）的最後一個鏈結。
* JavaScript 物件是一「包」動態的屬性（也就是**它自己**的屬性）並擁有一個原型物件的鏈結，當物件試圖存取一個物件的屬性時，其不僅會尋找該物件，也會尋找該物件的原型、原型的原型……直到找到相符合的屬性，或是到達原型鏈的尾端。
* ES6 開始就有了 `Class` 語法可以使用，但本質上還是原型
* new 後面其實就是一個函式
  * 有沒有ｎｅｗ的差別以及this可以看這篇[\[JavaScript\] new的用法與基本概念](https://dotblogs.com.tw/acelee/2017/06/22/135553)

<mark style="background-color:red;">找不到本身的屬性</mark><mark style="background-color:red;">**才會**</mark><mark style="background-color:red;">往.prototype上屬性找</mark>

```javascript
// 利用含有 a 與 b 屬性的 f 函式，建立一個 o 物件：
let f = function () {
  this.a = 1;
  this.b = 2;
};
let o = new f(); // {a: 1, b: 2}

// 接著針對 f 函式的原型添加屬性
f.prototype.b = 3;
f.prototype.c = 4;

// 不要寫 f.prototype = {b:3,c:4}; 因為它會破壞原型鏈
// o.[[Prototype]] 有 b 與 c 的屬性：{b: 3, c: 4}
// o.[[Prototype]].[[Prototype]] 是 Object.prototype.
// 最後 o.[[Prototype]].[[Prototype]].[[Prototype]] 成了 null
// 這是原型鏈的結末，因為 null 按照定義並沒有 [[Prototype]]。
// 因此，整個原型鏈看起來就像：
// {a: 1, b: 2} ---> {b: 3, c: 4} ---> Object.prototype ---> null

console.log(o.a); // 1
// o 有屬性「a」嗎？有，該數值為 1。

console.log(o.b); // 2
// o 有屬性「b」嗎？有，該數值為 2。
// o 還有個原型屬性「b」，但這裡沒有被訪問到。
// 這稱作「property shadowing」。

console.log(o.c); // 4
// o 有屬性「c」嗎？沒有，那就找 o 的原型看看。
// o 在「o.[[Prototype]]」有屬性「c」嗎？有，該數值為 4。

console.log(o.d); // undefined
// o 有屬性「d」嗎？沒有，那就找 o 的原型看看。
// o 在「o.[[Prototype]]」有屬性「d」嗎？沒有，那就找 o.[[Prototype]] 的原型看看。
// o.[[Prototype]].[[Prototype]] 是 Object.prototype，預設並沒有屬性「d」，那再找他的原型看看。
// o 在「o.[[Prototype]].[[Prototype]].[[Prototype]]」是 null，停止搜尋。
// 找不到任何屬性，回傳 undefined。
```



###

###







#### 沒有用new是呼叫函示，有用new是建構函式嗎

在 JavaScript 中，我們使用 `new` 來呼叫一個函數，通常是用來創建一個新的物件實例。這種特殊的函數通常被稱為構造函數（Constructor Function）。

當使用 `new` 關鍵字來調用一個函數時，它會執行以下步驟：

1. 創建一個空的物件。
2. 設置該物件的 `[[Prototype]]` 屬性為構造函數的 `prototype` 屬性。
3. 將構造函數的 `this` 綁定到剛剛創建的物件。
4. 執行構造函數，並將 `this` 作為新創建的物件返回值。

這樣，使用 `new` 關鍵字創建的實例具有構造函數定義的屬性和方法。

以下是一個示例：

```javascript
// 定義構造函數
function Animal(name) {
    this.name = name;
}

// 使用 new 關鍵字創建實例
var myAnimal = new Animal("Cat");

console.log(myAnimal.name); // 輸出: Cat
```

如果在創建實例時沒有使用 `new`，那麼該函數將被視為一個普通的函數調用，並且 `this` 的值將取決於它被調用的上下文。這可能導致意外的行為，因為沒有創建新的物件實例。

簡而言之，`new` 用來標記函數的調用方式，指示該函數應該用作構造函數，創建新的實例。

[^1]: 
