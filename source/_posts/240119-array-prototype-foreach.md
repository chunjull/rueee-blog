---
title: '#87 陣列處理方法：forEach'
category: DoJS
tags:
  - JavaScript
abbrlink: 871183559
date: 2024-01-19 00:00:00
---
`forEach` 可達成多種目標，適合在「處理大筆資料」時使用。
<!--more-->
## 快速了解
處理大筆資料時，使用陣列處理方法能夠有效提升工作效率。
例如： `forEach` 可以取代 `for` 迴圈、計算陣列數字累加、讀取字串或物件等不同型別的資料，還可以搭配 `if` 條件判斷使用。
### forEach 結構
forEach 的函式結構為 `function(item, index, array)` ，第一個參數是「當前元素的值」、第二個參數是「當前元素是陣列第幾筆資料」、第三個參數是「當前元素的資料」。
特別注意！ `forEach` 不會回傳值。
```jsx
let data = [10, 20];
data.forEach(function(item, index, array){
	console.log(item, index, array);
});
// 10 0 (2)[10, 20]
// 20 1 (2)[10, 20]
```
### 範例：forEach 與 for 迴圈
當有一個陣列的內容需要依序取值時，通常會使用 `for` 迴圈的方式，將值一一取出。
```jsx
let data = [10, 20, 30, 40];
for(var i = 0; i < data.length; i++){
	const item = data[i];
	console.log(i, item)
};
// 0 10
// 1 20
// 2 30
// 3 40
```
學會 `forEach` 後，可以透過更簡潔的程式碼做到一樣的效果。
```jsx
let data = [10, 20, 30, 40];
data.forEach(function(item, index, array){
	console.log(index, item);
});
// 0 10
// 1 20
// 2 30
// 3 40
```
必須注意的是， `forEach` 並沒有像 `for` 迴圈一樣的中斷方式，故無法被中途停止運行。
## 了解更多
- [MDN－forEach](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)：了解 `forEach` 的使用方式。
- [卡斯柏－for 迴圈與 forEach 有什麼不同](https://www.casper.tw/development/2020/10/05/js-for-loop-vs-for-each/)：比較 `for` 和 `forEach` 的差異。