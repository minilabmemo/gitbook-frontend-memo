# install nvm

安裝nvm for mac

brew install nvm



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



&#x20;[Node.js 安裝與版本切換教學 (for MAC)](http://icarus4.logdown.com/posts/175092-nodejs-installation-guide)
