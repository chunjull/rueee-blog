---
title: '#111 ES6：let 與 const'
category: DoJS
tags:
  - JavaScript
abbrlink: 3102308988
date: 2024-05-23 00:00:00
---
`let` 與 `const` 能夠有效解決 `var` 宣告產生的問題。
<!--more-->
## 快速了解
過去，JS 開發者皆以 `var` 作為變數宣告的方式，直到 ES6 新增了 `let` 與 `const` 這兩種宣告方式，能夠彌補 `var` 變數宣告的缺陷，才逐漸以 `let` 與 `const` 取代 `var` 。
### 回顧 `var`
 `var` 的宣告對象為變數（Variable），其有效範圍是函式作用域。允許重複宣告且可以重新賦值，因此若宣告兩個同名變數時，後宣告者會覆蓋先宣告者的值，導致開發問題。
以 `for` 迴圈為例：
```jsx
for (var i = 0; i < 10; i++){
	console.log(i); // 0~9
};
console.log(i); // 10
console.log(window.i); // 10
```
因為 `for` 迴圈裡 `var` 宣告的變數 `i` 是全域變數，因此不論在 `for` 迴圈內、外都可以取用到 `i` 的值，造成作用域被污染，使得在迴圈範圍外，仍可以透過 `window.i` 找到 `i` 值。
透過立即函式（IIFE）可以將 `var` 的有效範圍限制在「函式區塊」內，以保全作用域的完整性。
```jsx
(function (){
	for (var i = 0; i < 10; i++){
		console.log(i); // 0~9
	};
})();
console.log(i); // Uncaught ReferenceError: i is not defined
```
藉由立即函式包住 `for` 迴圈，即可避免在 `for` 迴圈外層還能取到內層 `i` 值的情況。
### `let` 與 `const` 的基本概念
相較於 `var` 可以重複宣告同樣的變數名稱並重新賦值，在相同作用域下， `let` 與 `const` 無法再重新宣告同名變數，但使用 `let` 宣告變數者，可以修改其值；而使用 `const` 宣告變數者，則無法重新賦值。
因為 `let` 與 `const` 的有效範圍透過大括號 `{}` 來切分，是存在於區塊（block）內，若其宣告的變數所在作用域不同，就不算重複宣告。
以上述 `for` 迴圈為例：
```jsx
for (let i = 0; i < 10; i++){
	console.log(i); // 0~9
};
console.log(i); // Uncaught ReferenceError: i is not defined
```
因為 `let` 宣告的變數有效範圍在區塊中，因此，外層無法取得 `i` 值。
### 刪除差異
在一般情況下，是否使用 `var` 最大的差別是：能否被 `delete` 刪除。
 `delete` 的用途是刪除「運算子的物件屬性」與移除「未經 `var` 宣告的全域變數」，因此，如果一個全域變數沒有使用 `var` 宣告的話，可能會很輕易的被刪除，而導致系統出現問題。
而 `let` 與 `const` 因為是區域變數，無法使用 `window` 找到相關變數，因此也無法使用 `delete` 刪除該變數。
### 小知識
- 使用 `let` 與 `const` 宣告變數是更嚴謹且備受推薦的做法。
## 了解更多
- [#30 變數宣告](https://chunjull.github.io/javascript/20231123/704880787/)：回顧三種變數宣告的方式。
- [#31 變數的有效範圍](https://chunjull.github.io/javascript/20231124/3746595863/)：回顧變數的有效範圍。
- [#32 變數提升](https://chunjull.github.io/javascript/20231125/3405801099/)：回顧 `var` 宣告的變數提升問題。
- [#33 暫時性死區](https://chunjull.github.io/javascript/20231126/1744441320/)：回顧 `let` 與 `const` 專有的暫時性死區（TDZ）問題。
- [#34 全域變數與區域變數](https://chunjull.github.io/javascript/20231127/3502683458/)：回顧全域變數與區域變數的差異。