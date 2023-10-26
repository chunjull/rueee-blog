---
title: "#1 JS 是什麼？"
date: 2023-10-25
category: JS 一分鐘
tags:
 - JavaScript
---
JavaScript 不是魔法，而是一種實現多樣化功能的程式語言。
<!-- more -->
## 快速了解
### JS 是什麼樣的程式語言？
- JS 是一種腳本程式語言，具有簡單、易學、易用的特性。
- JS 是一種直譯式語言，其程式碼由上到下執行，且能夠立即得到執行結果。
- JS 是一種動態程式，會在瀏覽器上調整 HTML 與 CSS，以產生新的內容，並在頁面中呈現。因為此特性，使它必需在 HTML、CSS 之後載入，否則可能會發生錯誤。
### JS 的功能
JS 可以在網頁中展現複雜的動態功能，例如：表單驗證、彈跳動畫等互動行為。
基礎的 JS 可以進行四則運算、數字排序、判斷大小寫等。
若加上應用程式介面（API），還能提供 JS 額外的功能，例如：內容即時更新、繪製 2D/3D 圖形、影片播放控制。
### JS 的使用方式
JS 主要有兩種載入方式：內部與外部。
- 內部的 JS：在 HTML 檔案的 `</head>` 結尾標籤前加入以下文字。
  ```html
  <script>
    // JavaScript 內容
  </script>
  ```

- 外部的 JS：建立一個以 .js 為副檔名的檔案，將 JS 內容寫在該檔案內，並在 HTML 檔案的 `</head>` 結尾標籤前加入以下文字。
  ```html
  <script src="filename.js"></script>
  ```

JS 有兩種註解方式：單行和多行。
- 單行註解：文字寫在兩個斜線「//」之後。
  ```javascript
  // 我是一個註解
  ```

- 多行註解：文字寫在 /* 和 */ 之間。
  ```javascript
  /*
    我也是
    一個註解
  */
  ```
## 了解更多
- [MDN－JavaScript 是什麼？](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/First_steps/What_is_JavaScript)：詳細說明 JS 的能力與使用方式。
- [MuleSoft Videos－What is an API?](https://www.youtube.com/watch?v=zvKadd9Cflc)：了解 API 在網頁中扮演的角色與功能。