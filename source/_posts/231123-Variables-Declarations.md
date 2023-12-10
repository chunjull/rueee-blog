---
title: "#30 變數宣告"
category: DoJS
tags:
  - JavaScript
abbrlink: 704880787
date: 2023-11-23 00:00:00
---
變數宣告與後續會提到的 JS 觀念息息相關。
<!--more-->
## 快速了解
我們之前介紹過，變數有三種宣告方式： `var` 、 `let` 、 `const` 。
過去通常會使用 `var` 宣告變數，直到 ES6 新增了區域變數 `let` 、 `const` ，開發者們逐漸以此取代 `var` 。
### var
- 宣告對象為變數（Variable）。
- 變數有效範圍為函式作用域。
- 允許重複宣告。
- 可以重新賦值。
- 宣告前就存取對應變數，會得到 `undefined` 。
### let
- 宣告對象為變數（Variable）。
- 變數有效範圍為區塊作用域，是區域變數。
- 同一個區塊作用域中不允許重複宣告。
- 可以重新賦值。
- 宣告前就存取對應變數，會得到 `ReferenceError` 錯誤。
### const
- 宣告對象為常數（Constant）。
- 變數有效範圍為區塊作用域，是區域變數。
- 同一個區塊作用域中不允許重複宣告。
- 不可以重新賦值。
- 宣告前就存取對應變數，會得到 `ReferenceError` 錯誤。
- **宣告時一定要給值**。
### 宣告方式整理
|  | var | let | const |
| --- | --- | --- | --- |
| 宣告對象 | 變數 | 變數 | 常數 |
| 有效範圍 | 函式作用域 | 區塊作用域 | 區塊作用域 |
| 能否重複宣告 | 可 | 同一個區塊作用域中不可 | 同一個區塊作用域中不可 |
| 能否重新賦值 | 可 | 可 | 不可 |
| 宣告強度 | 弱 | 中 | 強 |
| 嚴謹程度 | 低 | 高 | 高 |
### 小知識
- `var` 與 `let` 的差別在於： `var` 是以 `function` 為作用域； `let` 則是以大括號 `{}` 區塊的程式碼為作用的範圍。
## 了解更多
- [ㄚ淳淳－const、let、var的區別—DAY3](https://ithelp.ithome.com.tw/articles/10257802)：了解三種宣告的差異與練習題目。
- [popeye_ux－變數宣告var、let、const的區別](https://ithelp.ithome.com.tw/articles/10259329)：透過案例了解三種宣告的差異。
- [程式碼農－JS 宣告變數， var 與 let / const 差異](https://www.programfarmer.com/articles/2020/javascript-var-let-const-for-loop)：了解更詳細的三種宣告差異。