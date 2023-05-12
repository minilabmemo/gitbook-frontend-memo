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



## 協助開發者debug的插件

chrome& firefox 上協助開發者debug的插件:React-Developer-Tools

打開瀏覽器的開發者工具後，會看到多了兩個名為 `Components` 和 `Profiler` 的頁籤

更多關於 [Profilers](https://reactjs.org/blog/2018/09/10/introducing-the-react-profiler.html) 的使用可以進一步參考 React 在官方網站 的說明。

\
