# hook

### `使用hook注意事項`

{% hint style="warning" %}
不能在條件式（conditions）、迴圈（loops）或嵌套函式（nested functions）中呼叫 Hook 方法

換句話說：須注意以 use 開頭的函式不能放在判斷式內，setxxx則是可以在判斷式內使用的

#### 只在 React Function 中呼叫 Hook <a href="#only-call-hooks-from-react-functions" id="only-call-hooks-from-react-functions"></a>
{% endhint %}

* Hook 的規則 [https://zh-hant.reactjs.org/docs/hooks-rules.html](https://zh-hant.reactjs.org/docs/hooks-rules.html)
* ESLint plugin 叫做 `eslint-plugin-react-hooks` 來強制施行這兩個規則(Create React App 預設包含此 plugin)

### `useState`



#### **基本用法**

* **class(setState) vs function(useState)**

React 提供的 Hook－`useState`。我們有時也稱它做「State Hook」。前所未有地，它讓我們能夠增加 local state 到 React function component！

```diff
+// 引入
+ import React, { useState } from 'react';

functidon Example() {
+ // 宣告一個新的 state 變數，我們稱作為「count」。
+ const [count, setCount] = useState(0);
  return (
    <div>
+// 顯示state 變數
+     <p>You clicked {count} times</p>
+// 更變state 變數 觸發重新渲染
+      <button onClick={() => setCount(count + 1)}>
      </button>
    </div>
  );
}
```

#### prevState用法

* **多次呼叫setState方法時，可能會因為前一個狀態未被更新而出現狀態不一的狀況**，這時可以於setState內放入函式更新來獲取prevState，用法如下

```jsx
const [state, setState] = useState({});

setState(prevState => {
  // 也可以使用 Object.assign
  return {...prevState, ...updatedValues};
});
```

> 我覺得這很像data race的情況，setState是非同步的呼叫，因此需要注意資料可能會有不同步的狀況，所以利用**prevState**去解決它．
>
> 參考網路範例說明：
>
> * 在迴圈內使用setState引發錯誤：[React 中的 `setState` 和 `prevState`](https://www.delftstack.com/zh-tw/howto/react/react-setstate-prevstate/#react-%E4%B8%AD%E7%9A%84-setstate-%E5%92%8C-prevstate)
> * 多次使用frech API去setState引發錯誤

### ------------------------



### useEffect

可以把 `useEffect` 視為 `componentDidMount`，`componentDidUpdate` 和 `componentWillUnmount` 的組合。

<mark style="color:blue;">**使用說明**</mark>

```diff
+//引入
import React, { useState, useEffect } from 'react';

useEffect(() => {
+    /*  componentDidMount 和  componentDidUpdate */
    return () => {
+      /* componentWillUnmount */   //在 component unmount 時，React 會執行清除。
    };
    
+}, [dependencies參數]); /* 是用來限定當哪些變數被改變時useEffect要觸發 */

```

* 需注意useEffect內動作與dependencies參數的互動，否則會進入無窮迴圈．
* **`useEffect` 有什麼作用？** 透過使用這個 Hook，你告訴 React 你的 component 需要在 render 後做一些事情。React 將記住你傳遞的 function（我們將其稱為「effect」），並在執行 DOM 更新之後呼叫它。&#x20;

<mark style="color:blue;">**放置的地方**</mark>

```diff
+ import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

+  useEffect(() => {
+    document.title = `You clicked ${count} times`;
+  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```



[官方-hooks-effect](https://zh-hant.reactjs.org/docs/hooks-effect.html) 重點：

* 內有使用class與hook 的範例對比說明

#### 函式該寫進useEffect裡面或外面

* 如果某個函式不需要被覆用，那麼可以直接定義在 useEffect 中
* 需要被覆用,把該方法提到 useEffect 外面後，記得用 useCallback 進行處理後再放到 useEffect 的 dependencies 中，來讓useEffect知道到底有沒有資料狀態的變化（處理不好會陷入無窮迴圈）。

#### 陷入無窮迴圈

你可以藉由一個一個移除依屬 (dependencies) 來發現到底是哪個值。然而，移除一個依屬（或盲目地使用 `[]`）通常是錯誤的修正方式。

應該要修正這個問題的根源。例如，放入函式可能造成這個問題，將它們放到 effects 裡，或抽出他們到上層，或是將他們包在 `useCallback` 裡都可能會有幫助。為了避免重複產生新的物件，`useMemo` 也可以達成類似的目的。

### `useCallback` <a href="#usecallback" id="usecallback"></a>

* 用法與useEffect參數傳遞很像，但會回傳一個memoized 的Callback
* 可以記憶住該 function 的記憶體位置，避免每一次子元件 re-render 時都因為 function 的記憶體位置改變導致子元件重新渲染。

```jsx
import React, { useState, useEffect, useCallback } from 'react';

//傳遞一個 inline callback 及依賴 array。
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b); // inline callback 
  },
  [a, b],//依賴
);
//useCallback 會回傳該 callback 的 memoized 版本，它僅在依賴改變時才會更新。
```

* `useCallback(fn, deps)` 相等於 `useMemo(() => fn, deps)`。

### `useMemo` <a href="#usememo" id="usememo"></a>

* 傳遞一個「建立」function 及依賴 array。`useMemo` 只會在依賴改變時才重新計算 memoized 的值。這個最佳化可以避免在每次 render 都進行**昂貴的計算**。

```javascript
const memoizedValue = useMemo(
() => computeExpensiveValue(a, b)//第一個參數傳入要記住的運算函式
, [a, b]); //第二個參數傳入 dependency array。
```

* 不要濫用，需用在複雜的計算，例如可能要 map 一組很大的陣列，這時候可能就值得運算結果暫記起來下次用。
* <mark style="background-color:yellow;">My Note</mark>: 透過log可以得知有沒有重複計算或是profile可以得知計算速度的減少狀況

#### reference

* [什麼時候該使用 useMemo 跟 useCallback](https://medium.com/ichef/%E4%BB%80%E9%BA%BC%E6%99%82%E5%80%99%E8%A9%B2%E4%BD%BF%E7%94%A8-usememo-%E8%B7%9F-usecallback-a3c1cd0eb520)
* [关于React函数组件的一些日常调试与性能优化技巧](https://juejin.cn/post/6987561807002992677) 待看
