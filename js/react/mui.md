# MUI/styles

### 輪播器

[https://github.com/Learus/react-material-ui-carousel](https://github.com/Learus/react-material-ui-carousel)

* 只要照個說明加入就有一個簡單的輪播器,可以看demo決定要不要按鈕
* 缺點是已經有一些預設效果例如陰影 要用sx:{}屬性去移除等等
* 未解：圖片是用網址 引入內部位置圖片會失敗 不確定怎麼加



### Icon

* react 的 icon 加入方法 [https://fontawesome.com/v5/docs/web/use-with/react#using-icons](https://fontawesome.com/v5/docs/web/use-with/react#using-icons) 這班只有看到v5版本的加入方式
* icon 庫搜尋 [https://fontawesome.com/v5/search?q=home\&o=r\&m=free](https://fontawesome.com/v5/search?q=home\&o=r\&m=free) 版本記得選免費與v5,pro不可用
* 引用時不知道為什麼 他提示的命名不可以用,另外引入方式不是用global而是獨立的
* 問題未解：icon看到的樣式有些微不同.... 騙人啊！

{% hint style="warning" %}
這樣一來還是自己匯入svg 來的一致？
{% endhint %}

````diff
```json
 "@fortawesome/fontawesome-svg-core": "^6.4.0",
    "@fortawesome/free-solid-svg-icons": "^6.4.0",
    "@fortawesome/react-fontawesome": "^0.2.0",
```

+import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'
+import { faCheckSquare, faHome } from '@fortawesome/free-solid-svg-icons'
-import { fahome } from '@fortawesome/free-solid-svg-icons' 他提示的命名不可以用

+<FontAwesomeIcon icon={faHome} />

````

### css-in-js

* [CSS in JS (react) 簡介與優缺點分析](https://linyencheng.github.io/2022/09/10/relationships-between-frontend-and-backend/css-in-js-with-reactjs/)
* css moules

```
import styleMain from "./main.module.css";
import stylePage from "./page.module.css";

export default function Test() {
  return (
    <div>
      <h1 className={styleMain.information}>App</h1>
      <h3 className={stylePage.information}>Test</h1>
    </div>
  );
}
```

#### style-component

````diff

+發現props可以一直傳到下面去
```typescriptreact
const OverlayWrapper = styled.div<OverlayWrapperProps>`
  ${(props: OverlayWrapperProps) => placementStyleMap[props.placement] || placementStyleMap.top};
`;

+placementStyleMap 裡面可以對應到另一種type, 這裡面用到的參數不可以與OverlayWrapperProps有衝突

```

-但是有一次使用isOpen,雖然可以執行 但一直跳出紅色的錯誤log,
React does not recognize the `isOpen` prop on a DOM element. If you intentionally want it to appear in the DOM as a custom attribute, spell it as lowercase `disabledbackgroundcolor` instead. If you accidentally passed it from a parent component, remove it from the DOM element.

+isOpen 一直叫我全部小寫, 參考網路文章說明 要加上＄isOpen. 錯誤就消失了

//參考：
https://styled-components.com/docs/api#transient-props
如果你想防止本應由樣式化組件使用的 props 傳遞到底層 React 節點或渲染到 DOM 元素，你可以在 prop 名稱前加上美元符號 ( )，將其轉換為瞬態 prop $。
https://juejin.cn/post/7109726822622822436
````



不知道為什麼沒有辦法在裡面同時使用theme/props 不知道怎麼加 TBD
