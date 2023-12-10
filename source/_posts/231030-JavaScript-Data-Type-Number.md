---
title: '#6 基本型別：數字'
category: DoJS
tags:
  - JavaScript
abbrlink: 4193996687
date: 2023-10-30 00:00:00
---
數字型別除了基礎運算， `NaN` 與浮點數問題也相當重要。
<!--more-->
## 快速了解
JS 只有一種數字的型別，不論整數、浮點數，或 `Infinity`（無限大）、`-Infinity`（負無限大）及 `NaN`（不是數值）等特殊數字，都屬於 `number` 型別。
### 數字使用方式
數字有兩種使用方式：字面常量與科學記號表示法。

字面常量：
```jsx
var x = 90;
var y = 12.34;
```
科學記號表示法：
```jsx
var x = 101e3; // 101000
var y = 101e-3; // 0.101
```
### 無限的計算方式
`Infinity` 與 `-Infinity` 分別代表數學上的無限大與負無限大。
任何正數除以 0，結果會得到 `Infinity`；相反的，任何負數除以 0，結果會是 `-Infinity`。
### NaN
`NaN` 不等於任何數字，甚至是自己。因此，它與任何數字運算，結果都是 `NaN`。
然而，使用 `typeof` 判斷 `NaN` 型別時，回傳結果卻是數字。
那麼該如何判斷一個變數是否為 `NaN` 呢？可以透過 `isNaN(value)` 函式來協助：
```jsx
isNaN(NaN); // true
isNaN(123); // false
isNaN("123"); // false, 字串型別會被自動轉型成數字
isNaN("NaN"); // true, 字串 "NaN" 無法轉型成數字
```
### 浮點數
JS 在運算 `0.1 + 0.2` 時，其結果不是 `0.3`，而是 `0.30000000000000004` 。因此執行 `0.1 + 0.2 === 0.3` 會回傳 false 的結果。
這是因為 JS 採用「IEEE 754」六十四位元二進位浮點數算術標準，十進位的小數無法完美的用二進位表示，只能用無限循環的位數來趨近於十進位的小數，導致還原時的小數不夠精準。
透過 `toFixed()` 和 `toPrecision()` 設定精確度，可以避免浮點數問題。
例如：設定精確到小數第一位。
```jsx
console.log((0.1 + 0.2).toFixed(1)); // 0.3
console.log((0.1 + 0.2).toPrecision(1)); // 0.3
```
### 小知識
- 數字型別常搭配 `Math` 物件使用，例如： `Math.PI` 可用來計算圓周和直徑。
## 了解更多
- [MDN－Math 物件](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Math)：了解 `Math` 的常見用法。
- [MDN－NaN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/NaN)：了解 `NaN` 的使用方式與相關限制。
- [Floating Point Math](https://0.30000000000000004.com/)：解釋 `0.1 + 0.2 !== 0.3` 的原理與彙整各程式語言計算方式。