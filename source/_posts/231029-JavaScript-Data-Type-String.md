---
title: '#5 基本型別：字串'
category: DoJS
tags:
  - JavaScript
abbrlink: 3345115497
date: 2023-10-29 00:00:00
---
字串型別原本專門儲存、處理文字，樣板字面值的出現，大幅提升字串的靈活度。
<!--more-->
## 快速了解
在 JS 中，文字會以字串表示。
### 字串使用方式
字串會用一組單引號 `’’` 或雙引號 `””` 包住，且兩者不可混用。
```jsx
var str = '這是一個字串';
var str2 = "這也是一個字串";
```
在單引號中包覆單引號，或在雙引號中包覆雙引號都會出現問題。
如果非用不可，可以透過跳脫字元 `\` 處理：
```jsx
var str = 'Let's go!'; // 會出錯
var str2 = "Let's go!"; // OK
var str3 = 'Let\'s go!'; // OK
```
遇到多組字串時，可以透過加號 `+` 連接：
```jsx
var hello = 'Hello, ' + 'world!'; 
console.log(hello);
// Hello, world!
```
或是在多行字串時，使用反斜線 `\` 連結：
```jsx
var hi = 'Hello, \
I\'m Juby. \
Nice to meet you.';
console.log(hi);
// Hello,
// I'm Juby.
// Nice to meet you.
```
### 樣板字面值
樣板字元值（template literal）是 ES6 新增的特殊字串，支援多行字串、允許將變數嵌入字串，且能夠內嵌運算式，大幅提升字串的靈活度。
樣板字元值由反引號 ```` 所包覆，由一般字串、錢字號 `$` 、大括弧 `{}` 組成。

支援多行字串：
```jsx
var hi = `Hello, 
I'm Juby.
Nice to meet you.`;
console.log(hi);
// Hello,
// I'm Juby.
// Nice to meet you.
```
允許將變數嵌入字串
```jsx
var age = 20;
var str = `I am ${age} years old.`;
console.log(str);
// I am 20 years old.
```
內嵌運算式：
```jsx
var a = 2;
var b = 3;
console.log(`Five is ${a + b} and not ${2 * a + b}.`);
// Five is 5 and not 7.
```
### 小知識
- 連接多行字串時，反斜線 `\` 後方不可以有任何內容，包括空白字元。
- 反引號位於鍵盤左上方，<kbd>Esc</kbd> 底下。
## 了解更多
- [MDN－樣板字面值](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Template_literals)：了解樣板字面值的詳細內容與更多範例。
- [PJCHENder－樣板字面值](https://pjchender.dev/react-bootcamp/docs/book/ch1/1-3)：了解樣板字面值的應用。
- [菜鳥教程－HTML DOM console.log() 方法](https://www.runoob.com/jsref/met-console-log.html)：簡介 console.log 用法。