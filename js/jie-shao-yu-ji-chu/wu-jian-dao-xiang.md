---
description: 物件導向
---

# 物件導向









#### 沒有用new是呼叫函示，有用new是建構函式嗎

在 JavaScript 中，我們使用 `new` 來呼叫一個函數，通常是用來創建一個新的物件實例。這種特殊的函數通常被稱為構造函數（Constructor Function）。

當使用 `new` 關鍵字來調用一個函數時，它會執行以下步驟：

1. 創建一個空的物件。
2. 設置該物件的 `[[Prototype]]` 屬性為構造函數的 `prototype` 屬性。
3. 將構造函數的 `this` 綁定到剛剛創建的物件。
4. 執行構造函數，並將 `this` 作為新創建的物件返回值。

這樣，使用 `new` 關鍵字創建的實例具有構造函數定義的屬性和方法。

以下是一個示例：

```javascript
// 定義構造函數
function Animal(name) {
    this.name = name;
}

// 使用 new 關鍵字創建實例
var myAnimal = new Animal("Cat");

console.log(myAnimal.name); // 輸出: Cat
```

如果在創建實例時沒有使用 `new`，那麼該函數將被視為一個普通的函數調用，並且 `this` 的值將取決於它被調用的上下文。這可能導致意外的行為，因為沒有創建新的物件實例。

簡而言之，`new` 用來標記函數的調用方式，指示該函數應該用作構造函數，創建新的實例。
