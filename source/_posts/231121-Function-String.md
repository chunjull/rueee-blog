---
title: '#28 常用的內建函式：String'
category: DoJS
tags:
  - JavaScript
abbrlink: 1909286593
date: 2023-11-21 00:00:00
---
學習 `String` 內建函式，可以讓程式碼更簡潔。
<!--more-->
## 快速了解
內建函式可以讓程式碼更簡潔，但並非必要，使用一般程式碼也可以完成這些功能。
以下分享一些 `String` 常用的內建函式。

`toUpperCase` 、 `toLowerCase` ：將字串轉換大、小寫。
```jsx
console.log(("abc".toUpperCase())); // ABC
console.log(("ABC++".toLowerCase())); // abc++
```

`.charCodeAt()` ：取得字串特定位置的字元 ASCII 編碼。
```jsx
console.log("ABC".charCodeAt(0)); // 65（A 的編碼）
console.log("cba".charCodeAt(3)); //  97（a 的編碼）
```

`String.fromCharCode()`：將 ASCII 編碼的數字轉換成字元。
```jsx
console.log((String.fromCharCode(65))); //  A
var str = String.fromCharCode("Abc".charCodeAt(0) + 32);
console.log(str); // a
```

`indexOf()` ：可回傳「指定字串」在字串中第一次出現的位置，若找不到則回傳 `-1`。
```jsx
var str = 'hey hello world';
var index = str.indexOf('hello');
console.log(index); // 印出 4，hello 第一次出現在 index = 4

var index = str.indexOf('hello!!');
console.log(index); // 印出 -1，代表字串不存在
```

`replace()` ：取代字串，只能換第一個指定字串。
```jsx
var str = 'hey hey hello world'.replace('hey', '!!!');
console.log(str); // !!! hey hello world
```

`split()` ：透過「指定分隔符」來分開字串，回傳值為陣列。
```jsx
var str = 'data1,data2,data3';
var arr = str.split(',');
console.log(arr); // ['data1', 'data2', 'data3']
```

`trim()` ：移除目前字串開頭和結尾的所有空格。
```jsx
var str = '   data1,data2,data3   ';
console.log(str.trim()); // data1,data2,data3
```

`string.length` ：可回傳字串長度，常搭配迴圈使用。備註：此指令不是函式。
```jsx
var str = 'hello world';
console.log(str.length); // 11

// 迴圈應用，在每行印出第 i 個字元
for (var i = 0; i < str.length; i++){
  console.log(str[i]);
};
```
### ASCII
ASCII 是「美國標準資訊交換碼」，每一個可顯示字元都有自己專屬的索引，大、小寫字母的索引相差 32。

利用 ASCII code 進行字串比大小，可判斷該字元為大小寫、是否在條件範圍內：
```jsx
var char ='J';
console.log(char >= 'A' && char <= 'Z'); // 印出 true，判斷為大寫

var char ='g';
console.log(char >= 'A' && char <= 'Z'); // 印出 false，判斷為小寫
```

如果想要取代「所有的」指定字串，可以使用正規表達式（Regular expressions）達成：
```jsx
var str = 'hey hey hello world'.replace(/hey/g, '!!!')
console.log(str); //  !!! !!! hello world
```
## 了解更多
- [MDN－String](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/String)：了解 `String` 的常見函式。
- [維基百科－ASCII](https://zh.wikipedia.org/wiki/ASCII)：了解 ASCII 編碼的意義。
- [MDN－正規表達式](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Regular_Expressions)：了解正規表達式的使用方式。