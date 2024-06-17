---
title: '#100 函式參數'
category: DoJS
tags:
  - JavaScript
abbrlink: 2883286607
date: 2024-05-12 00:00:00
---
函式參數可傳入 arguments 物件、其餘參數等值。
<!--more-->
## 快速了解
呼叫函式時，最常見的函式結構是透過「函式名稱」加上「小括號」的方式，小括號內的資料，就是「參數」。
```jsx
const plus = function(numA, numB){
	return numA + numB;
};
plus(1, 2); // 3
```
以上述程式碼為例：呼叫 `plus(1, 2);` 時，其中的 `1, 2` 會作為「參數」傳至 `plus` 函式中， `numA` 與 `numB` 的值就會分別是 `1` 與 `2` 。回傳內容 `return numA + numB;` 就會是 `1 + 2` 的結果。
### arguments 物件
當函式被呼叫時，會產生一個 `arguments` 物件，其內容為：呼叫函式所帶入的「參數」。
雖然 `arguments` 看起來像「陣列」，但實際上它只是一個看起來帶有「索引」特性且內建 `length` 屬性的物件，其他地方與「陣列」完全不同。
即使在定義函式時，完全沒有指定參數，仍然可以在函式內透過 `arguments` 物件才取得參數。換言之，利用 `arguments` 物件可以讓函式變得更有彈性。例如：
```jsx
const plus = function(numA, numB){
	let num = 0;
	for(var i = 0; i < arguments.length; i++){
		num += arguments[i];
	}
	return num;
};
plus(1, 2, 3, 4); // 10
```
原本只能讓 `plus` 函式做「兩個數值相加」，但現在，藉由 `arguments` 物件可以讓 `plus(1, 2, 3, 4)` 的所有參數一起相加。
### 其餘參數
ES6 新增了一種特性「其餘參數」（rest parameter），可以藉此來取得不確定數量的參數。
因為 ES6 的箭頭函式無法使用 `arguments` 物件，能透過箭頭函式搭配其餘參數的方法，完成和 `arguments` 物件相同的功能。
```jsx
const plus = (...arguments) => {
	let num = 0;
	for(var i = 0; i < arguments.length; i++){
		num += arguments[i];
	}
	return num;
};
plus(1, 2, 3, 4); // 10
```
當函式的最後一個參數以 `...` 作為開頭命名時，它會被視為一個陣列，並且將所有的參數存入這個陣列中。
而因為 `...arguments` 實際上是一個「陣列」，所以它能夠使用 `arguments` 物件所沒有的 `reduce` 方法，讓該 `plus` 函式變得更加簡短，例如可以將上述程式碼簡化成底下這樣：
```jsx
const plus = (...arguments) => arguments.reduce((a, b) => a + b);
plus(1, 2); // 3
```
### 以「物件」作為參數
除了上述參數外，還有一種常見方式：將多個參數用一個「物件」包裝起來。
由於物件屬性不要求「順序」，即便中間忽略幾個非必填的屬性也不影響程式運作。同時，往後就算要新增參數也不擔心會影響到過去的程式。
這種作法讓呼叫函式更簡便，且使程式碼更容易閱讀，也易於維護。
```jsx
var people = {
	name: "Kumamon",
	birthDay: "03/12",
	gender: "male",
	address: "Kumamoto-ken",
	phone: "",
	email: ""
};
addPerson(people);
```
以上述程式碼為例：假設要完成「將某人加入通訊錄」的功能，以函式 `addPerson()` 實作。首先將某人的資料屬性填入物件 `people` 中，非必填屬性可以留白不填，最後再把 `people` 物件作為參數傳入 `addPerson()` 。
### 參數的預設檢查
在 JS 中，即使函式的參數數量已經定義過，實際在呼叫時，仍可以不傳入參數或者傳入不對等的數量。如果傳多了也無所謂；若傳少了，那些接收不到值的參數們就會變成 `undefined` 。
有幾種方法可以幫助我們檢查參數：
1.  `||` 運算子

    ```jsx
    const plus = function(numA, numB){
    	numA = numA || 0;
    	numB = numB || 0;
    	return numA + numB;
    };
    ```    
2.  `!==` 搭配三元運算子

    ```jsx
    const plus = function(numA, numB){
    	numA = (typeof numA !== "undefined") ? numA : 0;
    	numB = ;
    	return numA + numB;
    };
    ```    
3. ES6 預設參數

    ```jsx
    const plus = function(numA = 0, numB = 0){
    	return numA + numB;
    };
    ```
## 了解更多
- [MDN－arguments](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments)：了解 `arguments` 物件的意義。
- [MDN－rest parameter](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/rest_parameters)：了解其餘參數（rest parameter）的意義。
- [MDN－預設參數](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Default_parameters)：了解 ES6 預設參數的意義。