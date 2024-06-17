---
title: '#88 陣列處理方法：map、filter、find、findIndex'
category: DoJS
tags:
  - JavaScript
abbrlink: 1550320910
date: 2024-01-20 00:00:00
---
使用 `map` 、 `filter` 、 `find` 等進階的陣列處理方法，可以提升開發效率。
<!--more-->
## 快速了解
除了前面介紹過的 `forEach` ，還有許多種陣列處理方法，例如： `map` 、 `filter` 、 `find` 、 `findIndex` 等。
除了 `forEach` ，其他所有陣列方法都會回傳值。
### map
 `map()` 方法可以把原有的陣列「映射」到另一個新的陣列，並回傳新的陣列內容。
```jsx
let arrayOld = [1, 4, 9];
let arrayNew = arrayOld.map(Math.sqrt);
console.log(arrayNew);
// [1, 2, 3]
```
### filter
 `filter()` 可以搜尋符合條件的資料，會回傳一個陣列。
```jsx
let data = [1, 2, 3, 4];
function isOdd(i){
	return i % 2 !== 0;
};
let result = data.filter(isOdd);
console.log(result);
// [1, 3]
```
### find
和 `filter()` 類似， `find()` 也可以用來搜尋符合條件者，但其只會回傳第一個 `true` 的值。
```jsx
let data = [1, 2, 3, 4];
function isOdd(i){
	return i % 2 !== 0;
};
let result = data.find(isOdd);
console.log(result);
// 1
```
### findIndex
 `findIndex()` 的使用目標也和上述兩者類似，但其回傳的資料會是「索引」，而非值。
若無符合的對象，則回傳 `-1` 。
```jsx
let data = [1, 2, 3, 4];
function isBiggerThanFive(i){
	return i > 5;
};
let result = data.findIndex(isBiggerThanFive);
console.log(result);
// -1
```
### 小知識
- 除了上述介紹的陣列使用方法，還有 `every()`、`some()`、`each()` 等常見的使用方式。
## 了解更多
- [MDN－map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)：了解 `map` 的使用方式。
- [MDN－filter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)：了解 `filter` 的使用方式。
- [MDN－find](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/find)：了解 `find` 的使用方式。
- [MDN－findIndex](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)：了解 `findIndex` 的使用方式。
- [卡斯柏－JavaScript 陣列處理方法](https://www.casper.tw/javascript/2017/06/29/es6-native-array/)：了解更多陣列處理方法。