# DevTools

### 叫出開發模式視窗 cmd+option+i

### animation 視窗

選擇**DevTools** > **More tools** > **Animations**.，說明請看[Animations: Inspect and modify CSS animation effects](https://developer.chrome.com/docs/devtools/css/animations/)





### Console

**複製內容**

一般來說可以在 console 中印出陣列，但 console 會顯示階層式的物件，如果想要複製單純內物件內容，就要透過下列動作達成：

Right-click an object in Chrome’s console and select Store as Global Variable from the context menu. It will return something like temp1 as the variable name.

Chrome also has a copy() method, so copy(temp1) in the console should copy that object to your clipboard.

[Javascript / Chrome - How to copy an object from the webkit inspector as code](https://stackoverflow.com/questions/10305365/javascript-chrome-how-to-copy-an-object-from-the-webkit-inspector-as-code)

```
(9) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
temp1
(9) [{…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}, {…}]
copy(temp1)
JSON.stringify(temp1)
"[{"name":"Cupcake","pri":1,"status":"OPEN","type":"blog","protein":4.3},{"name":"Donut","pri":2,"status":"OPEN","type":"go","protein":4.9}]"

```
