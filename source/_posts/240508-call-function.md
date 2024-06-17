---
title: '#96 回呼函式'
category: DoJS
tags:
  - JavaScript
abbrlink: 969311364
date: 2024-05-08 00:00:00
---
回呼函式指「在某一函式執行時或執行後，依條件或依序去執行所傳遞進來的函式」。
<!--more-->
## 快速了解
CallBack 被翻譯為「回調、回函、回呼」等意思。
CallBack function 則是指「能藉由參數通往另一函式的函式」，簡單來說，就是「把函式當作另一個函式的參數，透過另一個函式來呼叫它」。
當某函式在滿足特定條件才會「被動地」去執行時，可以稱其為「回呼函式」。
以下分享回呼函式的兩種常見情境：
1. 事件。
2. 控制多個函式之間執行的順序。
### 事件驅動案例
以「辦公室電話響了」、「去接電話」這個事件為例：
```jsx
office.addEventListener('電話響', function(){ /* 接電話 */}, false);
```
 `office` 透過 `addEventListener` 方法註冊了一個「電話響」的事件，當該事件被觸發時，它會去執行指定的第二個參數——「接電話」這個「函式」。
### 定時器案例
以定時器函式 `window.setTimeout` 為例，假設我們需要設定「間隔某段時間後再執行某件事」，並控制多函式間的執行順序：
```jsx
const funcA = function(callback){
  const i = Math.random() + 1;
  window.setTimeout(function(){
    console.log('function A');
    if( typeof callback === 'function' ){
      callback();
    };
  }, i * 1000);
};
const funcB = function(){
  const i = Math.random() + 1;
  window.setTimeout(function(){
    console.log('function B');
  }, i * 1000);
};
funcA( funcB );
```
為了確保執行順序是先 `funcA` 後 `funcB` ，要先在 `funcA` 加上參數 `callback` ，並加上判斷式「若參數 `callback` 是函式就呼叫它」。如此一來，無論 `funcA` 在執行時要等多久， `funcB` 都會等到 `console.log('function A');` 完成後才執行。
### CallBack Hell
如果函式之間的相依過深，可能會造成多層巢狀的「回呼地獄」（CallBack Hell）。
```jsx
step1(function(value1){
	step2(function(value2){
		step3(function(value3){
			step4(function(value4){
				step5(function(value5){
					console.log(value5);
				});
			});
		});
	});
});
```
像上面這樣，不斷向下回呼的函式結構，就被稱為「回呼地獄」。
## 了解更多
- [Kuro－Callback Function 與 IIFE](https://ithelp.ithome.com.tw/articles/10192739)：本文最主要的參考範例。
- [MDN－回呼函式](https://developer.mozilla.org/zh-TW/docs/Glossary/Callback_function)：了解回呼函式的概念。
- [MDN－setTimeout](https://developer.mozilla.org/zh-CN/docs/Web/API/setTimeout)：了解 `setTimeout` 的延伸用法。
- [Ray－RE：從零開始的學習 JS 生活-第二十五日](https://ithelp.ithome.com.tw/articles/10226668?sc=rss.iron)：欣賞回呼地獄造成的「波動拳」動畫。