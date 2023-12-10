---
title: '#27 常用的內建函式：Number'
category: DoJS
tags:
  - JavaScript
abbrlink: 576908797
date: 2023-11-20 00:00:00
---
學習 `Number` 內建函式，可以讓程式碼更簡潔。
<!--more-->
## 快速了解
內建函式可以讓程式碼更簡潔，但並非必要，使用一般程式碼也可以完成這些功能。
以下分享一些 `Number` 常用的內建函式。

`Number()` ：將字串轉數字。
```jsx
var a = 1;
var b = "4";
console.log(a + Number(b)); // 5
```

`parseInt()` ：將字串轉整數，預設為十進位，例如：`parseInt(a, 10)` 。
```jsx
var a = "12.34";
console.log(parseInt(a)); // 12
```

`parseFloat()` ：將字串轉浮點數，即有小數點。
```jsx
var a = "12.34";
console.log(parseFloat(a)); // 12.34
```

`toFixed()` ：取到小數點後第幾位，括號內不輸入就會取整數。
```jsx
var a = "12.345";
console.log(parseFloat(a).toFixed(2)); // 12.35
```

`.toString()`：數字轉字串。
```jsx
var a = 1;
console.log(a.toString()); // 1
```

`Number.MAX_VALUE` 、 `Number.MIN_VALUE` ：得知在 JS 可儲存的最大、最小值，若超出這個值，計算就會不精準。
```jsx
console.log(Number.MAX_VALUE)
// 1.7976931348623157e+308
console.log(Number.MIN_VALUE)
// 5e-324
```

`Math.PI` ：圓周率。
`Math.ceil()` ：無條件進位，取大於這個數的最小整數。
```jsx
console.log(Math.ceil(2.34)); // 3
```

`Math.floor()` ：無條件捨去，取小於這個數的最大整數。
```jsx
console.log(Math.floor(3.9)); // 3
```

`Math.round` ：四捨五入。
```jsx
console.log(Math.round(5.59)); // 6
```

`Math.sqrt()`：開根號。
```jsx
console.log(Math.sqrt(9)); // 3
```

`Math.pow(x, y)`：次方，取 x 的 y 次方。
```jsx
console.log(Math.pow(2, 10)) // 1024，即 2 的 10 次方
```

`Math.random` ：產生 0～1 之間的隨機小數（不包含 1） 。
```jsx
console.log(Math.random()); // 0~1 隨機數
console.log(Math.floor(Math.random() * 10 + 1));
// 乘以十可產生 0~10 的隨機數（不包含 10）
// 無條件捨去，可產生 1~10 的整數
```
### 小知識
- 常數會用大寫英文字母表示，例如： `PI` 。
- `toFixed()` 常與 `parseFloat()` 搭配使用。
- 數字轉字串的另一個方式：數字加空字串（ `''` 或 `""` ）。
## 了解更多
- [MDN－Number](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Number)：了解 `Number` 的常見函式。
- [MDN－Math](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Math)：了解 `Math` 的常見函式。