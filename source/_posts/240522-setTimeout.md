---
title: '#110 setTimeout'
category: DoJS
tags:
  - JavaScript
abbrlink: 3236465105
date: 2024-05-22 00:00:00
---
`setTimeout` 遇到事件循環時，會等待其他內容先完成，再立即執行相關程式碼。
<!--more-->
## 快速了解
在上一篇文章中，介紹過 `setTimeout` 不在 ECMAScript 的規格中，而是一種由瀏覽器提供的 Web API，且與事件循環的概念息息相關。
接下來，將會說明 `setTimeout` 是什麼？它與事件循環又有什麼關聯？以及補充介紹與 `setTimeout` 類似的 `setInterval` 概念。
### setTimeout
 `setTimeout` 的功能為：在指定的某段時間（單位為毫秒）後，才去執行「一次」指定程式碼。
```jsx
setTimeout(function sayHello(){
	console.log("Hello");
}, 3000);
```
上述程式碼會在 3 秒（即 3000 毫秒）後，執行函式 `sayHello` 的內容，再回傳字串 `Hello`。
 `setTimeout` 會先判斷第一個參數是否為函式，若是函式，會正常執行函式內容；若不是，則會嘗試將該參數當作字串處理，而如果沒有回傳值，就會以 `undefined` 作為處理。
此外，可以使用 `clearTimeout` 語法來取消 `setTimeout` 設定：
```jsx
const sayHello = setTimeout((() => console.log("Hello")), 3000);
clearTimeout(sayHello);
```
### setTimeout 與事件循環
事件循環（Event Loop）會持續查看執行堆疊是否還有任務尚未執行，若堆疊中所有任務都已完成，則會把工作佇列中的任務拉進堆疊中執行。
如果開發者使用 `setTimeout` 並且希望在 0 秒馬上執行會發生什麼事呢？
```jsx
console.log("Pikachu");
setTimeout(function saySomething(){
	console.log("Pika!");
}, 0);
console.log("Pi-ka-chu!!");
```
以上述程式碼為例，即使開發時設定 0 秒後即執行，這個回呼函式被放到工作佇列中，因為 `saySomething` 函式是最後才被放入該佇列裡，所以會等到其他堆疊內容都被清空後，才會「立即」執行這個函式。
因此，上述程式碼的印出順序會是： `Pikachu` 、 `Pi-ka-chu!!` 、 `Pika!` 。而不是先執行 `setTimeout 0` 的函式，才接續執行其他內容。
### setInterval
 `setInterval` 的功能為：固定延遲了某段時間之後，再重複執行指定程式碼。 
 `setInterval` 與 `setTimeout` 的不同之處在於：前者會在間隔固定的時間內不斷重複；後者則是執行一次就結束。
```jsx
setInterval(function sayHello(){
	console.log("Hello");
}, 3000);
```
上述程式碼會在 3 秒（即 3000 毫秒）後，重複執行函式 `sayHello` 的內容。
與 `setTimeout` 同理，可以使用 `clearTimeout` 語法來取消設定。
## 了解更多
- [Kuro－談談 JavaScript 的 setTimeout 與 setInterval](https://kuro.tw/posts/2019/02/23/談談-JavaScript-的-setTimeout-與-setInterval/)：本文最主要的參考範例。
- [MDN－setTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout)：了解 `setTimeout` 的意義。
- [MDN－setInterval()](https://developer.mozilla.org/en-US/docs/Web/API/setInterval)：了解 `setInterval` 的意義。
- [#109 事件循環](https://chunjull.github.io/javascript/20240522/3236465105/)：回顧事件循環的意義。