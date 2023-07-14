---
description: 問題
---

# 問題

### npm install出現問題

最近下這錯誤很常有一堆錯誤，導致相依無法下載。



### node-sass問題

[https://hackmd.io/@mko123654/S1io-20K9](https://hackmd.io/@mko123654/S1io-20K9) 這篇是說要降node版本

我是把node-sass移除,安裝sass就好了



### gyp錯誤

還爆出python與node-gyp錯誤

```
  File "/usr/local/lib/node_modules/node-gyp/gyp/pylib/gyp/xcode_emulation.py", line 1551, in CLTVersion
    return re.search(regex, output).groupdict()["version"]
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
AttributeError: 'NoneType' object has no attribute 'groupdict'
gyp ERR! configure error 
gyp ERR! stack Error: `gyp` failed with exit code: 1
npm install with error: `gyp` failed with exit code: 1

yp ERR! cwd /Users/..../node_modules/deasync
gyp ERR! node -v v20.4.0
gyp ERR! node-gyp -v v9.4.0
```

網路上一樣的問題[\[ npm ERR! code 1 \] 我裝不起來CLI了啦，沒用過python卻一直跟我說python出問題](https://ithelp.ithome.com.tw/questions/10210962)

我發現我根本沒有python3，還跑去裝好python3，但一樣會有錯誤。

後來裝了nvm，一種可以輕鬆降node版本的工具，我降到了node -v v18.16.1 終於解了。$ npm -v 9.5.1

#### 檢查node/npm版本

```
$ node -v v20.3.0 
 $ npm -v 9.8.0
重新安裝 可以再去nodejs 重新下載點安裝即可
但是安裝後的版本是node 升版 npm 將版？？
$ npm -v
9.7.2
$ node -v
v20.4.0
```
