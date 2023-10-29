---
title: '#3 變數'
category: JS一分鐘
tags:
  - JavaScript
abbrlink: 1250803838
date: 2023-10-27 00:00:00
---
變數是儲存資料的容器，可以幫助我們紀錄、使用資訊。
<!--more-->
## 快速了解
### 變數是什麼？
變數（Variables）是用來儲存資料和進行運算的基本單位，可以將變數想像為一個盒子，用來存放資料。
變數儲存的資料被稱為「值」（value）。
### 變數的命名規則
- 變數的第一個字母必須是英文字母、底線（_）或錢字號（$），後面可以是英文字母、底線（_）或錢字號（$）及數字。
- 變數名稱不可以是保留字和關鍵字。
- 區分大小寫，「app」和「App」會被視為不同變數。
### 變數的宣告方式
變數有三種宣告方式：`var`、`let`、`const`。差異為變數作用範圍、能否重複宣告等。
變數必須經過宣告才能使用，如果在沒有宣告變數的情況下使用，會出現錯誤。
```jsx
var n = 1;
// 透過 var 宣告變數 n，n 值的內容為數字 1。

let m = "apple";
// 透過 let 宣告變數 m，m 值的內容為英文 apple。

const l = "卯咪";
// 透過 const 宣告變數 l，l 值的內容為中文 卯咪。
```
### 小知識
- JS 支援 Unicode，變數名稱可以用中文命名。但基於開發習慣，仍應該避免使用英文字母、底線（_）或錢字號（$）以外的字原來命名變數。
- 事實上，變數還有第四種宣告方式：無宣告。但沒有經過宣告的變數都會變成全域變數，可能會造成維護困難，因此非常不建議這麼做！
## 了解更多
- [MDN－存儲您需要的資訊 - 變數](https://developer.mozilla.org/zh-TW/docs/Learn/JavaScript/First_steps/Variables#%E4%BB%80%E9%BA%BC%E6%98%AF%E8%AE%8A%E9%87%8F%EF%BC%8F%E8%AE%8A%E6%95%B8_variable_%EF%BC%9F)：詳細說明 JS 變數的使用規則。
- [W3School－JavaScript Reserved Words](https://www.notion.so/3-b2698f71bf974ce7a39db73a9f7eb218?pvs=21)：JS 的保留字列表。
- [阿建－JavaScript 變數宣告有哪些?必須弄懂的4個重點](https://jianline.com/javascript-statements/)：了解 JS 的四種變數宣告。
- [Roy Kwok－Unicode 與 UTF-8 的關係？](https://roykwokcode.medium.com/unicode-%E8%88%87-utf-8-%E7%9A%84%E9%97%9C%E4%BF%82-1c9b7a0b7c29)：說明 Unicode 如何編譯中文字元。