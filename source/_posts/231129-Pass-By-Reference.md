---
title: '#36 參數傳遞：Pass by reference'
category: DoJS
tags:
  - JavaScript
abbrlink: 1891124894
date: 2023-11-29 00:00:00
---
物件型別是以 Pass by reference 的方式傳遞參數。
<!--more-->
## 快速了解
物件型別指的是**可能由零或多種不同型別**（包含純值與物件）所組成的物件。
在比較、更新與傳遞時，會以「實體參考」的形式進行，這種參數傳遞方式被稱為「**傳址**」（Pass by reference）。
### 物件型別的比較
JS 的物件可以被視為是一個「實體」（instance）。
對於兩個不同的實體來說，即使它們內容的「值」一樣，也不表示它們相等。
```jsx
var box1 = {value: 5};
var box2 = {value: 5};
console.log(box1 === box2); // false
```
雖然 box1、box2 看起來「等值」，但這並不是「box1 等於 box2 」的意思。
### 物件型別的更新與傳遞
物件是透過「引用」方式傳遞資料，接收的對象是引用的「參考」而不是「值」的副本。
因此，當被引用的參考內容被更新時，引用者的內容也會一併更新。在此時，透過 `===` 去檢查兩個實體，會發現兩者實際上是同一個實體。
```jsx
var box1 = {value: 10};
var box2 = box1;
console.log(box1.value); // 10
console.log(box2.value); // 10

// 更新 box1.value 內容
box1.value = 100;
console.log(box1.value); // 100
console.log(box2.value); // 100
console.log(box1 === box2); // true
```
這個流程是這樣運作：
首先在建立一個物件時，JS 會在記憶體某處建立一個物件，再將 box1 變數指向該新生成的物件。
接著，宣告第二個變數 box2 後，透過 `=` 將其指向 box1 的位置。
最後，當 box1.value 的內容更新，box2.value 也一起被更新。
## 了解更多
- [Kuro－JavaScript 是「傳值」或「傳址」？](https://ithelp.ithome.com.tw/articles/10191057)：本文最主要的參考範例。
- [itsems－Javascript中的傳值 by value 與傳址 by reference](https://medium.com/itsems-frontend/javascript-pass-by-value-reference-sharing-5d6095ae030b)：了解傳址方法。