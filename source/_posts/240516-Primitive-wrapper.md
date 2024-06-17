---
title: '#104 包裹器'
category: DoJS
tags:
  - JavaScript
abbrlink: 2915105083
date: 2024-05-16 00:00:00
---
基本型別包裹器會賦予「基本型別」屬性與方法。
<!--more-->
## 快速了解
JS 的資料型別有兩種：基本型別（Primitives）與物件型別（Object）。
在物件型別中，又可以再細分出幾種內建的「建構子函式」（Constructor function），例如： `String()` 、 `Number` 、 `Boolean()` 、 `Array()` 、 `Object()` 、 `Function()` 、 `RegExp()` 、 `Date()` 、 `Error()` 、 `Symbol()` 等。
這些建構子都是 JS 提供的內建函式，可以透過 `new` 運算子來產生對應物件。
### 自動轉型與基本型別
為什麼 `String()` 、 `Number` 、 `Boolean()` 這三個「基本型別」卻會有「屬性」與「方法」可以呼叫呢？這是因為「自動轉型」賦予「屬性」和「方法」給這三種基本型別，讓它們被轉型為「物件」。
JS 在存取 `String` 、 `Number` 與 `Boolean` 這三種基本型別的屬性時，會在存取當下的「那一刻」（runtime）被轉型為該類型的「物件」。
```jsx
let str = "Hello";
console.log(str.length);
```
以上述程式碼為例，讀取 `str.length` 時，背後原理是這樣的：
```jsx
let str = "Hello";
typeof str; // "string"
let strObj = new String("Hello");
typeof strObj; // "object"
strObj.color = "red";
str.color = "red";
console.log(strObj.color); // "red"
console.log(str.color); // undefined
```
JS 會透過對應的物件建構子函式將 `"Hello"` 包裝成 `String` 的「物件」，並在回傳對應的屬性後，即刻銷毀並恢復成基本型別。當我們分別為物件型別與基本型別的 `string` 變數設定 `color` 屬性時，雖然在設定時不會出錯，但在事後讀取時，基本型別的 `str` 屬性仍是 `undefined` ，物件型別的 `strObj` 字串則會保留 `color` 屬性。
### 基本型別包裹器
基本型別的「屬性」與「方法」是由對應的物件所提供，這些對應物件就是「基本型別包裹器」（Primitive Wrapper）。
「包裹器」意指這些複合式物件都有同樣特性，可以透過 `instanceof` 來確認其基本型別為何；若想取得原始值，則可以透過 `.valueOf()` 取得。例如：
```jsx
var nameStr = new String("Pikachu");
typeof nameStr; // "object"
nameStr instanceof String; // true
nameStr.valueOf(); // "Pikachu"
```
另外，在原本設計時 `null` 與 `undefined` 就是代表「空值」與「未定義」，因此沒有對應的物件型別，也不會有屬性與方法。
### 小知識
- 透過 `new` 建構式生成的結果必定是物件，不論是 `String` 、 `Number` 或 `Boolean` 。
## 了解更多
- [Kuro－基本型別包裹器 Primitive Wrapper](https://ithelp.ithome.com.tw/articles/10193902)：本文最主要的參考範例。
- [#4 資料型別簡介](https://chunjull.github.io/javascript/20231028/764880996/)：回顧 JS 資料型別簡介。