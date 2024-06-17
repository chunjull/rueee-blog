---
title: '#44 DOM 環境配置'
category: DoJS
tags:
  - JavaScript
abbrlink: 2560653094
date: 2023-12-07 00:00:00
---
將 `<script>` 標籤放在 `</body>` 之前，才能讓網頁被完整解析成 DOM tree。
<!--more-->
## 快速了解
通常來說，JS 的 `<script>` 標籤有兩種擺放位置：
- 放在 `<head> ... </heade>` 之間。
- 放在 `</body>` 之前。
然而，放在 `<head> ... </heade>` 之間的 JS 卻可能無法作用，這跟瀏覽器的執行原理有關。
### 瀏覽器執行原理
當網頁被載入到瀏覽器時，瀏覽器會先分析該 HTML 檔案，**由上往下**依序讀取分析。
如果瀏覽器在 `<head> ... </heade>` 之間遇到 `<script>` 標籤，就會暫停解析網頁，並且立即執行 `<script>` 裡的內容，直到所有內容都執行完畢後，才會再繼續解析網頁。
這樣的情況會導致 JS 無法作用的結果，因為在 `<head> ... </heade>` 之間的 `<script>` 試圖去尋找「尚未被解析到的 HTML 內容」，卻無從取得，最後只能呈現「JS 無法作用」的狀態。
但如果瀏覽器是在 `</body>` 之前才讀取到 `<script>` 標籤，由於該網頁已經解析成 DOM 節點，使 JS 可以順利操作網頁節點，成功顯示開發者欲展現的內容。
## 了解更多
- [Kuro－透過 DOM API 查找節點](https://ithelp.ithome.com.tw/articles/10191765)：本文最主要的參考範例。
- [#43 DOM 的差別與重要性](https://chunjull.github.io/javascript/20231206/1110551957/)：回顧網頁載入流程。