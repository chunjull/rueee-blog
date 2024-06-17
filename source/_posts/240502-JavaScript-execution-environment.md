---
title: '#90 JS 執行環境'
category: DoJS
tags:
  - JavaScript
abbrlink: 453057554
date: 2024-05-02 00:00:00
---
所有程式碼都必須在執行環境中運作，執行環境相互堆疊後，會形成「執行堆疊」。
<!--more-->
## 快速了解
所有程式碼都必須在執行環境（Execution Context）中執行。
當 JS 需要執行多件事項時，這些事件會「執行堆疊」，遵守「後進先出」的原則，一件、一件完成。
### 執行環境
執行環境可以分為「全域執行環境」與「函式執行環境」。
- 全域執行環境：全域環境在瀏覽器或 node.js 開啟後，執行環境會自動產生變數，也會產生 `this` ，但 `this` 會隨著執行環境而不同。
- 函式執行環境：JS 函式的作用域在該函式內部。當一個函式執行時，會產生屬於自己的執行環境，該環境會有限制作用域的功用，且有自己的 `this` 。
### 執行堆疊
JS 是一種「單執行緒」的程式語言，即一次只能做一件事，如果有太多事情要處理，JS 會將這些事情排隊堆疊，在一件件完成。以下列程式碼為例：
```jsx
function first(){
	second();
}
function second(){
	console.log("end!");
}
first();
```
這段程式碼執行堆疊的流程為：
1. 瀏覽器先建立全域執行環境。
2. 建立 `first()` 執行環境，執行 `first()` 函式內容，全域執行環境暫停。
3. 建立 `second()` 執行環境，執行 `second()` 函式內容， `first()` 函式執行環境暫停。
4.  `second()` 函式執行完成，跳出堆疊， `first()` 函式執行環境繼續。
5.  `first()` 函式執行完成，跳出堆疊，全域執行環境繼續。
### 回收機制
在函式執行環境中，會創造屬於自己的記憶體空間。
而回收機制的目的是追蹤記憶體分配的使用情況，以便自動釋放一個不再使用的記憶體空間，歸還給系統。
回收機制的演算法會將「一個不再被任何物件參考的物件」，視為可被回收的記憶體垃圾。
因此，若某函式沒有被任何物件參考，其離開執行環境的同時，也會將佔用的記憶體空間釋放出來。
### 小知識
- 在全域執行環境下，瀏覽器會產生 `window` 變數，Node.js 則產生 `global` 變數。
- 執行環境的堆疊與「函式宣告順序」無關，而是與「呼叫順序」有關聯。
## 了解更多
- [MDN－this](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/this)：預習 `this` 的概念。
- [Coding Monster－秒懂！JavaScript 執行環境與堆疊](https://medium.com/%E9%AD%94%E9%AC%BC%E8%97%8F%E5%9C%A8%E7%A8%8B%E5%BC%8F%E7%B4%B0%E7%AF%80%E8%A3%A1/%E6%B7%BA%E8%AB%87-javascript-%E5%9F%B7%E8%A1%8C%E7%92%B0%E5%A2%83-2976b3eaf248)：了解 JS 執行環境。
- [items－Javascript 的執行環境 (Execution context) 與堆疊 (Stack)](https://medium.com/itsems-frontend/javascript-execution-context-and-call-stack-e36e7f77152e)：深入了解 JS 執行環境與堆疊。
- [MDN－Memory Management](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Memory_Management)：了解記憶體管理的概念。
- [#24 變數儲存模型](https://chunjull.github.io/javascript/20231117/1831802184/)：回顧記憶體存放的概念。