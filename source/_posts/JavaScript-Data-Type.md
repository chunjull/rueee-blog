---
title: "#4 資料型別簡介"
date: 2023-10-28
category: JS 一分鐘
tags:
 - JavaScript
---
變數沒有型別，值才有。
<!--more-->
## 快速了解
變數本身不帶有資料型別的資訊，其中的「值」或「物件」才有。換句話說，變數只是用來作為取得值或物件的參考。
JS 的資料型別分為兩大類：基本型別（Primitives）與物件型別（Object）。
### 型別整理
JS 總共有七種資料型別：六種基本型別及一種物件型別。
| 資料型別 | 說明 |
| --- | --- |
| String | 字串。 |
| Number | 數字，可以是整數或小數。 |
| Boolean | 布林值，只有 true、false 兩種。 |
| null | 空值，表示參考值不存在。 |
| undefined | 未定義，宣告變數卻未指派內容給它。 |
| symbol | 符號，表示獨一無二的值。 |
| object | 物件、陣列、函式都屬於物件型別。 |
### 型別判斷
可以透過 `typeof` 運算子判斷型別。
```javascript
typeof "abc"; // string
typeof 1200; // number
typeof true; // boolean
typeof undefined; // undefined
typeof { }; // object
typeof [ ]; // object
```
### 小知識
- JS 是一種「弱型別語言」，宣告變數時，可以不指定該值的資料型別。編譯時，JS 會將該變數轉換成「可以被執行」的資料型別，並強制執行。
## 了解更多
- [MDN－資料結構與型別](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Grammar_and_types#%E8%B3%87%E6%96%99%E7%B5%90%E6%A7%8B%E5%8F%8A%E5%9E%8B%E5%88%A5)：了解 JS 各資料型別的基本內容。
- [Yi-Ning－關於 JavaScript 的弱型別特性](https://medium.com/@yining1204/%E9%97%9C%E6%96%BCjavascript%E7%9A%84%E5%BC%B1%E5%9E%8B%E5%88%A5%E7%89%B9%E6%80%A7-93ffcdcf623e)：了解弱型別語言的定義。