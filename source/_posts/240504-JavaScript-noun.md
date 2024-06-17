---
title: '#92 JS 名詞比較'
category: DoJS
tags:
  - JavaScript
abbrlink: 1637140423
date: 2024-05-04 00:00:00
---
比較 `not defined` 與 `undefined` 、單執行緒與多執行緒的差異。
<!--more-->
## 快速了解
### 變數定義狀態
一個變數的定義狀態通常可以分為兩種： `not defined` 與 `undefined` 。
- `not defined`：記憶體上沒有準備該變數的存放空間。
- `undefined`：記憶體已準備該變數的存放空間，但尚未賦值。
在開發時盡可能避免將 `undefined` 的值賦予到變數上，如果需要賦予空值在一個變數上，建議使用 `null` 。
 `null` 會指出一個變數不存在的狀態； `undefined` 則是代表一個變數還沒被賦予值、尚未初始化的狀態。
### 執行緒
行程（process）是 CPU 分配資源的最小單位，即「運行中的程式」。而執行緒（Thread）則是行程中的一部份，一個行程至少包含一或多個執行緒。
執行緒可以分成兩種類別：單執行緒與多執行緒。
- 單執行緒：一次只能執行一項任務。
- 多執行緒：可以執行多項任務。
JS 是單執行緒的程式語言，遇到多項任務時會「按照順序執行」，尚未被執行的任務會處於等待狀態，直到前面任務執行完成，才會往後執行。
### 小知識
- 因為 JS 設計 Bug 的關係， `typeof null` 回傳結果是`“obejct”` ，而非 `null` 。
## 了解更多
- [MDN－ReferenceError: "x" is not defined](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Errors/Not_defined)：了解 `not defined` 的意義。
- [MDN－undefined](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)：了解 `undefined` 的意義。
- [tim80411－行程(Process)、執行緒(thread)傻傻分不清楚(中)-執行緒管理](https://ithelp.ithome.com.tw/articles/10297649)：了解行程與執行緒的關係。
- [#7 基本型別：布林值、null、undefined 與 symbol](https://chunjull.github.io/javascript/20231031/2849981050/)：回顧 `null` 的型別判斷 Bug。