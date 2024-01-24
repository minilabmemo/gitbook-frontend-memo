# deploy-github



1. 安裝工具 `npm i gh-pages`
2. 添加package.json

````diff
```json
 "homepage": "https://minilabmemo.github.io/f2e-election-person",
   "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
```
+ "homepage": "https://<youeaccout>.github.io/reponame",  

"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
+    "predeploy": "npm run build", 
+    "deploy": "gh-pages -d build"
  },
````

```
-d 代表資料夾
gh-pages -d build。//react專案
gh-pages -d dist   //vue專案
```

3.執行`npm run deploy`

如果報錯Failed to get remote.origin.url 就代表要先去設定遠端位置

```bash
$ npm run deploy

> pet-finder-tw@0.1.0 predeploy /Users/yiyin/dev/front/react/pet-finder-tw
> npm run build


> pet-finder-tw@0.1.0 build /Users/yiyin/dev/front/react/pet-finder-tw
> react-scripts build

Creating an optimized production build...
Compiled successfully.

File sizes after gzip:

  46.63 kB  build/static/js/main.02ca2eea.js
  1.79 kB   build/static/js/787.a1295684.chunk.js
  541 B     build/static/css/main.073c9b0a.css

The project was built assuming it is hosted at /pet-finder-tw/.
You can control this with the homepage field in your package.json.

The build folder is ready to be deployed.

Find out more about deployment here:

  https://cra.link/deployment


> pet-finder-tw@0.1.0 deploy /Users/yiyin/dev/front/react/pet-finder-tw
> gh-pages -d build

Published
```

4.到github網站就會看到多了一個分支叫做 **gh-pages**

5\. 文章說還要再進一步配置，但我看已經有預設值了，接著直接去看deployments就可以開啟網站了







| 文章                                                                                                      | Memo   |
| ------------------------------------------------------------------------------------------------------- | ------ |
| [\[Git Note\] — React 部署至 GitHub Page 超級淺入遷出](https://rexhung0302.github.io/2021/09/28/20210928/)       | 完整圖文教學 |
| [\[Day 29 - 即時天氣\] 寫網頁就是要炫耀啊，不然要幹麻？發布上 Github Pages 吧！](https://ithelp.ithome.com.tw/articles/10228423) |        |
|                                                                                                         |        |



