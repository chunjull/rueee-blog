---
title: '#91 作用域與範圍鍊'
category: DoJS
tags:
  - JavaScript
abbrlink: 3963825218
date: 2024-05-03 00:00:00
---
作用域是變數的有效範圍，瀏覽器會隨著範圍鍊尋找可取用的變數。
<!--more-->
## 快速了解
之前介紹過：變數的有效範圍被稱為「作用域」，實際上，作用域還可以細分成靜態與動態兩種。
### 語法作用域
JS 中的「Scope」可稱為作用域、範疇、有效範圍、存在範圍，意思是：變數可被取用（accessibility）或可被看到（visibility）的有效範圍。
作用域分為「靜態作用域」與「動態作用域」，其會影響變數的賦值方式，並牽涉到直譯式語言的編譯及運行流程。
兩種作用域的區分為：
- 靜態作用域：變數的作用域在**語法解析**時，就已經確定作用域，且**不會改變**。
- 動態作用域：變數的作用域在**函式調用**時才決定。
JS 採用又被稱為「語法作用域」（lexical scope）的靜態作用域，原始碼寫好時，作用域就已經被確定，且不會再改變。
### 範圍鍊
範圍鍊（Scope Chain）指「當函式內沒有需要的變數時，向外尋找該變數」的過程。
範圍鍊是依據函式文法本身來決定，與執行環境無關。
當作用域內需要某個變數但在該範圍內找不到時，瀏覽器會向外一層層查找，在全域環境頁找不到時，會回傳 `Uncaught ReferenceError: xxx is not defined` 的錯誤訊息。
```jsx
var value = 1;
function fn1(){
	console.log(value);
}
function fn2(){
	var value = 2;
	fn1();
}
fn2();
```
在上述程式碼中，無論是 `fn1` 或 `fn2` ，其範圍鍊都指向全域。
 `fn1` 的回傳結果會是 `1` ，因為對 `fn1` 函式來說，它沒有 `value` 這個變數，只能往外部環境尋找，而 `fn1` 的外部環境是全域執行環境，不是 `fn2` ，所以最終取得的值是全域的 `value = 1` 。
## 了解更多
- [itsems－Javascript 的作用域 (Scope) 與範圍鏈 (Scope Chain)](search.google.com/search-console/welcome?utm_source=about-page)：深入了解作用域與範圍鍊的概念。
- [#31 變數的有效範圍](https://chunjull.github.io/javascript/20231124/3746595863/)：回顧作用域的概念。