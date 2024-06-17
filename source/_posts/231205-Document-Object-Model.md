---
title: '#42 DOM'
category: DoJS
tags:
  - JavaScript
abbrlink: 2401154791
date: 2023-12-05 00:00:00
---
DOM API 讓 JS 可以對操作網頁內容。
<!--more-->
## 快速了解
DOM（Document Object Model），文件物件模型，是一個將 HTML 文件以樹狀結構來呈現的模型。其組合起來的樹狀圖被稱為「DOM tree」。
DOM 會把 HTML 文件行程一個個「節點」（node），再組成一個樹狀結構。
在最根部的位置，是 `document` 。
往下延伸出 HTML 標籤節點，一個節點就是一個標籤（Element）。再往下又可以延伸出「文本節點」（Text）與「屬性節點」（Attribute）。
### DOM 選取方式
DOM API 定義了多種方法，讓 JS 可以存取、改變 HTML 架構、樣式和內容，甚至可以對節點綁定事件。
使用 JS 取得網頁中元素的方式有很多種，例如：
- 根據 id 名稱選取： `document.getElementById()` 。
- 根據元素名稱選取所有符合條件者： `document.getElementsByTagName()` 。
- 根據 class 名稱選取所有符合條件者： `document.getElementsByClassName()` 。
- 根據條件選取第一個符合條件者： `document.querySelector()` 。
- 根據條件選取所有符合條件者： `document.querySelectorAll()` 。
總結來說，JS 就是透過 DOM 提供的 API 來對 HTML 進行存取與操作。
### 小知識
- `document` 是 `window` 物件的其中一種屬性。
## 了解更多
- [Kuro－前端工程師的主戰場：瀏覽器裡的 JavaScript](https://ithelp.ithome.com.tw/articles/10191666)：本文最主要的參考範例。
- [陳奕帆 Andy Chen－深入理解網頁架構：DOM](https://ithelp.ithome.com.tw/articles/10202689)：了解 DOM tree 的結構。