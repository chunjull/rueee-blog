---
title: '#98 Promise'
category: DoJS
tags:
  - JavaScript
abbrlink: 1163736102
date: 2024-05-10 00:00:00
---
`Promise` 物件表示一個「或已實現、或以拒絕」的函式結果。
<!--more-->
## 快速了解
ES6 新增了一種名為 `Promise` 的特殊物件，使用目的為：表示非同步運算的最終結果是成功或失敗。
換句話說， `Promise` 的任務是確保「非同步函式的結果」可以用已被預期的方式處理：要不是被履行（resolve），就是被拒絕（reject）。
### Promise 結構
透過新增一個 `Promise` 物件，搭配箭頭函式的方式，可以展示成功或失敗的最終結果。
```jsx
const firstPromise = new Promise((resolve, reject) => {
	resolve(someValue); // 完成
	reject("failure reason"); // 拒絕
});
```
另外，如果要提供一個函式 `Promise` 功能，可以透過讓它回傳一個 `Promise` 物件來達成：
```jsx
function myAsyncFunction(url){
	return new Promise((resolve, reject) => {
		// resolve() or reject()
	});
};
```
當 `Promise` 被完成時，可以呼叫 `resolve()` ，再將取得的資料傳遞出去；當拒絕 `Promise` 時，則呼叫 `reject()` 來拒絕。
### Promise 狀態
pending, fulfilled, rejected, `.then()` 
一般來說， `Promise` 物件有以下三種狀態：
- pending：初始狀態，不是 `fulfilled` 或 `rejected` 。
- fulfilled：表示操作成功完成。
- rejected：表示操作失敗。

此外，還可以透過 `.then()` 依序串連執行多個 `Promise` 功能。

```jsx
var p1 = new Promise((resolve, reject) => {
  resolve("Success!");
});

p1.then(
  (value) => {
    console.log(value); // Success!
  },
  (reason) => {
    console.log(reason); // Error!
  },
);
```
### Promise 方法
 `Promise` 有兩種較常見的處理方法： `Promise.all` 與 `Promise.race` 。
- `Promise.all` 的功能為：直到目標函式都回覆 `resolve` 才會繼續後續行為。然而，當執行過程中，只要有任何一個 `Promise` 物件發生錯誤例外，或是有 `Promise` 發生 `reject` 情況，就會立即回傳一個 `rejected` 狀態的 `Promise` 物件。此方法不在乎目標函式的先後順序，只關心其是否都已經完成。
- `Promise.race` 的功能為：只要有其中一個目標函式被 `resolve` ，就會執行下一步驟。雖然，只要有一個函式完成任務，就會進行後續行為，但這不表示「其他未完成的函式會取消任務」，這些函式仍然會被執行。
## 了解更多
- [Kuro－同步與非同步](https://ithelp.ithome.com.tw/articles/10194569)：本文最主要的參考範例。
- [MDN－使用 Promise](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Using_promises)：了解如何使用 `Promise` 。
- [MDN－Promise](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Promise)：了解更多的 `Promise` 使用規則。
- [MDN－Promise.all](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)：了解 `Promise.all` 的意義。
- [MDN－Promise.race](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)：了解 `Promise.race` 的意義。
- [MDN－.then()](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)：了解 `.then()` 的意義。