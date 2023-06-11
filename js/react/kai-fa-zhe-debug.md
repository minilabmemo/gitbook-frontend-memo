# 開發者debug

## 開發者工具

### 協助開發者debug的插件

chrome& firefox 上協助開發者debug的插件:React-Developer-Tools

打開瀏覽器的開發者工具後，會看到多了兩個名為 `Components` 和 `Profiler` 的頁籤

更多關於 [Profilers](https://reactjs.org/blog/2018/09/10/introducing-the-react-profiler.html) 的使用可以進一步參考 React 在官方網站 的說明。



### Components

可以直接在這邊找到傳入組件的PROPS與hooks裡的state, 甚至可以手動直接更改內容值來看看效果

![](<../../.gitbook/assets/image (2).png>)

> 備註 做拆分後有出現過devTools讀不到檔案出現異常timeout狀況,這時重開就可以了

## VS code

### css-in-js

#### css-in-js plugin

css-in-js [plugin](https://marketplace.visualstudio.com/items?itemName=paulmolluzzo.convert-css-in-js) 照說明可以做轉換 或自動完成 但txs測試沒作用？

#### styled-components

Styled Components has moved! Make sure you're downloading it from here: [https://marketplace.visualstudio.com/items?itemName=styled-components.vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=styled-components.vscode-styled-components)



### components

* [how-to-debug-create-react-apps-in-visual-studio-code](https://stackoverflow.com/questions/71412727/how-to-debug-create-react-apps-in-visual-studio-code)
*   您的_第一個_啟動配置很好，您只需要：

    1. `npm start`從一個單獨的終端啟動開發服務器；
    2. 按`F5`或 VS Code 中的綠色箭頭啟動調試器並打開一個新的瀏覽器實例。

    參考：[調試 React](https://code.visualstudio.com/docs/nodejs/reactjs-tutorial#\_debugging-react)

    **.vscode/launch.json**

    ```json
    {
      "version": "0.2.0",
      "configurations": [
        {
          "type": "chrome",
          "request": "launch",
          "name": "Launch Chrome against localhost",
          "url": "http://localhost:3000",
          "webRoot": "${workspaceFolder}"
        }
      ]
    }
    ```

然後斷點在組件上,可以看到參數變化
