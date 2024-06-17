---
title: '#37 參數傳遞：Pass by sharing'
category: DoJS
tags:
  - JavaScript
abbrlink: 3304160290
date: 2023-11-30 00:00:00
---
事實上，JS 是以 Pass by sharing 的方式傳遞參數。
<!--more-->
## 快速了解
大多數情況下，基本型別是「傳值」，物件型別是「傳址」。
但實際上，JS 不屬於單純的「傳值」或「傳址」。準確來說，JS 是透過「Pass by sharing」的方法來傳遞參數。
### Pass by sharing
Pass by sharing 的特點在於：當 `function` 的參數被重新賦值時，外部變數的內容不會被影響。而如果不是重新賦值的情況，則會跟 Pass by reference 的結果一樣。
```jsx
// 參數重新賦值
var box1 = {value: 10};
function changeValue(obj) {
	obj = {value: 123};
};
changeValue(box1);
console.log(box1); // {value: 10}

// 參數沒有被重新賦值
var box2 = {value: 10};
function changeValue(obj) {
	obj.value = 456;
};
changeValue(box1);
console.log(box1); // {value: 456}
```
### 可變的與不可變的
JS 型別具有兩種特性：可變的（mutable）與不可變的（immutable）。
物件型別是可變的，代表當物件更新時，會影響到所有引用這個物件的變數與其副本，修改時會變動到原本的參考。但在賦與新值時，卻會產生新的實體參考。
基本型別則是不可變的，代表更新某個基本型別的值時，與該值的副本完全無關。
在操作基本型別時，Pass by sharing 與 Pass by value 的結果一樣，修改時永遠只能賦與新值。
### 小知識
- 參數傳遞方式與 JS 的深拷貝（Deep copy）、淺拷貝（Shallow copy）方法相關。
## 了解更多
- [Kuro－JavaScript 是「傳值」或「傳址」？](https://ithelp.ithome.com.tw/articles/10191057)：本文最主要的參考範例。
- [itsems－Javascript中的傳值 by value 與傳址 by reference](https://medium.com/itsems-frontend/javascript-pass-by-value-reference-sharing-5d6095ae030b)：了解 Pass by sharing 方法。
- [Huli－深入探討 JavaScript 中的參數傳遞](https://blog.huli.tw/2018/06/23/javascript-call-by-value-or-reference/)：深入了解參數傳遞與深、淺拷貝方法。