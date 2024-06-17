---
title: '#109 事件循環'
category: DoJS
tags:
  - JavaScript
abbrlink: 962447775
date: 2024-05-21 00:00:00
---
事件循環搭配非同步請求，使 JS 可以同時處理多個任務。
<!--more-->
## 快速了解
事件循環（Event Loop）是 JS 的一種機制，目的為處理非同步（Asynchronous）執行的程式碼。
事件循環會監控執行堆疊（Call Stack）和工作佇列（Callback Queue），當堆疊沒有執行項目、是空的時，其會把佇列中的內容拉到堆疊中執行。
### 回顧 JS 執行環境
前面章節介紹過：JS 是一種「單執行緒」的程式語言，具有同步執行（synchronous）的特性，一行程式碼執行完畢才會再執行下一行。此種方式可能會因為程式碼需要長時間等待執行，而使頁面看起來像「卡住」而發生「阻塞」（Blocking）的現象，因此，可以透過非同步（Asynchronous）來處理這個問題。
相較於一次執行一件事，一件一件接著做的「同步」（synchronous）觀念，「非同步」（Asynchronous）的意義則是：很多件事件一起開始做，會結束在不一樣的時間點。
實際上在 JS 的執行環境（Runtime），一次只能執行一件事，前一件任務完成才會接續進行後面任務，但 JS 引擎與瀏覽器提供了多種 API 使用，讓開發者可以透過事件循環搭配非同步的方式，同時處理多個任務。
瀏覽器提供的 API （Web APIs）包含： `document` 、 `XMLHttpRequest` 、 `setTimeout` 等，它們不會引響到 JS 主程式的運作，且可以和這些程式碼同時一起執行（Concurrency）。
### 事件循環的流程
說明「事件循環」倒底是什麼之前，先來了解與其相關聯的幾個觀念：
- 執行堆疊（Call Stack）：程式中要執行的函式會在此處堆疊，採取「後進先出」的原則，會從全域的主程式開始，逐一把各個待執行函式堆至「執行堆疊」的最上方，並從最後進入的函式開始執行，直到此堆疊清空。
- Web APIs： `document` 、 `XMLHttpRequest` 、 `setTimeout` 等 API，使 JS 可以同時處理多項任務。當完成 Web APIs 的函式後，便會將任務傳遞至工作佇列。
- 工作佇列（Callback Queue / Task Queue）：存放回呼函式（Callback function）的地方，採取「先進先出」的規則，會接收從 Web APIs 傳來的任務，並透過事件循環的監控，當堆疊中沒有執行項目時，便會把佇列中的任務拉進堆疊中執行。
從上述觀念可以得知：事件循環（Event Loop）的任務是「持續查看執行堆疊是否還有任務尚未執行，若堆疊中所有任務都已完成，則會把工作佇列中的任務拉進堆疊中執行」。
### 事件循環的重要性
綜合上述內容，可以歸納出兩個事件循環的重要性：
1. 事件循環協助非同步請求的實現，並產生連貫的畫面呈現，減少頁面因「阻塞」（Blocking）而卡頓的情況。
2. 事件循環將「費時較久」或「需等待事件才能啟動」的任務往後安排，以打造連貫的使用者體驗。
### 小知識
- 事件循環不存在於 JS 本身，而是由 JS 執行環境（如：瀏覽器）來實現。
## 了解更多
- [MDN－並行模型和事件循環](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Event_loop)：了解事件循環的意義。
- [JSConfEU Philip Roberts－所以說 event loop 到底是什麼玩意兒？](https://www.youtube.com/watch?v=8aGhZQkoFbQ)：了解 JS 的完整運行方式。
- [itsems－Javascript 的事件循環 (Event Loop)、事件佇列 (Event Queue)、事件堆疊 (Call Stack)：排隊](https://medium.com/itsems-frontend/javascript-event-loop-event-queue-call-stack-74a02fed5625)：了解 JS 執行環境。
- [PJCHENder－理解 JavaScript 中的事件循環、堆疊、佇列和併發模式](https://pjchender.dev/javascript/js-event-loop-stack-queue/)：了解 JS 執行環境與延伸使用。
- [郭耿綸 Kaleb－到底 Event Loop 關我啥事？](https://medium.com/infinitegamer/why-event-loop-exist-e8ac9d287044)：了解事件循環與延伸問題。
- [ExplainThis－請說明瀏覽器中的事件循環 (Event Loop)](https://www.explainthis.io/zh-hant/swe/what-is-event-loop)：了解事件循環的意義與重要性。
- [ExplainThis－最常見的事件循環 (Event Loop) 面試題目彙整](https://www.explainthis.io/zh-hant/swe/js-event-loop-questions)：事件循環考題練習。
- [#90 JS 執行環境](https://chunjull.github.io/javascript/20240502/453057554/)：回顧 JS 執行環境與執行堆疊的特性。