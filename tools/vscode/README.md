---
description: '快速打開設定setting.json cmd+shift+P Preferences: Open User Settings (JSON)'
---

# vscode

### 內建css檢驗器

<pre class="language-diff"><code class="lang-diff">
<strong>"css.validate": true,
</strong><strong>"scss.validate": true,
</strong>"less.validate": true,

// 這樣一來
```css
main {
  margin: 0 auto;
-  margend: 0 auto; //打錯字就會有提示 不過我試過後面打算不會有效果 執行時才會有！invaild
}
```
</code></pre>

* 使用其他插件stylelingt 要把設定關掉&#x20;
  * 參考這篇[stylelint-in-vscode](https://stackoverflow.com/questions/71955851/stylelint-wont-mark-errors-in-vscode) （不知道為何對我沒用 TBD)
  * 演示效果可以參考官網demo

#### Code Spell Checker

變數拼字檢查
