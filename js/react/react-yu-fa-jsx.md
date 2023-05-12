---
description: 語法
---

# React 語法 JSX

## JSX <a href="#jsx" id="jsx"></a>

看起來是 <mark style="background-color:orange;">**html 與 JS 混合使用，比較接近 JavaScript 而不是 HTML**</mark>，ＪＳＸ允許你使用 JavaScript 所有的功能。

* Ref :[https://zh-hant.reactjs.org/docs/introducing-jsx.html](https://zh-hant.reactjs.org/docs/introducing-jsx.html)

專案產生的public/index.html，含有基本HTML範本id="root"的div區塊

```
<div id="root"></div>
```

### React 中的 JSX 區域 <a href="#react-e4-b8-a-d-e7-9a-84-jsx-e5-8d-80-e5-9f-9f" id="react-e4-b8-a-d-e7-9a-84-jsx-e5-8d-80-e5-9f-9f"></a>

接著看一下src/index.js裡的程式碼

#### 基本範例: ReactDOM.render  <a href="#e5-9f-ba-e6-9c-ac-e7-af-84-e4-be-8b-e7-9b-b4-e6-8e-a5-e6-92-b0-e5-af-abhtml" id="e5-9f-ba-e6-9c-ac-e7-af-84-e4-be-8b-e7-9b-b4-e6-8e-a5-e6-92-b0-e5-af-abhtml"></a>

```diff
由 React DOM 函式將元素渲染 ROOT 這個DOM 節點中
而將 html 當參數傳遞是使用一種Javascript語法: JSX

+// APP是組件
ReactDOM.render(<App />, document.getElementById('root'));

+//或是改成   "將 html 當參數傳遞" 
ReactDOM.render(<h1> Hello world!</h1>,document.getElementById('root'));
```

### 使用變數 const element = \<h1>Hello, {name}\</h1>;&#x20;

```diff
+//一般javascript
const name = 'Josh Perez'; 

+//混和的 html 與字串 特殊JSX語法
const element = <h1>Hello, {name}</h1>;  

+ 把變數丟入render也可以
ReactDOM.render(element,document.getElementById('root'));

```

**關於Babel**

是JavaScript 前處理器，編譯器，主要能轉換JSX與ES6成各瀏覽器支持的ＪＳ

```diff
- const element = (<h1 className="text">Hello, World!</h1>);
+//Babel 將 JSX 編譯為呼叫 React.createElement() 的程式。
+剛剛混用的語法就是以下轉換
+const element = React.createElement('h1', {className: 'text'}, 'Hello, World!');
```

***

### 範例: 在 html中 <mark style="background-color:orange;">用{JS} 表達式崁入變數</mark> <a href="#e7-af-84-e4-be-8b-e5-9c-a8html-e4-b8-a-d-e5-8f-af-e4-bb-a5-e7-94-a8js-e8-a1-a8-e9-81-94-e5-bc-8f-e5" id="e7-af-84-e4-be-8b-e5-9c-a8html-e4-b8-a-d-e5-8f-af-e4-bb-a5-e7-94-a8js-e8-a1-a8-e9-81-94-e5-bc-8f-e5"></a>

```diff
+//js 函式宣告或是變數宣告區
const styleRed = { color: 'red' };

+//html語法可以當作參數傳遞
const pic=()=>{ 
  return (
  <div><img src="https://picsum.photos/200/200?image=229" alt="" class="circle-profile"/></div>);
}
var arr = [
        <h1>REACT學習</h1>,
        <h2>如何使用JSX！</h2>,
];

ReactDOM.render( 
 <React.StrictMode>
   <h1 style = { styleRed } > Hello, world! </h1>
+   <div>{ pic()} </div> {/*註解這樣寫*/}
+   <div>{arr}</div>,{/*可以放入數組*/}
 </React.StrictMode>,
    document.getElementById('root')
);

- 可在 html 標籤中利用 {} 寫 javascript 表示式
- 其中style = {{ color: 'red' }} 這樣的表示也可以。
```

### 範例: 帶入onClick 與 Event <a href="#e7-af-84-e4-be-8b-e5-b8-b6-e5-85-a5-e5-b1-ac-e6-80-a7-e5-91-bd-e5-90-8d-e8-88-87event" id="e7-af-84-e4-be-8b-e5-b8-b6-e5-85-a5-e5-b1-ac-e6-80-a7-e5-91-bd-e5-90-8d-e8-88-87event"></a>

```diff
+const getValue=(event)=>{
+  console.log(event.target.value). //event.target.value
}
ReactDOM.render(
 <React.StrictMode>
    <h1 className = "title" > Hello, world! </h1>
+   <button value onClick={getValue}>按下以取得數值 </button>
+   <button value={true} onClick={getValue}>按下以取得數值 </button>
 </React.StrictMode>,
    document.getElementById('root')
);
```

* 駱駝式命名
  * class 要用 className 然後可以在 style.css中更改樣式
  * onclick 也要改<mark style="background-color:orange;">onClick{函數名稱}</mark>[ ](#user-content-fn-1)[^1]駱駝式命名
  * 實測命名打錯 console 會出現報 Warning: Invalid DOM property `class`. Did you mean `className`?
* <mark style="background-color:red;">輸入類的元件</mark> [<mark style="background-color:red;">button/input/textarea 互動事件觸發時，函式只會接收到一個event類別的參數，並不能傳遞其他參數</mark>](#user-content-fn-2)[^2]
* 布林=true 的屬性值可以不寫

### 範例 JSX 引入Inline-style <a href="#e7-af-84-e4-be-8b-jsx-e5-bc-95-e5-85-a5inline-style" id="e7-af-84-e4-be-8b-jsx-e5-bc-95-e5-85-a5inline-style"></a>

```
export default function App() {
  return (
    <div className="App" style={{
      color: 'blue',fontSize:'19px'
    }}>
    </div>
  );
}

```

* 在style內的是ＪＳ物件也可以把他們只給一個const變數
* 內容與css不同的是必須是小寫駱駝且去除'-'
* 這種寫法的缺點是不行用hover等特殊效果，需利用其他模組化style寫法

## 條件渲染 <a href="#day7-e6-a2-9d-e4-bb-b6-e6-b8-b2-e6-9f-93" id="day7-e6-a2-9d-e4-bb-b6-e6-b8-b2-e6-9f-93"></a>

* 這邊的寫法是根據ＪＳ邏輯運算子與ＪＳＸ寫法

### 範例： CSS 隱藏方式

控制 css style , 可以選擇以下兩種：

* display:none （空間會消失 導致畫面排版「跳一下）
* visibility:hidden（空間會存在）

<pre class="language-diff"><code class="lang-diff">//找到要加的地方 inline style
 &#x3C;div
+  style={{
+    visibility: count >= 10 &#x26;&#x26; 'hidden',
+  }}
  onClick={() => {
    setCount(count + 1);
  }}
/>

//或者寫在className 隱藏元素 --> .vh是先定義到 css裡.  {中是ＪＳ判斷}  
<strong> &#x3C;div
</strong>+  className={`chevron chevron-up ${count >= 10 &#x26;&#x26; 'vh'}`}
  onClick={() => {
    setCount(count + 1);
  }}
/>
</code></pre>

### ＪＳ的邏輯運算子

在 JavaScript 中，&& 或 || 這種語法稱作「[邏輯運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions\_and\_operators#%E9%82%8F%E8%BC%AF%E9%81%8B%E7%AE%97%E5%AD%90)（Expressions - Logical operator）」，而因為在 <mark style="background-color:orange;">JSX 中的 {} 內只能放入表達式（expressions），而不能寫入像是 if...else... 這種陳述句（statement）</mark>

* || 就是前面為假時去拿後面的那個,為真拿前面

```
const a = 0 || 'iPhone'; 
// 因為 0 被轉型後為 false，所以 a 會是 'iPhone'
const b = 26900 || 24900;  
// 因為 26900 會轉型為 true，所以 b 會是 26900
```

* && 就是前面為真時去拿後面的那個,為假拿前面

```
const a = 0 && 'iPhone';   
// 因為 0 被轉型後為 false，所以 a 會是 0
const b = 26900 && 24900;  
// 因為 26900 轉型為 true，所以 b 會是 24900
```

### 範例：使用JSX外層判斷將 DOM整個隱藏方式

如果你需要比較嚴格的去控制使用者的行為，不想要使用者透過 CSS 就能簡單修改的話，那麼就把 DOM 整個移除；但如果這個功能被使用者手動打開也不會有太大影響的話，那就使用 CSS 樣式來控制畫面就好，如此會有比較好的效能和體驗(不會讓畫面排版有抖動的情況)。

```diff
//找到要控制的區塊
+ {count < 10 && (
  <div
    onClick={() => {
      setCount(count + 1);
    }}
  />
+ )}d
```





## 參考 <a href="#e7-b6-b2-e8-b7-af-e5-8f-83-e8-80-83-e6-96-87-e7-ab-a0" id="e7-b6-b2-e8-b7-af-e5-8f-83-e8-80-83-e6-96-87-e7-ab-a0"></a>

* [【React.js入門 - 06】 JSX](https://ithelp.ithome.com.tw/articles/10216468)
* [React篇: JSX語法撰寫指引](https://eyesofkids.gitbooks.io/react-basic-zh-tw/content/day18\_deeper\_jsx/)
* [\[Day 07 - 計數器\] 幫計數器設個最大最小值吧 - JSX 中條件渲染的使用](https://ithelp.ithome.com.tw/articles/10219716)

[^1]: 

[^2]: 
