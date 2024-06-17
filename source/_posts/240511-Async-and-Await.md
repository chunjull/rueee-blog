---
title: '#99 Async 與 Await'
category: DoJS
tags:
  - JavaScript
abbrlink: 1983175806
date: 2024-05-11 00:00:00
---
`Async` 與 `Await` 可以協助 `Promise` 物件更有效率地處理非同步任務。
<!--more-->
## 快速了解
 `Promise` 物件延伸出兩種新特性： `Async` 與 `Await` 。
過去，使用 `Promise` 處理非同步任務時，需要透過 `.then()` 來等待結果。現在，使用 `Async` 與 `Await` 指令時，可以更簡潔地處理非同步任務，提高程式碼可讀性。
### Async
 `Async function` 可用來定義非同步函式，其回傳值為一個 `Promise` 物件。
 `Async` 函式內可以包含 `Await` 表達式。
### Await
 `Await` 表達式會暫停 `Async` 函式執行，等待 `Promise` 物件的解析，並在 `Promise` 物件的值被實現後回覆 `Async` 函式的執行， `Await` 接著會回傳該被 `resolve` 的值。
若回傳值不是一個 `Promise` 物件，則會被轉換為 `resolve` 狀態的 `Promise` 物件；而若 `Promise` 物件被 `rejected` ，則會回傳 `rejected` 的值。
### 搭配 Promise
```jsx
function example(x){
	return new Promise((resolve) => {
		setTimeout(() => {
			resolve(x);
		}, 2000);
	});
};
async function f1(){
	let x = await example(10);
	console.log(x); // 10
};
f1();
```
以上述程式碼為例：先設定函式 `example` 是一個傳給 `Await` 表達式的 `Promise` 物件，會在內容實現的「後兩秒」執行 `console.log(x);` 的任務。
## 了解更多
- [MDN－async function](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/async_function)：了解 `Async` 的意義。
- [MDN－await](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/await)：了解 `Await` 的意義。
- [oxxo－簡單理解 JavaScript Async 和 Await](https://www.oxxostudio.tw/articles/201908/js-async-await.html)：了解更多 `Async` 與 `Await` 的範例。