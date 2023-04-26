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

