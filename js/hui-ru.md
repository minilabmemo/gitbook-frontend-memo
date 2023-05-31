---
description: 匯入
---

# 匯入

### **匯入 default export**&#x20;

```
===================
export default App;
=======================
import App from './module.js';
```



### **匯入 named export**

具名的匯出方式，則需要使用**解構的語法**將特定的模組取出（命名需與匯出的名稱一致），並且只有被匯入的原始碼片段才能夠被執行。

<pre><code><strong>===================================
</strong><strong>export const obj = { name: 'obj'}; // 此段如果沒有被匯入，則無法運作
</strong>export function fn() {
  console.log('這是一段函式')
}
====================================
import { fn, obj } from './module.js';
fn();
console.log(obj)
</code></pre>



