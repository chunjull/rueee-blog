---
title: '#65 事件監聽'
category: DoJS
tags:
  - JavaScript
abbrlink: 626749644
date: 2023-12-28 00:00:00
---
使用 `addEventListener()` 註冊事件監聽的好處：可重複指定多個「處理器」給同一事件。
<!--more-->
## 快速了解
前一個章節介紹的 `on-event` 處理器其對應 `function` 指「事件處理器」，本節分享的 `addEventListener()` 則是「事件監聽器」。
### addEventListener() 節構
 `addEventListener()` 基本上有三個參數：「事件名稱」、「事件處理器」（事件觸發時執行的 `function` ）及「一個 `Boolean` 值」。並由該 `Boolean` 值決定事件是以「捕獲」或「冒泡」機制執行，若不指定則預設為「冒泡」。
使用 `addEventListener()` 註冊事件的好處是：可以重複指定多個「處理器」給同一元素的同一事件。
```html
<button id="btn">Click</button>
```
```jsx
let btn = document.getElementById("btn");
btn.addEventListener("click", function(){
	console.log("HI");
}, false);
btn.addEventListener("click", function(){
	console.log("HELLO");
}, false);
// "HI"
// "HELLO"
```
### 解除事件監聽
透過 `removeEventListener()` 可以解除事件註冊。
和 `addEventListener()` 一樣， `removeEventListener()` 的三個參數分別是「事件名稱」、「事件處理器」以及「捕獲」或「冒泡」的機制。
```html
<button id="btn">Click</button>
```
```jsx
let btn = document.getElementById("btn");
// 把 event handler 拉出來
const clickHandler = function(){
	console.log("HI");
};
const clickHandler2 = function(){
	console.log("HELLO");
};
// 註冊事件監聽
btn.addEventListener("click", clickHandler, false);
btn.addEventListener("click", clickHandler2, false);
// 解除事件監聽
btn.removeEventLister("click", clickHandler2);
// 成功移除 clickHandler2
```
### 同時綁定多個處理器的情況
需要特別注意：因為 `addEventListener()` 可以同時針對某事件綁定多個處理器，所以透過 `removeEventListener()` 解除事件時，第二個參數的處理器必須要與先前在 `addEventListener()` 綁定的是同一個「實體」。因此，建議將第二個參數先另外宣告，再註冊事件監聽。
```html
<button id="btn">Click</button>
```
```jsx
let btn = document.getElementById("btn");
// 先宣告第二個參數
const clickHandler = function(){
	console.log("HI");
};
// 註冊事件監聽
btn.addEventListener("click", clickHandler, false);
// 解除事件監聽
btn.removeEventLister("click", clickHandler, false);
// 成功移除 clickHandler
```
### option 物件
 `addEventListener()` 的第三個參數用來表示「捕獲」或「冒泡」的機制，除了單一個 `Boolean` 值，還可以傳入名為 `option` 的物件。
 `option` 物件有三個屬性可以指定，每一個的值都是 `Boolean` ：
- `once` ：代表該事件只會被觸發一次，結束後就自動解除事件監聽。
- `passive` ：當設定成 `true` 時，表示該處理器不會呼叫 `event.preventDefault()` 這個 event 方法。若開發者呼叫 `event.preventDefault()` ，瀏覽器會直接忽略並在 console 主控台顯示警告訊息。
- `capture` ：與原本用來表示「捕獲」或「冒泡」的機制相同。
```jsx
element.addEventListener("click", myClickHandler, {
	once: true,
	passive: true,
	capturn: true
});
```
### 小知識
- 除了 IE，目前多數主流的瀏覽器都支援 `option` 物件。遇到不支援 `option` 物件的瀏覽器，會把其視為 `true` 看待。
## 了解更多
- [MDN－addEventListener()](https://developer.mozilla.org/zh-CN/docs/Web/API/EventTarget/addEventListener)：了解 `addEventListener()` 的使用方式。
- [MDN－options](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#options)：了解 `option` 的結構。
- [Alex lan－addEventListener的第三個參數](https://medium.com/@alexian853/addeventlistener%E7%9A%84%E7%AC%AC%E4%B8%89%E5%80%8B%E5%8F%83%E6%95%B8-%E9%82%A3%E4%BA%9B%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC%E6%87%89%E8%A9%B2%E8%A6%81%E7%9F%A5%E9%81%93%E7%9A%84%E5%B0%8F%E4%BA%8B-%E4%BA%8C-7fc29c9dec2)：中文版 `option` 介紹。