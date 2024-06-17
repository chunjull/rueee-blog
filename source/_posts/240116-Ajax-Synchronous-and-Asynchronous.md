---
title: '#84 Ajax：同步與非同步'
category: DoJS
tags:
  - JavaScript
abbrlink: 3831438034
date: 2024-01-16 00:00:00
---
同步的 JS 一次只能做一件事；非同步的 JS 則可以在同時做多件事。
<!--more-->
## 快速了解
在了解「非同步」的概念前，先解釋什麼是「同步 JS」。
### 同步的 JS
同步 JS（Synchronous JavaScript）指：用戶端對伺服器端送出 request ，且在收到伺服器端的 response 之後才會繼續下一步的動作，伺服器端在同一時間只能做一件事件，等待的期間無法處理其他事情。簡單來說，同步的 JS 是「一次只做一件事」。
若程式都是同步執行的話，會導致網頁的阻塞（Blocking）現象，使得網頁看似當掉、沒有回應，實際上是因為上一件事還沒有完成，所以下一件事情等著尚未執行。
### 非同步的 JS
非同步 JS（Asynchronous JavaScript）則是指：用戶端向伺服器端送出 request 之後，不需要等待結果，仍可以持續處理其他事情，甚至繼續送出其他 request。Response 回傳後，就被融合進當下頁面或應用中。簡單來說，非同步 JS 是「同時可以做很多件事情」。
非同步 JS 有兩種回呼方式：較舊的 callback function 與較新的 `promise` 。如今，callback 已較少被使用。
## 了解更多
- [MDN－非同步的 JS](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/Asynchronous/Introducing)：了解 JS 同步與非同步的意義。