---
title: '#26 函式：定義'
category: DoJS
tags:
  - JavaScript
abbrlink: 115912181
date: 2023-11-19 00:00:00
---
函式有三種定義方式，並可分為具名、匿名兩種。
<!--more-->
## 快速了解
函式有三種定義方式：
- 函式宣告（Function Declaration）。
- 函式運算式（Function Expressions）。
- 透過關鍵字 `new Function` 建立函式。
### 函式宣告
「函式宣告」是最常見的用法。
```jsx
function square(number) {
	return number * number;
};
```
### 函式運算式
將函式透過 `=` 指定給某個變數。
```jsx
var square = function (number) {
	return number * number;
}
```
### 透過關鍵字 new Function 建立函式。
因效能較差，實務上較少使用。
使用關鍵字 `new Function` 建立函式物件。
將參數與函式的內容依序傳入 `Function` ，即可建立一個函式物件。
```jsx
var square = new Function("number", "return number * number");
```
### 匿名函式
在前面「函式運算式」的範例中，可以發現：該函式是「沒有名字」的。
這種沒有名字的函式被稱為「匿名函式」。
### 小知識
- 有名字的「具名函式」只在「自己函式的區塊內」有效，換言之，脫離函式自身的 `{}` 區塊後，該變數就不存在。
## 了解更多
- [Kuro－函式的基本概念](https://ithelp.ithome.com.tw/articles/10191549)：本文最主要的參考範例。
- [MDN－函式](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Functions)：了解函式的常見用法。
- [Tim－具名函式與匿名函式的基本認識](https://hsuchihting.github.io/javascript/20200812/1474477581/)：了解匿名函式的使用方式。
- [OneJar－函數定義 (Function Definition) 的 100 種寫法](https://ithelp.ithome.com.tw/articles/10207740)：了解更多種函式定義方式。