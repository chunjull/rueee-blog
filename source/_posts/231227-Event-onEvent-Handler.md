---
title: '#64 事件的註冊綁定'
category: DoJS
tags:
  - JavaScript
abbrlink: 3714111571
date: 2023-12-27 00:00:00
---
on-event 處理器可以針對 HTML 屬性與非 HTML 屬性，進行事件綁定。
<!--more-->
## 快速了解
針對 HTML 屬性與非 HTML 屬性，有不同的方式可以綁定網頁元素的事件。
### on-event 處理器（HTML 屬性）
對 HTML 元素來說，只要支援某個「事件」的觸發，就可以透過 `on` 加上事件名稱的屬性來註冊事件：
```html
<button id="btn" onclick="console.log("HI");">Click</button>
```
以上述程式碼為例，透過 `onclick` 屬性，可以在 `<button>` 元素上註冊 `click` 事件。換句話說，按下 `<button>` 元素時，會執行 `console.log("HI");` 的程式碼。
### on-event 處理器（非 HTML 屬性）
在 `window` 或 `document` 此類沒有實體元素的情況，可以利用 DOM API 提供的「 `on-event` 處理器」（on-event handler）來處理事件。
```jsx
window.onload = function() {
	document.write("Hello World");
};
```
上述程式碼會在 `window` 觸發 `load` 事件時執行對應內容。
此外，實體元素也可以透過 DOM API 取得 DOM 物件後，再透過 `on-event` 處理器處理事件。
```html
<button id="btn">Click</button>
```
```jsx
let btn = document.getElementById("btn");
btn.onclick = function(){
	console.log("HI");
};
```
如果想要解除事件，重新指定 `on-event` 處理器為 `null` 即可。
```jsx
btn.onclick = null;
```
### 小知識
- 早期 JS 常用 `on-event` 處理器的方式綁定 HTML 屬性的事件，在「非侵入式 JS」的理論被提出後，基於程式碼的重複使用性與維護性考量，現在已經不建議用此方式綁定事件。
## 了解更多
- [Kuro－事件機制的原理](https://ithelp.ithome.com.tw/articles/10191970)：本文最主要的參考範例。