---
title: '#16 邏輯運算子'
category: DoJS
tags:
  - JavaScript
abbrlink: 3042451770
date: 2023-11-09 00:00:00
---
JS 的邏輯運算子和多數程式語言不同，其結果值並非只有 `true` 或 `false` 。
<!--more-->
## 快速了解
邏輯運算子有三種：AND、OR、NOT，照理來說，運算後會得到 `true` 或 `false` 的結果。
然而在 JS 中，只有 NOT 運算子才會回傳 `true` 或 `false` 。AND 和 OR 運算子的回傳結果則不一定是 `Boolean` ，還可能會是兩個數值的其中之一。
讓我們先來了解三種邏輯運算子的定義，再理解 JS 中的特殊規則。
### AND
AND 以 `&&` 符號表示。
在「多數程式語言」中表示「條件 A `&&` 條件 B」，當 `&&` 左右兩側的值都是 `true` 時，會得到 `true` 的結果；若其中一方是 `false` 則會得到 `false` 。
不過，在 JS 中不是這樣運作。
### OR
OR 以 `||` 符號表示。
在「多數程式語言」中表示「條件 A `||` 條件 B」，當 `||` 左右兩側有一方為 `true` ，則結果是 `true` ；只有在兩側都是 `false` 時才會得到 `false` 。
不過，在 JS 中不是這樣運作。
### NOT
NOT 以 `!` 符號表示。
原本是 `true` 的結果經過 `!` 轉換後會得到 `false` ；而原本是 `false` 的結果則會變成 `true` 。
### Boolean 的型別轉換
JS 中可以分成兩種「值」：不是 true 就是 false。
- 經過 `ToBoolean` 轉換後得到 `false` 的值，這些被稱為「Falsy」值。
- 其他的值，即經過 `ToBoolean` 轉換後得到 `true` 的值，這些被稱為「Truthy」值。
絕大部分的情況都會變成 `true` ，因此以下只提及會變成 `false` 的特例：
- `undefined`
- `null`
- `+0` , `-0` ,  `NaN`
- `''`  , `””` （空字串）
除此之外，所有的狀況都是 `true` ，例如：0、 `[]` 、 `{}` 、 `function(){}` 、 `"''"` （這並不是空字串）。
### `&&`  與 `||` 的特殊案例
相較於其他程式語言，JS 針對 `&&` 與 `||` 有不同的規範：結果並非布林值的 `true` 或 `false` ，而是**兩個數值的其中之一**。
 `&&` 與 `||` 運算子在判斷時，會先對左邊的數值進行檢查：
- 若是 `Boolean` 就在做後續判斷；若不是，則會透過 `ToBoolean` 判斷是「truthy」或「falsy」，並以此轉換乘對應的 `true` 跟 `false` 。
- 對 `&&` 來說，若第一個數值轉換為 `true` ，則回傳第一個數值；否則回傳第二個數值。
- 對 `||` 來說，若第一個數值轉換為 `false` ，則回傳第二個數值；否則回傳第一個數值。
### 小知識
- 需要判斷某數值 Boolean 轉換後的結果時，可以透過兩次「NOT」操作，用 `!!xxx` 來取代 `Boolean(xxx)` 。
- Falsy 值還有一種：本來就是 `false` 值者。同時要注意，`Boolean(false)` 和 `Boolean("false")` 的結果不同，前者是 `false` ；後者是字串，所以結果為 `true`。
## 了解更多
- [Kuro－Boolean 的真假判斷](https://ithelp.ithome.com.tw/articles/10191343)：本文最主要的參考範例。
- [Vicky－Truthy 與 Falsy](https://medium.com/vicky-notes/truthy-%E8%88%87-falsy-c795dfbd7dda)：了解 Truthy 與 Falsy 的差異。