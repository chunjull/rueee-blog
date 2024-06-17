---
title: '#32 變數提升'
category: DoJS
tags:
  - JavaScript
abbrlink: 3405801099
date: 2023-11-25 00:00:00
---
「提升」使得變數在宣告之前被使用會回傳 `undefined` 。
<!--more-->
## 快速了解
變數提升（Variables Hoisting）會把變數和函數的宣告移動到程式區塊頂端，直到實際執行時再賦值。
看起來是將變數和函數的宣告「移動」到程式區塊頂端。但在編譯階段時，變數和函式的宣告會先被放入記憶體，實際在程式碼中位置還是一樣。
換言之，如果在宣告前使用相應的變數，瀏覽器會先將該變數「提升」至程式區塊頂端並宣告，但尚未賦值，因此，此時會印出 `undefined` ，直到程式執行到相關的宣告程式碼時，才會賦值。
舉例來說：
```jsx
var word;
console.log(word); // undefined

var word = "hello";
console.log(word); // hello
```
在宣告變數 `word` 時尚未賦值，只會印出 `undefined` 的結果；直到變數 `word` 被執行並賦值時，才會回傳 `hello` 的結果。
### 進階案例
```jsx
var x = 1;
var doSomeThing = function(y){
	console.log(x); // ?
  var x = 100;
  return x + y;
};
console.log(doSomeThing(50)); // 150
console.log(x); // 1
```
在這個案例中， `console.log(x)` 的回傳值會是 `undefined` 。
因為，對瀏覽器來說，這時的程式碼會呈現下面的樣子：
```jsx
var x = 1;
var doSomeThing = function(y){
	var x;
	console.log(x); // ?
  x = 100;
  return x + y;
};
console.log(doSomeThing(50)); // 150
console.log(x); // 1
```
JS 會先在自己的作用域尋找變數 `x` ，發現在下面的 `var x = 100` 有宣告，就只會把「宣告的語法」提升到該作用域（即這個案例的 `function` ）的最上面，因此只會印出 `undefined` 的結果。
### 解決方式
為了解決 JS 「變數提升」的奇怪特性，建議使用以下兩種方式：
1. 先宣告再使用，所有可能用到的變數都盡量在「作用域的最上面」宣告完成後再使用。
2. 使用 ES6 的 `let` 或 `const` 代替，因為 `let` 宣告的變數不會有變數提升的特性。
### 小知識
- 只有宣告的變數會提升，賦值不會提升。
## 了解更多
- [Kuro－函式的基本概念](https://ithelp.ithome.com.tw/articles/10191549)：本文最主要的參考範例。
- [MDN－提升](https://developer.mozilla.org/zh-TW/docs/Glossary/Hoisting)：了解變數提升的概念。
- [阿建－JavaScript 提升(Hoisting)是什麼?關於提升的5個觀念](https://jianline.com/javascript-hoisting/)：了解變數提升的概念。
- [Huli－我知道你懂 hoisting，可是你了解到多深？](https://blog.techbridge.cc/2018/11/10/javascript-hoisting/)：深入了解變數提升的概念。