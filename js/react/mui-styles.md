# MUI/styles

### 輪播器

[https://github.com/Learus/react-material-ui-carousel](https://github.com/Learus/react-material-ui-carousel)

* 只要照個說明加入就有一個簡單的輪播器,可以看demo決定要不要按鈕
* 缺點是已經有一些預設效果例如陰影 要用sx:{}屬性去移除等等
* 未解：圖片是用網址 引入內部位置圖片會失敗 不確定怎麼加



### Icon

* [https://fontawesome.com/v5/docs/web/use-with/react#using-icons](https://fontawesome.com/v5/docs/web/use-with/react#using-icons)
* react 的 icon 加入方法



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
