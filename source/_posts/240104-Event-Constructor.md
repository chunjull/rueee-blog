---
title: '#72 自定義事件'
category: DoJS
tags:
  - JavaScript
abbrlink: 3081470379
date: 2024-01-04 00:00:00
---
除了瀏覽器內建事件外，也可以自行建立事件。
<!--more-->
## 快速了解
除了瀏覽器提供的標準事件之外，BOM 也提供了讓開發者自行建立事件的方式，此類事件可以用 `Event constructor` 建立，同樣透過 `addEventListener` 去監聽，並由 `dispatchEvent` 來決定觸發的時機。
```jsx
var event = new Event("build");
// 監聽事件
element.addEventListener("build", function(e){...}, false);
// 觸發事件
element.dispatchEvent(event);
```
如果像要在自訂事件內增加更多資料，可以改用 `CustomEvent` ，在 Event Handler 則透過 `event` 接收：
```jsx
const event = new Custom("build", {"detail: elem.dataset.time"});
function eventHandler(e){
	log("The time is: " + e.detail);
};
```
## 了解更多
- [Kuro－那些你知道與不知道的事件們](https://ithelp.ithome.com.tw/articles/10192175)：本文最主要的參考範例。
- [MDN－Event reference](https://developer.mozilla.org/zh-TW/docs/Web/Events)：參考更多事件。