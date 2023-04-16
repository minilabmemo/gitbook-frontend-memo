# deploy-github



1. 安裝工具 `npm i gh-pages`
2. 添加package.json

```diff
+ "homepage": "https://<youeaccout>.github.io/reponame",  

"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
+    "predeploy": "npm run build", 
+    "deploy": "gh-pages -d build"
  },
```

3.執行`npm run deploy`

4.到github網站就會看到多了一個分支叫做 **gh-pages**

5\. 文章說還要再進一步配置，但我看已經有預設值了，接著直接去看deployments就可以開啟網站了







| 文章                                                                                                | Memo   |
| ------------------------------------------------------------------------------------------------- | ------ |
| [\[Git Note\] — React 部署至 GitHub Page 超級淺入遷出](https://rexhung0302.github.io/2021/09/28/20210928/) | 完整圖文教學 |
|                                                                                                   |        |
|                                                                                                   |        |



