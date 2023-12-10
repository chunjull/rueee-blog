---
title: "#9 物件型別：陣列"
category: DoJS
tags:
  - JavaScript
abbrlink: 712042596
date: 2023-11-02 00:00:00
---
陣列是有順序性的集合，透過內建函式可以新增、刪除陣列中的元素。
<!--more-->
## 快速了解
陣列可被視為一種特別的「物件」，同樣是零至多個元素的集合，其值可以是原始的資料型別、另一個陣列、物件甚至函式。
與物件不同，陣列是**有順序性的集合**。
### 建立陣列
陣列有兩種宣告方式：建構式與陣列實字。

建構式：用 new 關鍵字加上 `Array()` 來宣告一個物件。
```jsx
var myArray = new Array();
```
陣列實字：用 `[]` 就可以宣告一個物件。
```jsx
var myArray = [];
var fruitList = ["apple", "banana", "orange"];
```
### 陣列索引
陣列索引是**由 0 開始計算**，以下方案例來說，陣列索引依序是 0、1、2、3。
陣列長度則可以透過 `array.length` 得知。
```jsx
var items = ["shoes", "shirts", "socks", "sweaters"];
items.length; // 4
```
### 陣列元素取值
陣列元素的取值方式為 `array[number]` ，number 指元素的索引值。舉例來說：陣列的第一個元素，要透過 `array[0]` 取得。
```jsx
var array = ['a' ,'b', 'c', 'd'];
console.log(array[0]); // 'a'
console.log(array[3]); // 'd'
```
### 新增元素
陣列有兩種新增元素的方式： `push()` 、 `unshift()` 。

`push()` ：加入項目至陣列末端。
```jsx
var array = ["apple", "banana", "cat", "dag"];
array.push("elf");
console.log(array); // ["apple", "banana", "cat", "dag", "elf"]
```
`unshift()` ：加入項目至陣列前端。
```jsx
var array = ["apple", "banana", "cat", "dag"];
array.unshift("zero"); 
console.log(array); // ["zero", "apple", "banana", "cat", "dag"]
```
### 刪除元素
陣列有三種刪除元素的方式： `pop()` 、 `shift()` 、 `splice()` 。

`pop()` ：移除陣列末端的項目。
```jsx
var array = ["apple", "banana", "cat", "dag"];
array.pop();
console.log(array); // ["apple", "banana", "cat"]
```
`shift()` ：移除陣列前端的項目。
```jsx
var array = ["apple", "banana", "cat", "dag"];
array.shift();
console.log(array); // [banana", "cat", "dag"]
```
`splice()` ：移除指定索引位置的項目，並可指定欲移除其後的多少個項目。
```jsx
var array = ["apple", "banana", "cat", "dag"];
array.splice(1, 2);
console.log(array); // ["apple", "dag"]
```
### 陣列判斷
使用 `typeof` 檢查一個陣列，會得到 `“object”` 的結果。
當我們要檢查一個變數是陣列而非物件時，可以透過 `isArray()` 的方法判斷：
```jsx
Array.isArray([]); // true
Array.isArray([1, 2, 3]); // true
Array.isArray(); // false
Array.isArray({name: 'ABC', number: 100}); //false
```
### 小知識
- `array.length` 的值可被覆寫，因此，陣列長度可以透過改變 `length` 屬性而更動。
## 了解更多
- [MDN－Array](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array)：了解陣列的更多應用。
- [MDN－Array.length](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/length)：熟悉 `array.length` 的操作邏輯。
- [卡斯柏－JS 常見陣列方法](https://www.casper.tw/development/2020/10/04/js-array-methods/)：理解 JS 常見的陣列方法。