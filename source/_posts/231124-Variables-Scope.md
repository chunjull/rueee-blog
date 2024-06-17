---
title: '#31 變數的有效範圍'
category: DoJS
tags:
  - JavaScript
abbrlink: 3746595863
date: 2023-11-24 00:00:00
---
除了 `let` 與 `const` ，切分變數有效範圍的最小單位是 `function` 。
<!--more-->
## 快速了解
變數的有效範圍被稱為「作用域」（Scope），而**切分變數有效範圍的最小單位是** `function` 。
在 ES6 之前，JS 變數有效範圍的最小單位是以 `function` 作為分界。（ES6 新增的 `let` 與 `const` 例外）
舉例來說：
```jsx
var x = 1;
var doSomeThing = function(y) {
	var x = 100;
	return x + y;
};
console.log(doSomeThing(50)); // 150, 100 + 50
console.log(x); // 1
```
上述程式碼代表著：在函式區塊內透過 `var` 定義的 `x` 變數只屬於這個函式，函式外的 `x` 與函式內的 `x` 是兩個不同的變數。
因此， `doSomeThing(50)` 會印出 `100 + 50` 的 `150` ； `x` 則會印出函式外面的 `1` 。
### 找不到指定變數的情況
```jsx
var x = 1;
var doSomeThing = function(y) {
	return x + y;
};
console.log(doSomeThing(50)); // 51, 1 + 50
```
如果 `function` 內沒有 `var x` 的話，在自己的  內沒有找到，就會一層層往外找，直到「全域變數」為止。
### 沒有 var 宣告變數的情況
在下面案例中，把 `function` 內的 `var` 拿掉。
```jsx
var x = 1;
var doSomeThing = function(y) {
	x = 100;
	return x + y;
};
console.log(doSomeThing(50)); // 150, 100 + 50
console.log(x); // 100
```
因為「切分變數有效範圍的最小單位是 `function` 」的特性，如果 `function` 內部沒有使用再次用 `var` 宣告某變數，JS 就會再往外層查找有無同名的變數，直到最外層的「全域物件」為止。
因此，這會使得 `function` 內的 `x = 100` 變更了外層的同名變數 `x` 。
### 小知識
- 與 `var` 不同， `let` 與 `const` 的作用域是透過大括號 `{}` 來切分，且 `let` 不允許重複宣告。
- 函式外層無法使用內層宣告的變數，但內層可以使用外層的變數。
- 最外層的「全域物件」，以瀏覽器來說，就是 `window`
## 了解更多
- [Kuro－函式的基本概念](https://ithelp.ithome.com.tw/articles/10191549)：本文最主要的參考範例。
- [Lochs－Scope 作用域](https://medium.com/take-a-day-off/js-scope-作用域-ee536640963b)：了解三種作用域概念與預習作用域鏈的觀念。