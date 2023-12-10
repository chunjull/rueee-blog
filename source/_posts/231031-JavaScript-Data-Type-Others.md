---
title: '#7 基本型別：布林值、null、undefined 與 symbol'
category: DoJS
tags:
  - JavaScript
abbrlink: 2849981050
date: 2023-10-31 00:00:00
---
簡介布林值、 `null` 、 `undefined`  與 `symbol` 等資料型別的常見應用。
<!--more-->
## 快速了解
### boolean
布林值（boolean）通常用在判斷式，作為控制程式流程的用途。
其值只有兩種：`true` 及 `false`。
### null
`null` 型別只有一種值——`null`（空值），代表「此變數可能曾經有值，也可能沒有值，**現在沒有值**」。
例如：以下案例中的 a ，明確表示此變數沒有值。
```jsx
var a = null; // null
```
### undefined
`undefined` 型別也只有一種值——`undefined`，代表「此變數**還沒有給值**，所以不知道是什麼」。
例如：以下案例的 b，當變數 b 被宣告時，其值還沒有定義或還未指定的情況下，預設值會是 `undefined`。
```jsx
var b; // undefined
```
### symbol
`symbol` 是 ES6 新增的基本資料型別，用來表示獨一無二的值，以避免名稱相同造成的衝突。
```jsx
let symbol1 = Symbol();
typeof symbol1; // symbol
```
### 小知識
- 在 JS 判斷比較的運算式中，所有內容都可以轉換為布林值。
- `typeof null` 回傳結果是`“obejct”` ，而非 `null`。這其實是一個 Bug！但因為修正該問題，會影響太多舊程式，最後只好保留這個錯誤。
## 了解更多
- [fooish－JavaScript ES6 Symbol 資料型態](https://www.fooish.com/javascript/ES6/Symbol.html)：了解 Symbol 的使用情境。
- [stackoverflow－Why is typeof null "object"?](https://stackoverflow.com/questions/18808226/why-is-typeof-null-object)：明白 `typeof null` 為什麼是 `“obejct”` 。