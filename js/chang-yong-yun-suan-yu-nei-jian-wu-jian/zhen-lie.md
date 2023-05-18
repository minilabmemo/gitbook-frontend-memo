---
description: 陣列
---

# 陣列

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

### entries

**`entries()`** 方法會回傳一個包含陣列中每一個索引之鍵值對（key/value pairs）的新陣列迭代器（**`Array Iterator`**）物件。

{% hint style="info" %}
**`for...of`语句**在[可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration\_protocols)（包括 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Array)，[`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Map)，[`Set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/Set)，[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/String)，[`TypedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global\_Objects/TypedArray)，[arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions\_and\_function\_scope/arguments) 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句

```jsx
const array1 = ['a', 'b', 'c'];

for (const element of array1) {
  console.log(element);
}
e
```
{% endhint %}



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

[^1]: 
