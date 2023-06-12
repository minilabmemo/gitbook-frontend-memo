---
description: 排版問題
---

# 排版問題

### 盒子模型的邊距折疊問題

關鍵問題：子元素margin-top导致父元素移动的问题，

* [MDN CSS 外边距重叠](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS\_box\_model/Mastering\_margin\_collapsing) 會發生的情況說明
* [子元素margin-top导致父元素移动的问题](https://www.jianshu.com/p/6d9fb5fbbd34) 說明與解法
* [子元素设置margin-top和margin-bottom无效，外边距折叠导致父元素移动](https://blog.csdn.net/aaahuahua/article/details/115288283)

{% hint style="info" %}
塊的上外邊距(margin-top)和下外邊距(margin-bottom)有時合併(折疊)為單個邊距，其大小為單個邊距的最大值，這種行為稱為邊距折疊。
{% endhint %}

## 　當物件設定abosolute之後的置中方式

* [幾個我自己常用的水平置中或垂直置中的方式](https://ithelp.ithome.com.tw/articles/10228762)

## 有彈出框的設計卻點了沒反應

設計上有可能彈出框是在上層卻隱藏,點了才會出現,這時如果他佔據了空間且事件,會使你點不到底層,因此隱藏的方式很重要,建議用none隱藏使他完全消失,如果只是透明度隱藏還是存在

* [css隐藏元素 触发点击事件,CSS隐藏元素的方法及区别](https://blog.csdn.net/weixin\_35390057/article/details/119367585)
