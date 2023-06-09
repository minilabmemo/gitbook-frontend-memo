# ReactDOM

## ReactDOM.createPortal

Portal 提供一個優秀方法來讓 children 可以 render 到 parent component DOM 樹以外的 DOM 節點。



{% hint style="info" %}
一個典型的 portal 使用案例是，當 parent component 有 `overflow: hidden` 或者 `z-index` 的樣式時，卻仍需要 child 在視覺上「跳出」其容器的狀況。例如 dialog、hovercard 與 tooltip 都屬於此案例。
{% endhint %}

```
ReactDOM.createPortal(child, container)

```
