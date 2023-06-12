# React + typescript

## 建立專案

方式一：用create-react-app + --template typescript

```
npm install -g create-react-app 
//有裝過可以不用跑
create-react-app pet-finder-tw --template typescript
//要注意後方是否正確 否則可能回出現非ts版本的專案

```

{% hint style="info" %}
TypeScript 編寫的檔案都以 `.ts` 為字尾，如果是用 TypeScript 編寫 React 時，以 `.tsx` 為字尾。

上述這樣產生出來的檔案會是index.tsx與 App.tsx
{% endhint %}

### 專案結構

在 `public` 資料夾中主要是放靜態檔案，也就是不需要再經過任何前處理（preprocess）或編譯（compile）的檔案。

*   對於要構建的項目，**這些文件必須以確切的文件名存在**：

    * `public/index.html`是頁面模板；
    * `src/index.js`是 JavaScript 入口點。

    您可以刪除或重命名其他文件。

    你可以在裡面創建子目錄`src`。為了更快地重建，`src`webpack 只處理其中的文件。您需要將**任何 JS 和 CSS 文件放入其中`src`**，否則 webpack 將看不到它們。



##



## 開始撰寫

`:type` 或是 `?:type` (非必填)

### 範例 props type的改法

```diff

const element = <ChildComponent firstName="Aaron" lastName="Chen" />;

interface FooProps {
  firstName: string;
  lastName: string
  // children: React.ReactNode;  //待研究
}


// 透過解構賦值把 props 內需要用到的變數取出
- function ChildComponent(props).  // 這邊會跳出毛毛蟲
- function ChildComponent(props: any) { 不要這樣寫
+ function ChildComponent(props: { firstName: string, lastName: string }) { 
+ function ChildComponent(props: FooProps) {
  const { firstName, lastName } = props;
  return <h1>Hello, {firstName} {lastName}</h1>;    // Hello, Aaron Chen
}


```



ref : [\[掘竅\] 了解這些，更快掌握 TypeScript 在 React 中的使用（Using TypeScript in React）](https://pjchender.blogspot.com/2020/07/typescript-react-using-typescript-in.html)\


### React.ReactNode

範例

<pre class="language-diff"><code class="lang-diff">
var items = [
    {
      name: "Random Name #1",
      description: "Probably the most random thing you have ever seen!",
      image: undefined,
      imageNode:
<strong>+       &#x3C;img alt="stack overflow" src={main_img_1}>&#x3C;/img>
</strong>
    },
    {
      name: "Random Name #2",
      description: "Hello World!",
      image: '',
      imageNode: &#x3C;>
        &#x3C;img alt="stack overflow" src={'https://picsum.photos/id/22/900/325'}>&#x3C;/img>
      &#x3C;/>
    },
    {
      name: "Random Name #3",
      description: "Hello World!",
      image: 'https://picsum.photos/id/123/900/325',
      imageNode: &#x3C;img alt="stack overflow" src={''}>&#x3C;/img>
    }
  ]



{
        items.map((item, i) => &#x3C;Item key={i} item={item} />)
      }

`
function Item(props: { 
item: { name: string; description: string; image: string | undefined;
+ imageNode: React.ReactNode }; }) {
  return (
    &#x3C;Paper sx={{
      width: "1000px",
      margin: "0 auto",/*TBD not woerked */
      boxShadow: '0 0px 0px #ccc', /*close boxShadow */

    }}>
      {/* {props.item.image != undefined ? (&#x3C;img src={props.item.image} alt={props.item.name} width="100%" >&#x3C;/img>) : ({ props.item.imageNode })} */}
      {/* {props.item.imageNode} */}
      {props.item.image !== undefined &#x26;&#x26; props.item.image !== '' ? (

        &#x3C;img src={props.item.image} alt={props.item.name} width="100%" >&#x3C;/img>

      ) : (
        &#x3C;>
+         {props.item.imageNode}
        &#x3C;/>
      )}
      
+ {props.item.imageNode}
    &#x3C;/Paper>
  )
}
```

</code></pre>

### css-in-js. & MAP參數範例

* const XXXWrapper = styled.div 裡面沒有用到參數就不管
* const XXXWrapper = styled.div<mark style="background-color:blue;">\<T></mark>\` 有用到props就要寫type

<pre class="language-diff"><code class="lang-diff">```typescriptreact
<strong>
</strong>interface TooltipPropsWapperTypes {
  childrenSize: {
    width: number,
    height: number
  },

//有用到styled要加
- const TooltipWrapper = styled.div
+ const TooltipWrapper = styled.div&#x3C;TooltipPropsWapperTypes>`
top: ${(props) => props.position ? props.position.top : 0}px;



//MAP參數範例
type placementStyleMapType = {
+  [key: string]: RuleSet&#x3C;TooltipPropsWapperTypes>;
};

- const placementStyleMap{
+ const placementStyleMap: placementStyleMapType = {
  top: topStyle,
  'top-left': topLeftStyle,
  }
  

  //有用到css不用 
  //但提示會顯示這是一個  RuleSet&#x3C;TooltipPropsWapperTypes 如果有其他地方要用到這串變成參數要加
  const topStyle = css`
   color:black;
   transform: translate(
    calc(${(props: TooltipPropsWapperTypes) => props.childrenSize.width / 2}px - 50%),
  `
  
  // const TooltipWrapper = styled.div
const TooltipWrapper = styled.div&#x3C;TooltipPropsWapperTypes>`
  animation: ${(props) => (props.isVisible ? fadeIn : fadeOut)} .3s ease-in-out forwards;
  ${(props) => placementStyleMap[props.placement] || placementStyleMap.top}
}
`;
</code></pre>
