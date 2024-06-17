---
title: '#54 DOM：innerHTML'
category: DoJS
tags:
  - JavaScript
abbrlink: 3149519580
date: 2023-12-17 00:00:00
---
`innerHTML` 能夠將字串傳進 HTML 並進行渲染，但安全性較低。
<!--more-->
## 快速了解
前面介紹過，可以利用 `document.createElement()` 的方式建立新元素。但此方法還需要搭配 `appendChild()` 、 `insertBefore()` 等語法將內容顯示在網頁中。
這時，如果透過 `innerHTML` 則可以讓我們用更簡潔的程式碼來使用 JS 操作 HTML。
### innerHTML
 `innerHTML` 可以較方便地插入、替換 HTML 內容，但仍有其限制：插入內容必須是**字串**型別。
嚴格來說， `innerHTML` 的插入內容必須是**包含 HTML 標籤的字串**。
另外，需要特別注意的是：若插入內容包含 class 屬性，要小心包圍 `class` 值的**單雙引號**不要跟外面包起來的引號重複，否則解譯器會不知道這一行程式碼的終點為何。
```jsx
let el = document.getElementById("main");
el.innerHTML = "<p class='red'>Ya!</p>"; // 注意單雙引號的使用
```
### innerHTML 與 createElement 的比較
innerHTML：
- 不需要搭配其他語法使用。
- 組完字串後，傳進 HTML 裡進行渲染。
- 安全性低，可能會成為網路攻擊的媒介，而導致安全問題。
- 效能較高。
createElement：
- 需搭配 `appendChild()` 使用，在 HTML 父元素下新增子元素。
- 以建立一個新的 DOM 節點來處理。
- 安全性高。
- 效能較低。
### 重點整理
|  | 使用方式 | 優點 | 缺點 |
| --- | --- | --- | --- |
|  innerHTML  | 以字串渲染 | 效能高 | 安全性低 |
|  createElement  | 以 DOM 節點處理 | 安全性高 | 效能低 |
### 小知識
- 如果需要插入一段 HTML，而非替代它的內容，建議使用 `insertAdjacentHTML()` 方法。
- 基於資安風險問題，插入純文字內容時，建議使用 `Node.textContent` 方法。
## 了解更多
- [MDN－innerHTML](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/innerHTML)：了解 `innerHTML` 的使用方式。
- [MDN－insertAdjacentHTML](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/insertAdjacentHTML)：了解 `insertAdjacentHTML()` 的使用方式。
- [Tim－使用 JavaScript 插入 innerHTML](https://hsuchihting.github.io/javascript/20200630/2965249736/)：觀看更多 `innerHTML` 範例。
- [Greta Ma－如何用 JS 新增 HTML 內容](https://ithelp.ithome.com.tw/articles/10218607)：了解 `innerHTML` 與 `createElement` 的差異。
- [#49 DOM：節點新增](https://chunjull.github.io/javascript/20231212/929725069/)：回顧 `createElement` 新增節點的方式。