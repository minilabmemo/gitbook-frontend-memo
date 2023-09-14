---
description: 操作
---

# 陣列與物件

## 遍尋陣列的方法

*   [JavaScript 遍歷 Array 的四種方法：for、for-in、for-of、forEach()](https://tigercosmos.xyz/post/2021/06/js/js-array-for-methods/)

    * 寫得很好，還有性能分析



### for迴圈

可以用continue,break,性能最好

### forEach

* (ES5) for的優化寫法
* 無法用continue,要換成return
* break可用flag自己控制或是用some(),every()取代，有些人會建議用for迴圈清楚點

### for-in

* (ES1) 拿到key值,但是拿到的非數字而是字串,性能差

### for-of

* 直接得到陣列元素
* 外加 `for` 可以用 `break`、`continue` 做到更彈性操作
* &#x20;`for-of` 也可以直接用來遍歷物件
* 效能稍差於for，但可以做到很多事，有些人偏好這種寫法

{% hint style="info" %}
**`for...of`语句**在[可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration\_protocols)（包括 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Array)，[`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Map)，[`Set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Set)，[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/String)，[`TypedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/TypedArray)，[arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions\_and\_function\_scope/arguments) 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句

```jsx
const array1 = ['a', 'b', 'c'];

for (const element of array1) {
  console.log(element);
}

```
{% endhint %}

<pre class="language-javascript"><code class="lang-javascript">
//只想拿取元素
const arr = ['a', 'b', 'c'];
arr.prop = 'property value';

for (const elem of arr) {
  console.log(elem);
}
// Output:
// 'a'
// 'b'
// 'c'

//同時想要 Array 的 Index &#x26; Value 
<strong>const arr = ['chocolate', 'vanilla', 'strawberry'];
</strong>
for (const [index, value] of arr.entries()) {
  console.log(index, value);
}
// Output:
// 0, 'chocolate'
// 1, 'vanilla'
// 2, 'strawberry'

//物件
const myMap = new Map()
  .set(false, 'no')
  .set(true, 'yes');

for (const [key, value] of myMap) {
  console.log(key, value);
}

// Output:
// false, 'no'
// true, 'yes'
</code></pre>

##

## **Object.entries()**

* Object.entries(obj)**.XXX** 取得所有 property 的 name 和 value，並以陣列回傳

```javascript
const object1 = {
  a: ["somestring",123],
  b: 42
};

console.log(object1);   //obj
console.log(Object.entries(object1)); //轉成陣列


for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}

//> Object { a: Array ["somestring", 123], b: 42 }
//> Array [Array ["a", Array ["somestring", 123]], Array ["b", 42]]
//> "a: somestring,123"
//> "b: 42"


```

## ARRAY對象

### Array.prototype.push()/pop()

**`push()`** 方法會添加一個或多個元素至陣列的末端，並且回傳陣列的新長度。

**`pop()`** 方法會移除並回傳陣列的**最後一個**元素。此方法會改變陣列的長度。

```
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// Expected output: 4
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// Expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]

```

###

### entries

**`entries()`** 方法會回傳一個包含陣列中每一個索引之鍵值對（key/value pairs）的新陣列迭代器（**`Array Iterator`**）物件。

#### 常與for-of做使用

```
var a = ["a", "b", "c"];
var iterator = a.entries();

for (let e of iterator) {
  console.log(e);
}
// [0, 'a']
// [1, 'b']
// [2, 'c']
```



### map

**`map()`** 方法會建立一個[<mark style="color:red;">新的陣列</mark>](#user-content-fn-1)[^1]，其內容為原陣列的每一個元素經由回呼函式運算後所回傳的結果之集合。

```
const array1 = [ {
    name: 'andy',
    age: 10
  },
  {
    name: 'amy',
    age: 23
  },
  {
    name: 'lisa',
    age: 30
  }];

const map1 = array1.map((location) => location.name);
console.log(map1);//[ 'andy', 'amy', 'lisa' ]
```

### filer

* **`filter()`** 方法會建立一個經指定之函式運算後，由原陣列中通過該函式檢驗之元素所構成的<mark style="color:red;">新陣列</mark>。
* var newArray = arr.filter(callback(element\[, index\[, array]])\[, thisArg])

```diff
+//範例一: 選出字數大於六的
const words = ["spray", "limit", "elite", "exuberant", "destruction", "present", "happy"];
let longWords = words.filter(word => word.length > 6);

