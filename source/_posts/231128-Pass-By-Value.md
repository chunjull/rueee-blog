---
title: '#35 參數傳遞：Pass by value'
category: DoJS
tags:
  - JavaScript
abbrlink: 1868702299
date: 2023-11-28 00:00:00
---
基本型別是以 Pass by value 的方式傳遞參數。
<!--more-->
## 快速了解
基本型別內的資料，會以**純值**的形式存在。
在比較、更新與傳遞時，也會以「值」的形式進行，這種參數傳遞方式被稱為「**傳值**」（Pass by value）。
### 基本型別的比較
在基本型別時，會透過變數裡面的內容——即「值」——來判斷兩個變數是否相等。
```jsx
// 數字
var a = 10;
var b = 10;
console.log(a === b); // true
// 字串
var c = 'Juby';
var d = "Juby";
console.log(c === d); // true
```
### 基本型別的更新與傳遞
在基本型別的變數中，看的是變數裡的「值」。
舉例來說，在複製變數時，複製的是該變數的「值」。
```jsx
var a = 10;
var b = a;
console.log(a); // 10
console.log(b); // 10
```
變數 b 的值是透過複製變數 a 的值而來。
但這不代表當變數 a 更新後，會影響變數 b 的數值：
```jsx
a = 100;
console.log(a); // 100
console.log(b); // 10
```
變數 a、b 是各自獨立的，變數 b 看起來是透過複製變數 a 而來，實際上，是變數 b 建立了一個新的值，再將變數 a 的內容複製過去。
因此，當變數 a 的內容後來經過更新變成 100 後，變數 b 的內容不受影響，依然是原本的 10。
## 了解更多
- [Kuro－JavaScript 是「傳值」或「傳址」？](https://ithelp.ithome.com.tw/articles/10191057)：本文最主要的參考範例。
- [itsems－Javascript中的傳值 by value 與傳址 by reference](https://medium.com/itsems-frontend/javascript-pass-by-value-reference-sharing-5d6095ae030b)：了解傳值方法。