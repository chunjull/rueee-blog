---
title: '#29 常用的內建函式：Array'
category: DoJS
tags:
  - JavaScript
abbrlink: 154092581
date: 2023-11-22 00:00:00
---
學習 `Array` 內建函式，可以讓程式碼更簡潔。
<!--more-->
## 快速了解
內建函式可以讓程式碼更簡潔，但並非必要，使用一般程式碼也可以完成這些功能。
以下分享一些 `Array` 常用的內建函式。

`join.()` ：將陣列中所有元素連接成一個字串，預設分隔符是逗號。
```jsx
var arr = [1, 2, 3];
console.log(arr.join()); // 1,2,3
console.log(arr.join('-')); // 1-2-3
console.log(arr.join('')); // 123
```

`map()` ：把陣列中的每個元素帶入指定函式，然後建立一個新的陣列。
```jsx
var arr = [1, 2, 3];
function double(x) {
  return x * 2;
};
console.log(arr.map(double)); // [2, 4, 6]
```

`filter()` ：概念和 `map()` 類似，會根據指定的測試函數，從一個陣列中過濾出符合條件的元素，並建立新的陣列。
```jsx
var arr = [1, 3, 5, 7, 9];
arr.filter(x => x > 4); // [5, 7, 9]
```

`slice()` ：可截取出陣列某部份元素，會建立一個新的陣列，其意義為「自哪一個索引開始提取，到哪一個索引**之前**結束」。
```jsx
var arr = [0, 1, 2, 3, 4, 5];
console.log(arr.slice(1, 4)); // [1, 2, 3]
```

`splice()` ：可用來刪除與新增元素，會改變原本的陣列。
```jsx
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
console.log(months); // ["Jan", "Feb", "March", "April", "June"]
```

`sort()` ：依照字母順序排列陣列中的所有元素，會改變原本的陣列。
```jsx
const array = [1, 30, 4, 21, 100000];
array.sort();
console.log(array); // [1, 100000, 21, 30, 4]
```
### 小知識
- 在使用 `sort()` 時，因為數字被轉換成字串，在 Unicode 順序中 `"80"` 會在 `"9"` 的前面。
## 了解更多
- [MDN－Array](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array)：了解 `Array` 的常見函式。