---
title: '#102 閉包'
category: DoJS
tags:
  - JavaScript
abbrlink: 2403192730
date: 2024-05-14 00:00:00
---
閉包可以使變數不被外在環境干擾。
<!--more-->
## 快速了解
再次回顧「作用域」概念：
- 變數在函式內：在函式執行完後，若變數沒有被任何內容參照到，該變數的記憶體空間就會被釋放掉。
- 變數在函式外：在全域環境的變數，其記憶體空間不會被釋放掉。
### 閉包觀念
閉包（closure）指：當內部的子函式被回傳後，內部函式能夠取得函式外部父函式的變數，並且記住這個變數，使該變數的記憶體不會被釋放。
建立「閉包」的優點為：讓變數保留在該函式中而不會被外在環境干擾。
閉包的達成條件有兩個：
1. 變數會被內部函式所參照。
2. 變數記憶體不會被釋放。
### 閉包範例
假設現在要實作一個「計算伊布數量」的函式：
```jsx
var count = 0;
function countEevees(){
	count++;
	console.log(count + " Eevee(s)");
};
countEevees(); // 1 Eevee(s)
countEevees(); // 2 Eevee(s)
countEevees(); // 3 Eevee(s)
```
以上程式碼為「不使用閉包」的範例，如果在只計算伊布的情況下，是否使用閉包並不影響程式碼運作。但若是我們還要計算更多寶可夢時，「不使用閉包」的程式碼可能會導致計算錯誤。因此，可以將程式碼更改成「閉包」的形式，例如：
```jsx
function eeveeFamily(){
	var count = 0;
	function countEevees(){
		count++;
		console.log(count + " Eevee(s)");
	}
	return countEevees;
};
function pikachuFamily(){
	var count = 0;
	function countPikachus(){
		count++;
		console.log(count + " Pikachu(s)");
	}
	return countPikachus;
};
const countEevees = eeveeFamily();
const countPikachus = pikachuFamily();
countEevees(); // 1 Eevee(s)
countEevees(); // 2 Eevee(s)
countEevees(); // 3 Eevee(s)
countPikachus(); // 1 Pikachu(s)
countPikachus(); // 2 Pikachu(s)
countPikachus(); // 3 Pikachu(s)
```
閉包形式會將計算伊布數量的變數 `count` 被包裹在函式 `eeveeFamily` 中。
父函式 `eeveeFamily` 內部的函式 `countEevees()` 才是真正要執行計算的部分， `count` 的值只有在父函式 `eeveeFamily` 裡面才能被使用，在父函式外無法取用到其值。
函式內要用到的變數 `count` 在執行真正記數的函式 `countEevees()` 後，會再將該函式的值回傳，使變數 `count` 不受其他函式影響，如此即可成功分開計算伊布和皮卡丘的數量。
## 了解更多
- [Kuro－閉包 Closure](https://ithelp.ithome.com.tw/articles/10193009)：本文最主要的參考範例。
- [MDN－閉包](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Closures)：了解閉包（closure）的意義。
- [Huli－所有的函式都是閉包：談 JS 中的作用域與 Closure](https://blog.huli.tw/2018/12/08/javascript-closure/)：深入了解作用域與閉包的關聯。
- [ExplainThis－什麼是閉包(closure)？](https://www.explainthis.io/zh-hant/swe/what-is-closure)：從多個範例了解「閉包」。
- [PJCHENder－深入淺出瞭解 JavaScript 閉包（closure）](https://pjchender.blogspot.com/2017/05/javascript-closure.html)：看看更多的範例