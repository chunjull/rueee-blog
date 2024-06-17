---
title: '#75 阻擋事件傳遞'
category: DoJS
tags:
  - JavaScript
abbrlink: 4041490375
date: 2024-01-07 00:00:00
---
`e.stopPropagation()` 可以阻擋事件傳遞，不論向上或向下。
<!--more-->
## 快速了解
前面提過， `event.preventDefault()` 可以阻擋預設事件，但不會阻止事件向上傳遞。
如果想要阻擋事件傳遞，可以利用另一個方法： `e.stopPropagation()` 。
當使用 `event.stopPropagation()`，事件傳遞就會停在設置的地方：
- 若在捕獲階段：阻止事件往下傳遞。
- 若在冒泡階段：阻止事件向上傳遞。
### 阻擋事件冒泡傳遞範例
 `e.stopPropagation()` 最常見的使用情境是：解決 `checkbox` 的冒泡問題。
```html
<label class="lbl">
	Label <input type="checkbox" name="chkbox">
</label>
```
為了增強 `checkbox` 的易用性，通常會另外加上 `label` 標籤在為對應的 `checkbox` 加上 `for` 屬性。
```jsx
var lbl = document.querySelector(".lbl");
lbl.addEventListener("click", function(e){
	console.log("lbl click");
}, false);

// "lbl click"
// "lbl click"
```
上述程式碼回傳結果是「把 `console.log("lbl click");` 執行兩次」，因為在 `label` 標籤包覆 `checkbox` 的情況下，是透過點擊 `label` 觸發 `click` 事件，所以瀏覽器會自動把這個 `click` 事件傳給 `checkbox` 。
而 `checkbox` 受事件冒泡影響，會再度把 `click` 事件傳遞至 `label` 上，導致 `"lbl click"` 出現兩次。
已知 `checkbox` 受事件冒泡影響而將事件向上傳遞，如果想要修正 `label` 的 `click` 事件觸發兩次的錯誤，可以在 `checkbox` 的 `click` 事件加上 `e.stopPropagation()` 。
```jsx
// label
var lbl = document.querySelector(".lbl");
// chkbox
var chkbox = document.querySelector("#chkbox");
lbl.addEventListener("click", function(e){
	console.log("lbl click");
}, false);
chkbox.addEventListener("click", function(e){
	e.stopPropagation();
}, false);
```
### 小知識
- 除了 `e.stopPropagation()` ，還有一種阻擋事件傳遞的方法： `e.stopImmediatePropagation()` ，其可以阻擋同層的其他事件運作。
- 在最上層 `window` 的捕獲階段設定 `e.stopPropagation()` ，會阻止後續事件傳遞，造成所有好相關事件都失效。
## 了解更多
- [Kuro－隱藏在 "事件" 之中的秘密](https://ithelp.ithome.com.tw/articles/10192015)：本文最主要的參考範例。
- [MDN－stopPropagation](https://developer.mozilla.org/zh-TW/docs/Web/API/Event/stopPropagation)：了解 `e.stopPropagation` 的使用方式。
- [MDN－stopImmediatePropagation](https://developer.mozilla.org/zh-TW/docs/Web/API/Event/stopImmediatePropagation)：了解 `e.stopImmediatePropagation` 的使用方式。