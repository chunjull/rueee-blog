---
title: '#8 物件型別：物件'
category: DoJS
tags:
  - JavaScript
abbrlink: 3927311135
date: 2023-11-01 00:00:00
---
物件型別對於 JS 來說是非常重要且容易混淆的概念，其包含物件、陣列、函式等值。
<!--more-->
## 快速了解
複習一下，除了六種基本型別之外的值，都可以被歸類為「物件型別」。因此，物件、陣列、函式都屬於物件型別。
### 物件定義
一個物件（object）可以是個零至多種屬性的集合，而屬性是名稱（name）與值（value）之間的關聯。
一個屬性的「值」可以是某個基本型別，也可以是另一個物件，甚至是一個函式。
物件內容來源有兩種：瀏覽器預先定義、開發者自己定義。
- 瀏覽器或執行環境預先定義，例如：`window`、`Date`、`Math` 等物件。
- 開發者自己定義物件的屬性與內容。
### 建立物件
物件有兩種宣告方式：物件建構式與物件實字。

物件建構式：用 new 關鍵字加上 `Object()` 來宣告一個物件。
```jsx
var myObj = new Object();
```
物件實字：用 `{}` 就可以宣告一個物件。
```jsx
var myObj = {};
```
### 物件屬性取值
物件的屬性有兩種取值方式：點記法與括弧記法。

點記法：使用 `.` （點）進行取值，語法為 `objectName.propertyName`。
```jsx
var person = {
	name: 'Tom',
	gender: 'Male',
	age: 44
};
person.name; // 'Tom'
person.age; // 44
```
括弧記法：使用 `[]` （中括弧）進行取值，語法為 `objectName["propertyName"]`。
```jsx
var friutShop = {
	appleNum: 23,
	bananaNum: 8,
	orangeNum: 10
};
fruitShop["orangeNum"]; // 10
```
### 新增屬性
使用 `=` （等號）指定，即可為物件新增屬性。
```jsx
var obj = {name: 'ABC'};
obj.number = 100;
obj.number; // 100
obj; // {name: 'ABC', number: 100}
```
### 刪除屬性
使用 `delete` 關鍵字，即可刪除屬性。
屬性刪除後，該變數的值會變成 undefined。
```jsx
var obj = {name: 'ABC', number: 100};
delete obj.number;
obj.number; // undefined
obj; // {name: 'ABC'}
```
### 小知識
- 因為 JSON 的特性，當屬性名稱是數字開頭時，使用點記法取值會出現錯誤，例如：`”001”` 。這時就必須改成括弧記法 `objName[”001”]` 的方式才能正確存取值。
- 當我們存取物件中不存在的屬性時，會回傳 undefined。因此，可以透過檢查某屬性是否為 undefined，來判斷屬性是否存在。除了此方式，還有兩種進階方法：`in` 運算子與 `hasOwnProperty()` 函式。
## 了解更多
- [卡斯柏－JS 物件名詞解釋及常見觀念問題](https://www.casper.tw/development/2020/09/21/js-object/)：了解物件相關知識。
- [JSON 精要讀書紀錄－JSON 語法](https://miniaspreading.github.io/guide-to-json/2-json-syntax.html)：預習 JSON 格式的使用方式。
- [MDN－關係運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Expressions_and_operators#%E9%97%9C%E4%BF%82%E9%81%8B%E7%AE%97%E5%AD%90)：`in` 運算子判斷屬性是否存在。
- [MDN－Object.prototype.hasOwnProperty()](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)：`hasOwnProperty()` 函式判斷屬性是否存在。