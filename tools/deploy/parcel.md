# parcel

### 打包工具

### parcel

前端往往都需要使用一些打包工具，方便我們在使用新的開發方式後可以在瀏覽器正常運作，其中最熱門的就是 webpack，但 webpack 本身很大也很複雜，如果想要感受打包工具威力的話，這邊我們可以先使用 parcel.js 打包工具來幫助我們專案的開發。

* 網路介紹：[輕量的前端打包工具 parcel.js 安裝教學](https://tools.wingzero.tw/article/sn/215)

<pre class="language-diff"><code class="lang-diff">{
  "name": "parcel-sandbox",
  "version": "1.0.0",
  "description": "Simple Parcel Sandbox",
  "main": "index.html",
  "scripts": {
    "start": "parcel index.html --open",
    "build": "parcel build index.html"
  },
  "dependencies": {},
  "devDependencies": {
    "parcel-bundler": "^1.6.1"
  }
}

<strong>+// Run parcel index.html 或是npm star 就可以打開http://localhost:1234 看到網頁了
</strong>+ Run npm build 可以看到 產生出./dist資料夾
</code></pre>

* dist 資料夾 ：[Dist 是什麼?](https://recafox.github.io/2020/08/02/what-is-dist/)

> dist的全名是distributable, 動詞為distribute, 意為分發、派送，這裡放的都是程式碼對外發布之後會用到的資源，可以是程式碼、圖片等等，就是網站上會看到的、公開的東西，因此這個資料夾也可以被命名為`public`, 也可以是`build`, 因為在公開的網站中我們使用的會是編譯過後, build後的程式碼, 這些程式碼可能已經都被webpack這類的打包工具處理過, 壓縮過, 跟原本你所寫的程式碼已經有很大差別了
>
> 還有另一個常見的資料夾就是src, 相對於dist, 這裡會放開發用的程式碼, 由於還沒有被處理, 壓縮過, 這裡的程式碼就是你寫code的地方
>
> 而assets, 則會存放靜態檔案, 就是平常不太會動到的檔案, 像是圖片等等



\----------------------------------------



### 啟動

第一種方式. 安裝 live server 對著index.html 按 go live&#x20;

第二種方式. 利用 npm start 用 parcel 啟動

```
> parcel index.html --open

Server running at http://localhost:1234 

過程中會產生.cache(加速開發) 與 dist 資料夾，可以將兩者加入 gitignore 中
```

* parcel build index.html 報錯 跟這篇 htmlnano 解法一樣 [parcel-js-tree-render-is-not-a-function](https://stackoverflow.com/questions/67087634/parcel-js-tree-render-is-not-a-function)
* 確保可以 build 之後, 撰寫 dockerfile, build image

```
docker build -t fe-night-sky . --no-cache
docker run -p 80:80 fe-night-sky
打開 http://localhost 看到網站了！
```

####

#### 改變預設生成資料夾

&#x20;/dist 改成生成在/build 採用gh-pages -d build 時可能會抓這邊。

```
"build": "parcel build index.html --out-dir build",
```



{% hint style="info" %}
build 後的 index.html 理論上應該也可以用 live server 開啟正常。
{% endhint %}

###



### (補充) deploy/build  issue

#### 網站樣式與圖片都不見了&#x20;

parcel build 會幫你把css/js等等檔案放到build中，然後引入路徑也不一樣，可是這樣通常是絕對路徑，會造成找不到檔案的狀況。

```
  //本地打開 build index.html
Refused to apply style from 'http://127.0.0.1:5500/style.01b3b57d.css' because its MIME type ('text/html') is not a supported stylesheet MIME type, and strict MIME checking is enabled.

//部署上去也是
   minilabmemo.github.io/:1     GET https://minilabmemo.github.io/style.01b3b57d.css 404
  
  解法  加上--public-url ./ 再次開啟就抓到了。
  "build": "parcel build index.html --out-dir build  --public-url ./  ",
```
