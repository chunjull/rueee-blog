---
title: '#67 網頁介面相關事件'
category: DoJS
tags:
  - JavaScript
abbrlink: 4272355166
date: 2023-12-30 00:00:00
---
網頁介面相關事件大多數與 BOM 較有關聯。
<!--more-->
## 快速了解
介面相關的事件不一定會與使用者對 DOM 的操作有關，反而大多數與 window 物件——即網頁介面相關事件——比較相關。
- `load` 事件：註冊在 `window` 物件上，指的是網頁資源（包括 CSS、JS、圖片等資源）全數載入完畢後才觸發。若是 `img` 元素的 `load` 事件，則表示「該圖片載入完畢後觸發」。
- `unload` 、 `beforeunload` 事件：與 `load` 事件相反， `unload` 與 `beforeunload` 事件分別會在離開頁面或重新整理時觸發，而 `beforeunload` 會跳出對話框，詢問使用者是否要離開目前頁面。
- `error` 事件：會在 `document` 或圖片載入錯誤時觸發。
- `resize` 事件：當瀏覽器或指定元素的「尺寸變更」時觸發。
- `fullscreenchange` 事件：當使用者切換瀏覽器為全螢幕或是還原原視窗時觸發。
- `scroll` 事件：當瀏覽器或指定元素的「捲軸被拉動」時觸發。
- `DOMContentLoaded` 事件：類似 `load` 事件，但 `load` 事件是在網頁「所有」資源都已載入完畢後才觸發，而 `DOMContentLoaded` 事件則是在 DOM 被完整讀取與解析後就會被觸發，不需等待外部資源讀取完成。
### error 事件補充
由於維護性考量，強烈建議用「非侵入式 JS」註冊大多數事件，只有 `error` 事件適合以 `on-event` handler 的寫法處理。
```jsx
<img src="image.jpg" onerror="this.src='default.jpg'">
```
上述程式碼表示：當 `image.jpg` 圖檔不存在時，馬上就會觸發 `error` 事件，透過 `this.src` 將 `<img>` 的 src 屬性替換成指定的預設圖檔。
若是在網頁載入完成後才註冊 `error` 事件的處理器，只會看到破圖的結果，因為 `error` 事件不會再次被觸發。
### DOMContentLoaded 事件補充
如果 `<script>` 標籤放在 `<head>...</head>` 之間，會因為還沒解析到網頁本體，而導致選取不到 DOM 的問題。
但如果把 `<head>` 的程式碼改成 `DOMContentLoaded` 事件，讓 `document` 結構已解析完畢再執行內容，就可以排除 `<script>` 標籤放在 `<head>...</head>` 之間抓不到 DOM 的問題。
```html
<head>
	<script>
		document.addEventListener("DOMContentLoaded", function(){
			document.getElementById("hello").textContent = "Hello";
		}, false);
	</script>
</head>
```
### 小知識
- 為了防止使用者遺失編輯中的資料或遭到詐騙， `beforeunload` 對話框的文字在 Chrome 51 後就不再提供自訂訊息的功能。
- jQuery 中的 `$(document).ready(handler)` 語法，其作用和 `DOMContentLoaded` 事件類似。
## 了解更多
- [Kuro－那些你知道與不知道的事件們](https://ithelp.ithome.com.tw/articles/10192175)：本文最主要的參考範例。