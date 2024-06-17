---
title: '#101 Scope Chain'
category: DoJS
tags:
  - JavaScript
abbrlink: 1390225425
date: 2024-05-13 00:00:00
---
Scope chain 指作用域由內向外尋找變數的的行為。
<!--more-->
## 快速了解
### 回顧作用域概念
作用域（Scope）指「一個變數的有效範圍」，一旦超出該範圍，就會無法取得該變數。
在 ES6 之前，JS 變數有效範圍的最小單位是以 `function` 作為分界。在 ES6 出現之後，作用域概念加入 `let` 與 `const` 宣告，可以用大括號 `{}` 來定義區塊作用域。
JS 的作用域可以分成三種：
- Global Scope：全域作用域。
- Function Scope：函式作用域。
- Block Scope：區塊作用域。
變數作用域的範圍取決於兩個元素：該變數的宣告方式、在哪裡進行宣告。而根據變數在哪裡宣告，又可以分為全域變數與區域變數。
### 範圍鍊
Scope chain，常被譯為「範圍鍊」或「作用域鍊」。
範圍鍊指：我們在使用變數時，會先嘗試在其有效範圍內——即「作用域」——尋找該變數。如果在有效範圍中找不到該變數，會往父層的作用域尋找，一直尋找到全域作用域為止。
以下述程式碼為例：在函式 `call()` 中最後 `console.log(name);` 的結果會是什麼呢？
```jsx
var name = "Pikachu";
evolve();
function evolve(){
	var name = "Raichu";
	call();
};
function call(){
	console.log(name); // ??
};
```
最終印出結果會是 `Pikachu` 。因為當函式 `call()` 在運作時，會擁有自己的函式作用域，而在這個有效範圍中，並沒有 `name` 變數。因此，JS 會繼續往外部的父層作用域尋找，函式 `call()` 的外部環境是全域，而非函式 `evolve()` ，所以，印出結果會是全域變數的 `Pikachu` 而不是函式 `evolve()` 中變數的 `Raichu` 。
## 了解更多
- [itsems－Javascript 的作用域與範圍鏈](https://medium.com/itsems-frontend/javascript-scope-and-scope-chain-ca17a1068c96)：了解作用與範圍鍊之間的關聯。