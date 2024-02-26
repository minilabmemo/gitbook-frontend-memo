---
description: 快捷
---

# Emmet 快捷

## Emmet

`ul#nav>li.item$*4>a{Item $}`按下`tab`



Emmet: Exclude Languages

不應展開 Emmet 縮寫的語言陣列。

我的設定原先有設定 "markdown"，但我在寫文章時也習慣用上html，先刪掉。



問題：在html中可以運作，但html裡的script區段不行，

有人說是vue套件造成，但照設定後一樣不行...

````
```json
"emmet.triggerExpansionOnTab": true,
"emmet.includeLanguages": {
"vue-html": "html",
"vue": "html"
},
"emmet.syntaxProfiles": {
"vue-html": "html",
"vue": "html"
}
```
````



