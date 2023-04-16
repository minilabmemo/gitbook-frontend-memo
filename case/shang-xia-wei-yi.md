---
description: 上下位移
---

# 上下位移

做出上下位移. [MDN translateY()](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateY)

```
transform: translateY(-1%);
 A percentage value refers 
 to the height of the reference box defined by the transform-box property.
 測試發現會隨著內容改變而讓高度上移太多，如果是不確定內容大小，建議用固定上移px就可以了．
 
 transform: translateY(-3px);
```

