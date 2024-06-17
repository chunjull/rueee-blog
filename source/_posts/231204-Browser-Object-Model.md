---
title: '#41 BOM'
category: DoJS
tags:
  - JavaScript
abbrlink: 3425939589
date: 2023-12-04 00:00:00
---
BOM 有兩種功能：全域物件與瀏覽器溝通窗口。
<!--more-->
## 快速了解
BOM（Browser Object Model），瀏覽器物件模型，是瀏覽器所有功能的核心，與網頁的內容無關。
### window 物件
BOM 的核心是 `window` 物件。
 `window` 物件提供的屬性主要有 `document` 、 `location` 、 `navigator` 、 `screen` 、 `history` 及 `frames` 。
在瀏覽器裡的 `window` 物件扮演著兩種角色：
- ECMAScript 標準裡的「全域物件」（Global Object）。
- JavaScript 用來與瀏覽器溝通的窗口。
### 全域物件
作為 JavaScript 的全域物件， `window` 物件包含了所有全域變數與函式，通常會把這些變數稱為「全域變數」，可以透過 `window.xxx` 取得它們。
```jsx
var a = 10;
console.log(window.a); // 10
```
在「全域作用範圍」宣告的全域變數雖然屬於 `window` 的屬性，但它無法使用 `delete` 關鍵字移除。
```jsx
var a = 10;
console.log(window.a); // 10
delete window.a; // false
console.log(window.a); // 10
```
但如果是直接透過指定 `window` 物件的屬性，就可以成功刪除。
```jsx
window.a = 10; // 直接指定 window.a
console.log(window.a); // 10
delete window.a; // true
console.log(window.a); // undefined
```
### 瀏覽器的溝通窗口
瀏覽器環境的 BOM 與 `window` 物件提供了多種內建功能的 API，例如：開啟或關閉視窗、改變視窗大小、計時器與取得網址等。 
`window` 物件只需要一行程式碼即可生成一個對話框。
舉例來說：用 `alert()` 產生一個「警告對話框」。
```jsx
alert("Hello!");
window.alert("Hello!");
```
實際上， `window.alert("Hello!");` 才是完整語法，但因為全域物件的特性， `window` 可以省略不打。
### 小知識
- BOM 有時被稱為「Level 0 DOM」，是因為它在 DOM Level 1 標準前就已存在，而非真的有文件規範。
- 在「全域作用範圍」內宣告的變數、物件、函式，都會自動變成「全域物件」的屬性。
## 了解更多
- [Kuro－前端工程師的主戰場：瀏覽器裡的 JavaScript](https://ithelp.ithome.com.tw/articles/10191666)：本文最主要的參考範例。
- [MDN－Window](https://developer.mozilla.org/en-US/docs/Web/API/Window)：了解更多 `window` 物件的屬性與方法。
- [Samuel－BOM和DOM筆記](https://medium.com/%E5%BF%AB%E6%A8%82%E5%AD%B8%E7%A8%8B%E5%BC%8F/javascript%E5%85%A5%E9%96%80%E7%B3%BB%E5%88%97-%E4%BD%95%E8%AC%82bom%E5%92%8Cdom-b6eeab2ee5fd)：觀看常用的 `window` 屬性及說明。
- [#34 全域變數與區域變數](https://chunjull.github.io/javascript/20231127/3502683458/)：回顧「全域物件」的概念。