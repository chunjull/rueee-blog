---
title: '#112 ES6：箭頭函式'
category: DoJS
tags:
  - JavaScript
abbrlink: 491475975
date: 2024-05-24 00:00:00
---
箭頭函式具有結構簡潔、沒有 `this` 值和 `arguments` 物件與「不能當成建構式使用」等特性。
<!--more-->
## 快速了解
ES6 新增了一種名叫「箭頭函式表達式」（Arrow Function expression）的函式表達式，通常簡稱為「箭頭函式」。
箭頭函式具有兩個重要特性：
- 更簡短的函式寫法。
- `this` 變數強制綁定。
### 箭頭函式的結構
首先，來回顧一下原始的函式結構：
```jsx
const arrowExample = function (doSomething){
	return something;
};
```
如果希望把一般函式修改成箭頭函式，可以依照以下步驟執行：
1. 把 `function` 關鍵字移除。
2. 在參數 `doSomething` 的右邊補上 `=>` 符號。
由上述步驟，可以得到以下結構的箭頭函式：
```jsx
const arrowExample = (doSomething) => {
	return something;
};
```
此外，當程式碼內容是表達式而沒有其他內容時，其只會直接回傳一個值，就還可以再進一步縮寫。
1. 把程式碼修改成「單行」。
2. 移除大括號。
3. 移除 `return` ，使函式直接回傳箭頭後面的結果。
```jsx
const arrowExample = (doSomething) => something;
```
當只有一個參數時，可以移除小括號；而當沒有參數或有兩個以上的參數時，小括號不可移除。
### 箭頭函式和一般函式的差異
箭頭函式和一般函式的主要差異有四點：
1. 箭頭函式寫法更簡潔。    
  相較於一般函式，箭頭函式只有一行程式碼，具有更簡短的結構。    
2.  `this` 值與一般函式不同。    
  箭頭函式的 `this` 值在一開始定義時就決定，永遠都會是最接近自己外層的一般函式中的值，且無法使用 `call` 、 `apply` 、 `bind` 來綁定 `this` 值。    
3. 沒有 `arguments` 物件。    
  傳統函式在執行時會自動帶上 `arguments` 參數，這是一種類陣列的物件，會將傳入的參數一一列出。使用箭頭函式時，若需要將未列出的參數取出，可以使用「其餘參數」達成。    
4. 不能作為建構式使用。
  不能搭配 `new` 關鍵字使用。
### 小知識
- 其餘參數（rest parameter） 與法為：在參數的變數名稱前方，加上 `...` 。
- 箭頭函式「沒有 `this` 值」的特性，很適合搭配 `setTimeout` 和 `EventTarget: addEventListener() method` 語法使用。
## 了解更多
- [MDN－箭頭函式](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/Arrow_functions)：了解箭頭函式的意義。
- [ExplainThis－什麼是箭頭函式 (Arrow Function)？跟一般的函式有什麼差別？](https://www.explainthis.io/zh-hant/swe/what-is-arrow-function)：了解箭頭函式與一般函式的差異。
- [MDN－其餘參數](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Functions/rest_parameters)：了解其餘參數的使用方式。