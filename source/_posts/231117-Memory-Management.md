---
title: '#24 變數儲存模型'
category: DoJS
tags:
  - JavaScript
abbrlink: 1831802184
date: 2023-11-17 00:00:00
---
記憶體儲存概念：一般的東西存資訊，物件存記憶體位置。
<!--more-->
## 快速了解
說到「變數資料」與「記憶體存放」的觀念，就必須先了解：在任何一個程式語言中，操作資料前，你會需要先找到一個地方放置這些資料，這個地方就是「變數」。
變數會提供一個「暫時儲存資料」的地方，透過一個可以識別的名字，將資料寫進記憶體。
### 記憶體存放流程
變數與資料操作的實際情況，在電腦上發生的是：
- 你在記憶體上宣告（declare）了一組變數。
- 你在記憶體上創建（create）了一筆資料。
- 變數指向（assign）這筆資料。
以下列程式碼為例：
```jsx
let appleColor = "red";
```
使用 `let` 的方式，宣告一個名為 `appleColor` 的變數，並對應到一筆 `"red"` 的資料。
### 物件型別的情況
如果想存物件或陣列，變數裡面存的內容是「指引」或「指標」，是前往某個記憶體位置的指引。
換句話說，基本型別的變數存資訊，物件則存在記憶體位置。
## 了解更多
- [Huli－從博物館寄物櫃理解變數儲存模型](https://hulitw.medium.com/variable-and-frontdesk-a53a0440af3c)：最白話的案例帶你了解變數儲存。
- [MDN－記憶體管理](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Memory_management)：深入了解 JS 的記憶體管理。
- [ALPHACamp－變數與值](https://javascript.alphacamp.co/variable-and-value.html)：複習變數與值的關係。