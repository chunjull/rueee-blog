---
title: '#33 暫時性死區'
category: DoJS
tags:
  - JavaScript
abbrlink: 1744441320
date: 2023-11-26 00:00:00
---
`let` 與 `const` 的宣告提升時，會產生暫時性死區。
<!--more-->
## 快速了解
暫時性死區（Temporal Dead Zone, TDZ）是只有 `let` 與 `const` 才具有的特性，專門用來解釋它們的提升行為。
### let 與 const 的提升
 `let` 與 `const` 也有提升，差別在於： `var` 提升之後，宣告的變數會被初始化為 `undefined` ；而 `let` 與 `const` 的宣告則不會被初始化為 `undefined`，如果在「賦值之前」就存取它，就會發生錯誤。
具體來說，在「提升之後」及「賦值之前」這段期間，如果存取該變數就會拋出錯誤，這段期間被稱為「暫時性死區」（TDZ）。
受到 TDZ 影響，變數需要在宣告後才能使用。如果在 `let` 與 `const` 宣告前讀取變數，會引發 `Uncaught ReferenceError` 的錯誤。
因此，不論是用何種宣告方式，使用變數前一定要先宣告。
### 函式宣告
除了變數，函式也有提升。
兩者差異為：變數提升只有宣告被提升；函式的提升則是包括內容都完全被提升。因此，函式提升優先於變數提升。
函式定義方式也會有差異。
透過函式宣告定義的函式，因為函式提升，可以在宣告前使用。
```jsx
square(2); // 4
function square(number) {
    return number * number;
};
```
透過函式運算式定義的函式則會出現錯誤。
```jsx
square(2); // Uncaught TypeError: square is not a function
var square = function (number) {
    return number * number;
};
```
### 小知識
- 除了可呼叫的時機不同外，「函式宣告」與「函式運算式」在執行時期沒有明顯的差別。
## 了解更多
- [Kuro－函式的基本概念](https://ithelp.ithome.com.tw/articles/10191549)：本文最主要的參考範例。
- [阿建－JavaScript 提升(Hoisting)是什麼?關於提升的5個觀念](https://jianline.com/javascript-hoisting/)：回顧變數提升的概念。
- [#26 函式：定義](https://chunjull.github.io/javascript/20231119/115912181/)：回顧函式定義方式。