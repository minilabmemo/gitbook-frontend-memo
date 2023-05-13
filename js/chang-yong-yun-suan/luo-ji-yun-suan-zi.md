# 邏輯運算子

### ＪＳ的邏輯運算子

在 JavaScript 中，&& 或 || 這種語法稱作「[邏輯運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions\_and\_operators#%E9%82%8F%E8%BC%AF%E9%81%8B%E7%AE%97%E5%AD%90)（Expressions - Logical operator）」

通常被用於布林(邏輯)值; 使用於 布林(邏輯)值時， 它們會回傳布林型態的值。 然而，<mark style="color:red;">`&&`</mark> <mark style="color:red;"></mark><mark style="color:red;">和</mark> <mark style="color:red;"></mark><mark style="color:red;">`||`</mark> <mark style="color:red;"></mark><mark style="color:red;">運算子實際上是回傳兩指定運算元之一，因此用於非布林型態值時，它可能會回傳一個非布林型態的值</mark>。 邏輯運算子將在下表中被詳細解釋。

輯運算子將在下表中被詳細解釋。

| Operator                                                                                                  | Usage            | Description                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [邏輯 AND](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators#logical\_and) (`&&`) | `運算式1 && 運算式2`   | <p>假如 <code>運算式1</code> 可以被轉換成 false 的話，回傳 <code>運算式1</code>; 否則，回傳 <code>運算式2</code>。 </p><p></p><p>因此，<code>&#x26;&#x26;</code>只有在 兩個運算元都是 True 時才會回傳 True，否則回傳 <code>false</code>。</p> |
| [邏輯 OR](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators#logical\_or) (`\|\|`) | `運算式1 \|\| 運算式2` | <p>假如 <code>運算式1</code> 可以被轉換成 true 的話，回傳 <code>運算式1</code>; 否則，回傳 <code>運算式2</code>。 </p><p></p><p>因此，<code>||</code>在 兩個運算元有任一個是 True 時就會回傳 True，否則回傳 <code>false</code>。</p>           |
| [邏輯 NOT](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators#logical\_not) (`!`)  | `!運算式`           | 假如單一個運算元能被轉換成 True 時，回傳`false` ， 不然回傳 `true`。                                                                                                                                             |

可以被轉換為 false 的運算式是 null， 0， NaN， 空字串 ("")，或 未定義。



* && 就是前面為真時去拿後面的那個,為假拿前面

<pre class="language-diff"><code class="lang-diff">+ // 邏輯判斷子其實是回傳某一個值
const a = 0 &#x26;&#x26; 'iPhone';  
console.log("a:" +a );  //a:0   
// 因為 0 被轉型後為 false，所以 a 會是 0
const b = 26900 &#x26;&#x26; 24900;  
// 因為 26900 轉型為 true，所以 b 會是 24900


<strong>+// 放進if 裡看起來的結果
</strong>if ( 0 &#x26;&#x26; 'iPhone'){
    console.log(`判斷真 ${0 &#x26;&#x26; 'iPhone' } `);
}else{
      console.log(`判斷假  ${0 &#x26;&#x26; 'iPhone' } `); // 判斷假  0 
}
</code></pre>



* || 就是前面為假時去拿後面的那個,為真拿前面

```
const a = 0 || 'iPhone'; 
// 因為 0 被轉型後為 false，所以 a 會是 'iPhone'
const b = 26900 || 24900;  
// 因為 26900 會轉型為 true，所以 b 會是 26900
```

