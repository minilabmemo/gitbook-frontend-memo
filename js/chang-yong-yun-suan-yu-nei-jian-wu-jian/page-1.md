# Page 1

### 解決物件拷貝

當物件改變時，兩個變數都會被影響, 如果希望複製一個物件,更改時不會影響原本物件

#### 可以透過 `Object.assign`

* 這種方法只影響第一層物件看起來像是深拷貝，但[<mark style="color:red;">第二層還是淺拷貝,所以它還是淺拷貝</mark>](#user-content-fn-1)[^1]

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



#### Immutable object 不可變物件

* 如 JavaScript 的原始型別 number、string、null、undefined、boolean 等,
* <mark style="color:green;">array的.map,.filter都會產生新陣列(MDN)</mark>

#### Mutable object 可變物件

* 如 JavaScript 的參考型別 [<mark style="color:red;">Object、Array的 push,pop,sort等會直接改變原本</mark>](#user-content-fn-2)[^2]、Function 等

[^1]: 

[^2]: 
