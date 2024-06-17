---
title: '#40 瀏覽器與 JS'
category: DoJS
tags:
  - JavaScript
abbrlink: 1229881720
date: 2023-12-03 00:00:00
---
瀏覽器提供網頁的操作方法，讓 JS 可以網頁中運作。
<!--more-->
## 快速了解
在學習前端知識時，你可能聽過這個說法：「HTML、CSS 與 JavaScript 是網頁前端三大要素」。由 HTML 負責資料與結構，CSS 負責樣式與呈現，JavaScript 負責行為與互動。
但事實上，JS 並沒有提供網頁的操作方法，前端開發者在網頁上的操作方法都由 JS 的執行平台——「瀏覽器」提供。
基本上，這些操作方法會分別由「BOM」與「DOM」這兩種物建所擁有。
因此，在瀏覽器上的 JS 包含了三個部分：
- JavaScript 核心（以 ECMAScript 標準為基礎）
- BOM（Browser Object Model，瀏覽器物件模型）
- DOM（Document Object Model，文件物件模型）
前端開發者就是透過 JS 去呼叫 BOM 與 DOM 提供的 API，再進一步透過它們去控制瀏覽器的行為與網頁的內容。
### 小知識
- 瀏覽器都會包含一個渲染引擎（rendering engine），負責解釋網頁上的程式碼，瀏覽器的 JS 解譯器就是該引擎的一部份。
## 了解更多
- [Kuro－前端工程師的主戰場：瀏覽器裡的 JavaScript](https://ithelp.ithome.com.tw/articles/10191666)：本文最主要的參考範例。