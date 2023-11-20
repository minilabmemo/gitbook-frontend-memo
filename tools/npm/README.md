---
description: npm (Node Package Manager)
---

# npm

## 指令

```
npm install
//npm i或npm install xxx 就可以安裝一些東西，產生node_modules
npm install 這個指令其實會下載兩樣東西~ 首先是這個package(套件)本身，再來就是他的dependency。
npm install 後面可以加上其他指令，


npm start


npm init 用來創造package.json
npm init -y 用默認值初始化
*想要un-init 就刪掉package.json
```

### node版本

```
$ node -v
v14.17.0
```

#### 錯誤提示

有時候下指令安裝一堆東西時出現此錯誤 \`error glob-promise@6.0.2: The engine "node" is incompatible with this module. Expected version ">=16". Got "14.17.0"\`

* 可以依照這篇說明去升級 或是有其他略過方式（沒試過）
* [the-engine-node-is-incompatible-with-this-module](https://stackoverflow.com/questions/56617209/the-engine-node-is-incompatible-with-this-module)

{% code overflow="wrap" %}
```
error next@14.0.3: The engine "node" is incompatible with this module. Expected version ">=18.17.0". Got "18.16.1"
$ node -v
v18.16.1
```
{% endcode %}

#### 升級node版本

[How To Update Node Versions Using Mac, Windows, and Linux](https://blog.hubspot.com/website/update-node-js)

```sh
// 使用 brew 無用
// 使用上述方法1 npm升級
 ~ npm install -g n  
/usr/local/bin/n -> /usr/local/lib/node_modules/n/bin/n
+ n@9.1.0
added 1 package from 2 contributors in 1.278s
➜  ~ n latest
  installing : node-v20.3.0
       mkdir : /usr/local/n/versions/node/20.3.0
mkdir: /usr/local/n: Permission denied

  Error: sudo required (or change ownership, or define N_PREFIX)

➜  ~ sudo n latest
Password:
  installing : node-v20.3.0
       mkdir : /usr/local/n/versions/node/20.3.0
       fetch : https://nodejs.org/dist/v20.3.0/node-v20.3.0-darwin-x64.tar.xz
     copying : node/20.3.0
   installed : v20.3.0 (with npm 9.6.7)
➜  ~ node -v
v20.3.0

```



### 依賴項選項

```sh
要在依賴項Dependencies中添加包：
npm install my_dep --save
npm install my_dep -S
//為 npm 5.0.0，默認情況下安裝的模塊作為依賴項添加，因此 --save 選項不再使用

在devDependencies中添加包
npm install my_test_framework --save-dev
```



### 解安裝

```
*命令之後想要un-init還必須刪除該node_modules
npm uninstall -D 套件 這指令則是會把套件從package.json刪除 但是node_modules裡不會不見

```

### 更新依賴項

`npm outdated` 是一個 npm 命令，用於檢查項目中已安裝的依賴項是否過時。執行 `npm outdated` 命令可以列出目前安裝的依賴項與最新版本之間的差異。

要單獨更新特定的依賴項，可以使用 `npm update` 命令，後接要更新的依賴項的名稱。

簡化步驟：

1. 執行 `npm outdated` 檢查過時的依賴項。
2. 執行 `npm update` 加上依賴項的名稱進行單獨更新。

請注意，在更新依賴項之前備份項目並進行全面的測試，以確保新的依賴項版本與項目相容。

### 參考

|                                                                                                                        |                                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [npm 入門到進階X常用指令與版本規則教學](https://linyencheng.github.io/2022/09/27/relationships-between-frontend-and-backend/tool-npm/) | <p>npm 是 Node Package Manager 的縮寫，是 Node.js 預設的 node 套件管理平台<br>package-lock.json 檔來保存安裝的紀錄<br></p> |
| [問題 npm install的--save選項是什麼？](http://www.adabai.com/questions/a7071560507407.html)                                     | 為 npm 5.0.0，默認情況下，已安裝的模塊作為依賴項添加，因此 --save 選項不再使用                                                   |
| [how-to-un-init-npm](https://stackoverflow.com/questions/62061964/how-to-un-init-npm)                                  |                                                                                                    |
| [【D4 - npm 你到底是誰】大家都叫我npm install!! 但這甚麼意思](https://ithelp.ithome.com.tw/articles/10234060)                            | npm run serve 照著字面的意思就是要跑出一個server，就是說 : 「npm 你可以幫我跑一下我在package.json, serve 這個名子底下定義的指令嗎?」         |
| [npm 全域性安裝和本地安裝](https://www.796t.com/content/1546005002.html)                                                         | 全域性安裝： npm install axios -g                                                                        |
| [Day6 - Node Package Manager (NPM) 套件管理](https://ithelp.ithome.com.tw/articles/10185207)                               | 更新套件                                                                                               |
| [如何用 npm uninstall 删除一个开发依赖项](https://www.freecodecamp.org/chinese/news/npm-uninstall-how-to-remove-a-package/)        | npm uninstall -D                                                                                   |

\


## yarn安裝

```shell
# install yarn CLI globally
$ npm install -g yarn
+ yarn@1.22.19
added 1 package in 0.983s

#get the package's version
$ yarn --version
1.22.19
```