+// 範例二：選出裡面item.key符合條件的
var people = [
  {name: 'Amy', id: '1',age: 18},
  {name: 'Cindy', id: '2', age: 24},
  {name: 'Lily', id: '3',age: 1}
];
var filterAgeThan5 = people.filter(function(item, index, array){
  return item.age > 5;       // 取得大於五歲的
});
console.log(filterAgeThan5); // Amy, Cindy 這兩個物件
```

### `reduce`

* `reduce()` 將數組元素計算為一個值（從左到右），會對每一個目前迭代到的陣列元素（除了空值以外），**可以與前一個回傳的值再次作運算**執行 `callback` 函式，回呼函式會接收四個參數
* 語法

```jsx
arr.reduce(callback[accumulator, currentValue, currentIndex, array], initialValue)
陣列.reduce(回調函數[累積,目前值,目前陣列,陣列],初始值) 這個陣列可以再指派出去。
```

* accumulator 是累加值，若在呼叫 `reduce()` 時有提供 `initialValue`，則 `accumulator` 將會等於 `initialValue`，且 `currentValue` 會等於陣列中的第一個元素值；若沒有提供 `initialValue`，則 `accumulator` 會等於陣列的第一個元素值，且 `currentValue` 將會等於陣列的第二個元素值。
* currentValue/currentIndex是裡面的物件
* <mark style="color:red;">**currentIndex, array 不一定要給，除非需要，很常看到省略**</mark>

#### 範例

#### [計算相同元素數量並以物件鍵值顯示](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global\_Objects/Array/Reduce#%E8%A8%88%E7%AE%97%E7%9B%B8%E5%90%8C%E5%85%83%E7%B4%A0%E6%95%B8%E9%87%8F%E4%B8%A6%E4%BB%A5%E7%89%A9%E4%BB%B6%E9%8D%B5%E5%80%BC%E9%A1%AF%E7%A4%BA) 這個範例就很像是把array變成累積map去做計算便回傳拿到結果 <a href="#ji-suan-xiang-tong-yuan-su-shu-liang-bing-yi-wu-jian-jian-zhi-xian-shi" id="ji-suan-xiang-tong-yuan-su-shu-liang-bing-yi-wu-jian-jian-zhi-xian-shi"></a>



### Array.prototype.every()

**`every()`** 方法测试一个数组内的所有元素是否都能通过指定函数的测试。它返回一个布尔值。

```
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// Expected output: true

```

### Array.prototype.some()

**`some()`** 方法测试数组中是否至少有一个元素通过了由提供的函数实现的测试。如果在数组中找到一个元素使得提供的函数返回 true，则返回 true；否则返回 false。它不会修改数组。

* 检测在数组中是否有元素大于 10之類的條件。

```
const array = [1, 2, 3, 4, 5];

// Checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// Expected output: true

```

### Array.prototype.includes()

**`includes()`** 方法用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 `true`，否则返回 `false`。

```
//語法
includes(searchElement)
includes(searchElement, fromIndex)

const array1 = [1, 2, 3];

console.log(array1.includes(2));
// Expected output: true
[1, 2, 3].includes(2); // true
[1, 2, 3].includes(4); // false
[1, 2, 3].includes(3, 3); // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
["1", "2", "3"].includes(3); // false


//你可以在稀疏数组中搜索 undefined，得到 true 。
console.log([1, , 3].includes(undefined)); // true
```

#### [在非数组对象上调用 includes() 方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Array/includes#%E5%9C%A8%E9%9D%9E%E6%95%B0%E7%BB%84%E5%AF%B9%E8%B1%A1%E4%B8%8A%E8%B0%83%E7%94%A8\_includes\_%E6%96%B9%E6%B3%95) <a href="#zai-fei-shu-zu-dui-xiang-shang-tiao-yong-includes-fang-fa" id="zai-fei-shu-zu-dui-xiang-shang-tiao-yong-includes-fang-fa"></a>

[^1]: 
