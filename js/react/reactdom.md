# ReactDOM

## ReactDOM.createPortal

Portal 提供一個優秀方法來讓 children 可以 render 到 parent component DOM 樹以外的 DOM 節點。



{% hint style="info" %}
一個典型的 portal 使用案例是，當 parent component 有 `overflow: hidden` 或者 `z-index` 的樣式時，卻仍需要 child 在視覺上「跳出」其容器的狀況。例如 dialog、hovercard 與 tooltip 都屬於此案例。
{% endhint %}

```
ReactDOM.createPortal(child, container)

```



### `StrictMode`



當您在 React 應用程序中使用 `<StrictMode>` 組件時，它會開啟嚴格模式，並在開發環境下執行額外的檢查和警告。嚴格模式可能會導致某些組件在初次渲染時觸發兩次。

在 `<StrictMode>` 組件下，React 會在初次渲染時進行「雙重渲染」以捕獲可能的潛在問題。這樣做是為了幫助您檢查並修復潛在的副作用和不正確的用法，並改善應用程序的可靠性。

因此，當您在 `<StrictMode>` 組件下運行應用程序時，某些組件可能會觸發兩次渲染。這是一種正常行為，並且僅在開發環境下發生。

然而，當您在非 `<StrictMode>` 環境中運行應用程序時，React 不會執行額外的檢查和警告，因此初次渲染只會觸發一次。

因此，如果您在 `<StrictMode>` 組件下觀察到初次渲染兩次的情況，那麼這是嚴格模式的預期行為，並且僅在開發環境下發生。在生產環境中，React 將只執行一次初次渲染。如果您的應用程序在非嚴格模式下只觸發一次初次渲染，那麼它是符合預期的行為。

您可以不必過於關注初次渲染兩次的情況，特別是在 `<StrictMode>` 環境

下。React 的嚴格模式主要用於檢測和提示潛在的問題，以幫助您提升應用程序的可靠性和性能。

[https://newsn.net/say/react-strict-mode.html](https://newsn.net/say/react-strict-mode.html)
