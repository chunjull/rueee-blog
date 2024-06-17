---
title: '#38 不可變的'
category: DoJS
tags:
  - JavaScript
abbrlink: 2821490299
date: 2023-12-01 00:00:00
---
基本型別的「不可變」特性，使其值必須重新賦值才能更新。
<!--more-->
## 快速了解
除了物件以外，其他基本型別（primitive types）都具有不可變的特性，並且會透過「傳值」方式傳遞參數。
換句話說，基本型別以「值」為基準，而不是以「址」為基準，每個值都是獨立的，就算值看起來是相等的，其所佔的記憶體位置也不一樣。
### 純值的重新賦值
因為不可變的特性，原本的值和後來的值是完全獨立的關係，必須要透過 `=` 重新賦值，才能讓後來的值取代原本的值。
```jsx
var a = "hello";
a = "yo";
console.log(a); // "yo"

a: "hello" 0x01 // 不會改變原本 hello 的值
a: "yo" 0x02 // 而是建立新的記憶體空間儲存 yo
```
變數 a 原本的值為「hello」，在宣告時被儲存在 0x01 的位置；被重新賦值時，後來的值「yo」不會取代舊值的位置，而是建立新的記憶體空間 0x02 來存放。
### 內建函式的重新賦值
由於字串具有不可變的特性，因此，不論呼叫什麼函式均無法改變 a 的值。必須要透過重新賦值，才能更新原本的值。
```jsx
// 範例一
var a = 'hello';
a.toUpperCase();
console.log(a); // hello

// 範例二
a = a.toUpperCase();
console.log(a); // HELLO
```
在範例一，試著透過內建函式 `toUpperCase()` 呼叫，使變數 a 的字串更新為大寫。但如果只對基本型別的值進行呼叫，不會有任何改變，回傳結果仍是原本的值—— `hello` 。
而範例二，則透過重新賦值的方式，讓變數 a **指向**了新的記憶體位置——即 `toUpperCase()` 的結果，才成功印出更新的值 `HELLO` 。
## 了解更多
- [文科少女學程式－JavaScript的mutable與immutable](https://pink-learn-frontend.medium.com/javascript萌新筆記-javascript的mutable與immutable-5dde0855040c)：詳細了解「不可變的」意義。
- [#35 參數傳遞：Pass by value](https://chunjull.github.io/javascript/20231128/1868702299/)：回顧「傳值」方式