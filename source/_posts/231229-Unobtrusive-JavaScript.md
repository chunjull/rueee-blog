---
title: '#66 非侵入式 JS'
category: DoJS
tags:
  - JavaScript
abbrlink: 3684974278
date: 2023-12-29 00:00:00
---
非侵入式 JS 讓 HTML 與 JS 能「關注點分離」。
<!--more-->
## 快速了解
非侵入式 JS（Unobtrusive JavaScript）是一種將 JS 從 HTML 結構中抽離的設計概念，避免在 HTML 標籤中夾雜一堆類似 `onchange` 、 `onclick` 等屬性來註冊 JS 事件，使 HTML 與 JS 能真正做到關注點分離，讓 HTML 專心負責結構與內容，而 JS 則專心負責操作與行為。
因此，傳統透過屬性去註冊事件的方式，屬於「侵入式」作法；而當頁面載入到瀏覽器中時，才去相對應地進行事件設定，則是屬於「非侵入式」的 JS 作法。
非侵入式 JS 範例：
```jsx
window.addEventListener("DOMContentLoaded", function(event){
	var btn = document.getElementById("btn");
	btn.addEventListener("click", clickHandler, false);
});
```
上述程式碼中， `window` 的 `DOMContentLoaded` 事件代表網頁上的 DOM 已解析完畢。
### 補充說明
除了事件之外，非侵入式 JS 的本質其實是在原有基礎上再增加「行為層分離」的概念，這些原則對大規模軟體工程開發非常重要。
## 了解更多
- [維基百科－非侵入式JavaScript](https://zh.wikipedia.org/zh-tw/%E9%9D%9E%E4%BE%B5%E5%85%A5%E5%BC%8FJavaScript)：了解非侵入式 JS 的概念。
- [Nissen－前端技術發展史，關注點分離的辯證](https://nissentech.org/frontend-soc-evolution/)：了解「關注點分離」的重要性。
- [#64 事件的註冊綁定](https://chunjull.github.io/javascript/20231227/3714111571/)：回顧非侵入式 JS 的影響。