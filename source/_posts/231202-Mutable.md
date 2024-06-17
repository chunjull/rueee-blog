---
title: '#39 可變的'
category: DoJS
tags:
  - JavaScript
abbrlink: 1332088474
date: 2023-12-02 00:00:00
---
物件型別的「可變」特性，使其內容可以直接被更新。
<!--more-->
## 快速了解
JS 的型別中，只有物件型別是可變的（Mutable），並且會透過「傳址」方式傳遞參數。
換句話說，物件型別以記憶體的「位址」為基準，來進行更新或複製，並非以「值」為基準。
因此，當物件更新時，會影響到所有引用該物件的變數與其副本。
### 物件更新
因為可變的特性，呼叫某些函式時，有可能會更動到原本記憶體位置儲存的東西。
```jsx
var arr = [2, 4, 6];
arr.push(8);
console.log(arr); // [2, 4, 6, 8]
```
在原本的陣列 arr 透過 `arr.push` 的方式呼叫，會更動到原本的陣列，使最後印出結果為 `[2, 4, 6, 8]` 。
這時，如果使用「重新賦值」的方式印出結果，將會產生不同的內容。
```jsx
var arr = [2, 4, 6];
arr = arr.push(8);
console.log(arr); // 4
```
在上述案例中，重新賦值會讓原本的陣列做兩件事情：新增元素到陣列、回傳陣列長度（arr.length）。使得最後印出結果變成陣列長度的 `4` 。
### 小知識
- 通常來說，不會改動到陣列的「內建函式」，其回傳結果**都不是陣列**，例如： `array.join()` 回傳結果為字串。
## 了解更多
- [文科少女學程式－JavaScript的mutable與immutable](https://pink-learn-frontend.medium.com/javascript萌新筆記-javascript的mutable與immutable-5dde0855040c)：詳細了解「可變的」意義。
- [#36 參數傳遞：Pass by reference](https://chunjull.github.io/javascript/20231129/1891124894)：回顧「傳址」方式。