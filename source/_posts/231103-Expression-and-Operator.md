---
title: "#10 運算式與運算子"
category: DoJS
tags:
  - JavaScript
abbrlink: 808747970
date: 2023-11-03 00:00:00
---
JS 可分為陳述式與運算式，最關鍵的差異為是否會回傳結果。
<!--more-->
## 快速了解
JS 的語法基本上可以分為兩類：陳述式與運算式。

陳述式（Statement）：會執行一些程式碼，且不會回傳結果，像是變數宣告、賦值、流程判斷、迴圈等。
```jsx
var foo;
```
運算式（Expression）：會回傳結果。換言之，任何**可回傳結果**都可稱為運算式，像是純值、變數、運算子、執行函式等。
```jsx
// 純值範例
10; // 10
// 運算子範例
1 === 1; //true
```
### 重點整理
|  | 是否會回傳結果？ | 常見分類 |
| --- | --- | --- |
| 陳述式 | 不會回傳結果。 | 變數宣告、賦值、流程判斷、迴圈等。 |
| 運算式 | 會回傳結果。 | 純值、變數、運算子、執行函式等。 |
### 運算子
在運算式中，存在很多種運算子（Operator），它們可以對值進行運算，進而得到運算結果。
常見運算子包含：算術運算子、位元運算子、比較運算子、賦值運算子、邏輯運算子等。
### 小知識
- 運算式又稱「表達式」。
- 學習陳述式和運算式概念時，建議搭配 Chrome 的開發者工具。
## 了解更多
- [卡斯柏－JavaScript 表達式觀念及運用 - JS Expression](https://www.casper.tw/development/2020/09/17/js-expression/)：熟悉陳述式與表達式的差異。
- [itsems－Javascript 的表達式和陳述式](https://medium.com/itsems-frontend/javascript-expressions-and-statements-7bd374effc95)：觀看更多表達式案例。