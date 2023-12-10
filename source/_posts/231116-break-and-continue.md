---
title: '#23 迴圈：break 與 continue'
category: DoJS
tags:
  - JavaScript
abbrlink: 2461366595
date: 2023-11-16 00:00:00
---
`break` 和 `continue` 都能中斷迴圈，但兩者的功能並不同。
<!--more-->
## 快速了解
使用迴圈時，有時會需要跳過其中幾次或提早離開迴圈。
這時，可以使用 `break` 和 `continue` 語法。
### break 語法
 `break` 會直接跳離迴圈。
例如：在包含一堆 `0` 和其他數字的陣列中找出不是 `0` 的「第一個數字」。
```jsx
var arr = [0, 0, 0, 7, 8, 0, 2];
for (var i = 0; i < arr.length; i++) {
	if (arr[i] !== 0) {
		console.log(arr[i]);
		break;
	};
};
```
找出那個不是 `0` 的「第一個數字」，印出後再退出迴圈。
### continue 語法
 `continue` 會跳過一次，再繼續下一次的迴圈。
例如：當我們要印出 1～10 的所有正整數，但跳過 3 的倍數。
```jsx
for (var i = 1; i <= 10; i++) {
	if (i % 3 === 0) {
		continue;
	}
	console.log(i);
};
// 1, 2, 4, 5, 7, 8, 10
```
在此案例中， `i` 能被 3 整除表示 `i` 是 3 的倍數，遇到 `continue` 則會跳過。
### 小知識
- 在迴圈中，可能會常看到 `arr.length` 的類似語法，這代表「陣列的長度」，常被放在 `for` 的條件部分。
## 了解更多
- [Kuro－流程判斷與迴圈](https://ithelp.ithome.com.tw/articles/10191453)：本文最主要的參考範例。
- [MDN－break 語法](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/break)：了解 `break` 的常見用法。
- [MDN－continue 語法](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/continue)：了解 `continue` 的常見用法。
- [ALPHACamp－Loop 迴圈](https://javascript.alphacamp.co/loop.html)：了解 JS 的迴圈用法。