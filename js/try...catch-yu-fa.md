# try...catch 語法

[try...catch 語法](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/try...catch)

* `try...catch` 語法標記出一整塊需要測試的語句，萬一有例外拋出時，`try...catch` 語句就會捕捉。

```
try {
  throw "myException"; // 拋出例外
} catch (e) {
  // 用來處理任何例外的語句
  console.log(e); // 當我有捕捉到時會印出 myException 
}finally {
   console.log("不管怎樣我都會執行"); 
}
```
