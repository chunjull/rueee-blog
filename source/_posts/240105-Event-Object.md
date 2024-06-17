---
title: '#73 事件物件'
category: DoJS
tags:
  - JavaScript
abbrlink: 2862496385
date: 2024-01-05 00:00:00
---
瀏覽器會主動將「事件物件」的資料傳入事件處理器。
<!--more-->
## 快速了解
當監聽事件發生時，瀏覽器會去執行開發者透過 `addEventListener()` 註冊的 Event Handler（EventListener），即指定的韓式內容。
這時，EventListener 會主動建立一個「事件物件」（Event Object），裡面包含所有與該事件有關的屬性，且會以「參數」形式傳給 Event Handler。
舉例來說：
```html
<button id="btn">Click</button>
```
```jsx
var btn = docuemnt.getElementById("btn");
btn.addEventListener("click", function(e){
	console.log(e)
}, false);
```
上述程式碼的參數 `e` 即為事件物件。
點擊 `<button>` 後，可以從 `console` 看到 `event` 物件提供的屬性，例如：
- `type` ：事件名稱。
- `target` ：觸發事件的元素
- `bubbles` ：該事件是否在「冒泡」階段觸發。
- `pageX` / `pageY` ：該事件觸發時，滑鼠座標在網頁的相對位置。
### 小知識
- 事件物件是參數，因此可以自定義名義。
- 可以透過 Chrome 的 `console` 主控台觀察到事件物件所提供的屬性們。
## 了解更多
- [Kuro－隱藏在 "事件" 之中的秘密](https://ithelp.ithome.com.tw/articles/10192015)：本文最主要的參考範例。
- [MDN－Event](https://developer.mozilla.org/zh-TW/docs/Web/API/Event)：了解更多種事件物件的屬性。
- [彭彭－Javascript 事件處理 - Event Object 事件物件](https://www.youtube.com/watch?v=6MIZmmV00cg)：了解事件物件的操作方法。