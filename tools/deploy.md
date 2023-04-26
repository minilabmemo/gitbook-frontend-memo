# deploy

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

<strong>// Run parcel index.html 或是npm star 就可以打開http://localhost:1234 看到網頁了
</strong>
</code></pre>



