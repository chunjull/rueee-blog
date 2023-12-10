---
title: '#15 逗號運算子'
category: DoJS
tags:
  - JavaScript
abbrlink: 1989175817
date: 2023-11-08 00:00:00
---
逗號運算子可以分隔運算式，或同時宣告多組變數。
<!--more-->
## 快速了解
逗號運算子主要工作為：用逗號分隔運算式，使其依序由左至右執行，並且會回傳最後一個運算式的值。
### 基本用法
逗號運算子由逗號 `,` 表示，透過逗號運算子可以將多組運算式看作是同一個，最常出現在 `for` 迴圈中。
```jsx
for (i = 0, j = 10; i < 10; i++, j++) {
	k = i + j;
}
```
### 進階用法
此外，逗號運算子也可以宣告變數。具體來說，可以同時宣告多組變數，且給予預設值。
值得注意的是，若使用錯誤方式同時宣告多組變數，可能會造成「全域變數」的大麻煩！
以下展示正確與錯誤的宣告方式。
```jsx
// 原始方式
var a = 10;
var b = 10;
// 正確改寫
var a = 10, b = 10;
// 錯誤改寫
var a = b = 10;
```
錯誤改寫看似同時用 var 宣告 `a`、`b` 變數，並賦值「10」。
然而，變數 `b` 並沒有被透過 `var` 宣告，而是一個全域變數。
```jsx
var a = b = 10;
// 拆開來後
b = 10;
var a = b; // 注意！變數 b 沒有被 var 宣告，但變數 a 有被宣告
```
## 了解更多
- [Kuro－Boolean 的真假判斷](https://ithelp.ithome.com.tw/articles/10191343)：本文最主要的參考範例。
- [MDN－逗號運算子](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Comma_operator)：觀看更多逗號運算子的範例。