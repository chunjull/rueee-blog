---
title: '#56 BOM：window 物件'
category: DoJS
tags:
  - JavaScript
abbrlink: 860044878
date: 2023-12-19 00:00:00
---
`window` 物件是 BOM 核心，在每一個頁面中都是獨立存在的。
<!--more-->
## 快速了解
BOM 的核心是 `window` 物件，它只要是作為「全域物件」和「瀏覽器溝通窗口」存在。
### BOM 的角色
DOM 是開發者用來操作網頁元素的關鍵，BOM 則是扮演 JS 與瀏覽器溝通的窗口。
BOM 提供開發者呼叫瀏覽器內建的功能，例如： `alert()` 對話框、控制上下頁的 `history` 、負責捲軸功能的 `scroll` 等。
### window 物件
BOM 包含了 DOM，JS 會透過瀏覽器提供的 BOM 來存取 `document` 的 DOM 模型，因此，DOM 的 `document.querySelector` 實際上是 `window.document.querySelector` ，而作為全域物件的 `window` 可以省略不寫。
瀏覽器的 JS 會透過一個全域物件來存放所有的全域變數與函式，所有全域變數都會自動成為該全域物件的「屬性」，因此，可以透過 `window` 物件去存取全域變數。
另外，每一個獨立瀏覽器視窗的 `window` 物件都是**彼此獨立**的，換句話說，原本的變數、屬性無法在另外一個新開啟的頁面存取。
### node.js 的全域物件
在 node.js 中也有全域物件的設定，但其與瀏覽器中的 JS 不同。
 node.js 的全域物件名稱為 `global` ，且即使在全域作用範圍下宣告變數，它也不會成為 `global` 物件下的屬性。
```jsx
var msg = "hello";
console.log(global.msg); // undefined
```
因為「在全域作用範圍下宣告變數不會成為 `global` 物件屬性」的特性，在 node 環境中執行上述程式碼，只會得到 `undefined` 的結果。
### 小知識
- 通常來說，原本的變數、屬性無法在另外一個新開啟的頁面存取，但 SPA 單頁式應用與 `localStorage/cookie` 等情況例外。
## 了解更多
- [Mike Huang－localStorage 的使用](https://medium.com/%E9%BA%A5%E5%85%8B%E7%9A%84%E5%8D%8A%E8%B7%AF%E5%87%BA%E5%AE%B6%E7%AD%86%E8%A8%98/javascript-localstorage-%E7%9A%84%E4%BD%BF%E7%94%A8-e0da6f402453)：了解 `localStorage` 的基礎運用。
- [#41 BOM](https://chunjull.github.io/javascript/20231204/3425939589/)：回顧 BOM（瀏覽器物件模型）的內容。