---
description: 物件
---

# 物件

#### Immutable object 不可變物件

* 如 JavaScript 的原始型別 number、string、null、undefined、boolean 等,
* <mark style="color:green;">array的.map,.filter都會產生新陣列(MDN)</mark>

#### Mutable object 可變物件

* 如 JavaScript 的參考型別 [<mark style="color:red;">Object、Array的 push,pop,sort等會直接改變原本</mark>](#user-content-fn-1)[^1]、Function 等



### 範例：物件傳參（可變物件）

<pre class="language-diff"><code class="lang-diff">var a = {};
// 指派一個空物件(一個記憶體位置)
var b = a;
-var c = b = { number: 1 };
// c指向b, b 指向新的物(另一個記憶體位置)
<strong>-c.name = ‘foo’;
</strong>console.log(a);
-console.log(b);
console.log(c)
結果
{}
-{ number: 1, name: ‘foo’ }
+{ number: 1, name: ‘foo’ }
</code></pre>

* &#x20;<mark style="color:red;">發現改變了c 就讓b一起改變了</mark> 对象在 JavaScript 中是引用传递的 可變的
* 共用同一個記憶體想當然只要有一方的值改變了另一方也會跟著改變，這個就叫做淺拷貝。

### 範例：物件傳參的例外 是用**pass by sharing**

如果是真的 call by reference，那你在 function 裡面把 obj 的值改掉了，外面的 o 也會一起被改掉，變成那個新的 object，可是從上面這段範例看起來並沒有，所以這樣做不是 call by reference。

```
var coin1 = { value: 10 };

function changeValue(obj) {
  // 讓 obj 變成一個新的 object
  // 僅更新 obj.value，並未重新賦值
  obj.value = 123;
}

changeValue(coin1);
console.log(coin1);   // 此時 coin1 則會變成 { value: 123 }
```

* 所以我說那個 JavaScript 是「傳值」或「傳址」呢 基本型別是「傳值」，而物件型別會是「傳址」的方式，但**凡事都有例外**JavaScript 應該屬於透過 **pass by sharing**。
* 「Pass by sharing」的特點在於，當 `function` 的參數，如 `function changeValue(obj){ ... }` 中的 `obj` 被重新賦值的時候，外部變數的內容是不會被影響的。

### 解決物件拷貝

當物件改變時，兩個變數都會被影響, 如果希望複製一個物件,更改時不會影響原本物件

#### 可以透過 `Object.assign`

* 這種方法只影響第一層物件看起來像是深拷貝，但[<mark style="color:red;">第二層還是淺拷貝,所以它還是淺拷貝</mark>](#user-content-fn-2)[^2]

<pre class="language-diff"><code class="lang-diff">let obj1 = {
  name: 'bar'
}
<strong>-//let obj2 =  obj1
</strong>+let obj2 = Object.assign({}, obj1) //物件拷貝
obj1.name = 'changed'

console.log(obj1.name)//changed
+console.log(obj2.name) // bar。這樣就不會互相影響了 否則可能會是changed
</code></pre>

使用 ES9 的物件展開運算子

```
let obj1 = {
  foo: 'bar'
}
let obj2 = { ...obj1 }
obj1.foo = 'changed'
console.log(obj2.foo) // bar
```

{% hint style="warning" %}
但如果物件中屬性的值也是物件，這樣的方法就只能複製到第一層物件的屬性，而無法複製到屬性值的物件；因此我們將這樣的複製方法稱為「淺拷貝」
{% endhint %}

#### 深拷貝  `JSON.stringify` 及 `JSON.parse`&#x20;

```diff
let obj1 = {
  foo: 'bar',
  arr: [0, 1]
}
let obj2 = { ...obj1 }
+let obj3 = JSON.parse(JSON.stringify(obj1))
obj1.foo = 'changed'
obj1.arr[0] = 99

+console.log(obj2.foo) // bar//淺拷貝
-console.log(obj2.arr) // [99, 1] //淺拷貝

+console.log(obj3.foo) // bar//深拷貝
+console.log(obj3.arr) // [0, 1] //深拷貝 不被影響
```

#### 關於ＪＳ的call by sharing討論

{% hint style="info" %}
[深入探討JavaScript 中的參數傳遞：call by value ... - Huli's blog](https://blog.huli.tw/2018/06/23/javascript-call-by-value-or-reference/)\


依據細分程度的不同，下面幾句話都是正確的：

1. JavaScript 裡面只有 pass by value
2. JavaScript 的 primitive type 是 pass by value，object 是 pass by sharing

\
[14. \[JS\] 深拷貝是什麼？如何實現？ - iT 邦幫忙](https://ithelp.ithome.com.tw/articles/10223178)
{% endhint %}



#### 延伸 J

S大坑之数据超过2的53次方引发的Number型精度丢失问题

* [JS之路 Day27- JSON Methods(JSON 方法)](https://ithelp.ithome.com.tw/articles/10307819?sc=iThelpR)
  * 第一`JSON`它只能用雙引號，不能用單引號，不論是`key`還是`value`，物件沒有這種限制，可以用單引號，甚至`key`不要加引號也沒有關係。
  * 第二`JSON` 支持 `object`、`array`、`string`、`number`、`boolean` 和 `null`，基本上除了`undefined`之外其他全包了

[^1]: 

[^2]: 
