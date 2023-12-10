---
title: '#25 函式：宣告'
category: DoJS
tags:
  - JavaScript
abbrlink: 1806621739
date: 2023-11-18 00:00:00
---
函式是物件的一種，具有可重複使用的特性。
<!--more-->
## 快速了解
函式（function）會將一或多段程式指令包裝起來，可以重複使用，也方便維護。
可以同時註冊多組函式，函式裡也可以執行其他函式。
### 函式結構
通常來說，一個函式會包含以下三個部分：
- 函式名稱（備註：也可能沒有名稱）。
- 在小括號中的部分為「參數（arguments）」，參數與參數之間會用逗號隔開（備註：不一定需要參數，但括號不可省略）。
- 大括號中則是需要「重複執行」的內容，是函式功能的主要區塊。
### 函式呼叫
所有的函式都有回傳值，回傳值可以用關鍵字 `return` 來指定。
定義為：宣告一個變數，其值為函式，待函式執行完， `return` 會將結果為傳至函式，並賦予到變數上。
如果沒有使用 `return` 回傳，預設會回傳 `undefined` 。
```jsx
return 函式名稱(參數);
```
### 函式範例
```jsx
function totalPrice(item1, item2) {
	return item1 + item2;
};
let oldList = totalPrice(25, 70); // 95
let newList = totalPrice(60, 90); // 150
```
- `function` ：使用關鍵字 `function` 宣告一個函式。
- `totalPrice` ：函式名稱。
- `(item1, item2)` ：參數。
- `return item1 + item2;` ：會回傳的執行區塊。
- `oldList` 、 `newList` ：宣告變數， `return` 會把結果傳到函式，再賦予至變數。
### 小知識
- 使用 `typeof` 檢查一個函式時，會得到 `function` 的結果。但實際上，函式仍屬於物件型別（ `object` ）。
- 參數跟變數不同，參數只存活在大括號裡。在函式外，印出參數會回傳錯誤。
- 函式可以分成兩種：不需要知道結果、需要回傳值。前者有無 `return()` 並不影響結果，通常只會用 `console.log()` 印出結果；後者則必須要透過 `return()` 得到回傳值。
## 了解更多
- [Kuro－函式的基本概念](https://ithelp.ithome.com.tw/articles/10191549)：本文最主要的參考範例。
- [MDN－函式](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Functions)：了解函式的常見用法。