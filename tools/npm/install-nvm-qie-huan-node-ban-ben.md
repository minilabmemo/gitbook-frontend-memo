---
description: 切換版本
---

# install nvm 切換node版本

## 安裝nvm for mac

```
brew install nvm
```



### 改設定

加上source $(brew --prefix nvm)/nvm.sh

```
vi ~/.bash_profile 
➜  ~ . ~/.bash_profile
~ cat ~/.bash_profile 
export GOROOT="/usr/local/go"
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
export GO111MODULE="on"
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm

PATH="/usr/local/bin:${PATH}"
export PATH
alias python="/usr/local/bin/python3"
source $(brew --prefix nvm)/nvm.sh
```



### node版本列表

➜  \~ nvm ls-remote

```
~ nvm ls-remote       
        v0.1.14
        v0.1.15
        v0.1.16
        v0.1.17
        v20.3.1
        v20.4.0
```

### 下載與切換

```
 ~ nvm install v18.16.1
Downloading and installing node v18.16.1...
Downloading https://nodejs.org/dist/v18.16.1/node-v18.16.1-darwin-x64.tar.xz...
######################################################################### 100.0%
Computing checksum with shasum -a 256
Checksums matched!
Now using node v18.16.1 (npm v9.5.1)
Creating default alias: default -> v18.16.1
➜  ~ node -v
v18.16.1

```

\-我們可以用`$ nvm use <version>`切換版本：

```
 nvm use v0.10.24
```

* 需注意是n**v**m use xxx 跟n**p**m run start 兩者很像 啟動不了報錯訊息容易以為壞了

### 參考

&#x20;[Node.js 安裝與版本切換教學 (for MAC)](http://icarus4.logdown.com/posts/175092-nodejs-installation-guide)
