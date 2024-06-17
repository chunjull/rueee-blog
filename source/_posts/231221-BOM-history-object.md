---
title: '#58 BOM：history'
category: DoJS
tags:
  - JavaScript
abbrlink: 520630088
date: 2023-12-21 00:00:00
---
`history` 搭配 SPA 的應用，可以提升使用者體驗並保障安全性。
<!--more-->
## 快速了解
 `window.history` 會記錄使用者在目前瀏覽器視窗上顯示過的頁面，且會把曾經瀏覽過的頁面 URL 放在 `history` 物件當中。
此外，由於隱私考量，BOM 不允許 JS 讀取清單上的詳細網址，所以我們只能取得 `history` 的 `length` 屬性，進而得知當下這個瀏覽器曾經切換過幾次頁面。
### 相關語法
除了 `length` 屬性外， `history` 物件還提供 `back()` 、 `forward()` 及 `go()` 這三種方法，讓 JS 可以控制網頁的歷史紀錄。
```jsx
history.back();
// 等同於瀏覽器的「上一頁」
history.forward();
// 等同於瀏覽器的「下一頁」
history.go(-1);
// 等同於瀏覽器的「上一頁」，也就是 history.back()
history.go(1);
// 等同於瀏覽器的「上一頁」，也就是 history.forward()
```
### SPA 與錨點
當今流行的前端趨勢——SPA（Single Page application，單頁式應用），是一種「在單一頁面上動態更新目前頁面內容」的程式模型。
過去，會透過操作 `hash` 的方式，讓使用者在切換上、下頁的同時瀏覽器不換頁更新。當使用者點擊錨點時，瀏覽器會在 `history` 增加一筆新紀錄，且不離開目前頁面。
此做法的缺點是：網站永遠只有單一網址，且 `hash` 紀錄可能會大到難以維護。
### SPA 與 pushState
在 HTML5 的規範中， `history` 物件新增了 `pushState()` 用法，可以將狀態與網址同時存入到 `history` 物件紀錄中，並在使用者切換上、下頁時，將已儲存的狀態還原至頁面中，如此達到在單一頁面中無縫切換的良好體驗。
 `pushState()` 語法為： `pushState(state, unused, url);` ，第一個參數為儲存的物件；第二個參數代表新頁面的標題；第三個參數則是新頁面的網址。
```jsx
let state = {
	pageName: "profile"
};
window.history.pushState(state, "My Profile", "/profile");
```
呼叫 `history.pushState()` 方法後，瀏覽器會在 `history` 物件新增一筆紀錄，且儲存當下的 `state` 。
為了安全性考量，防止有心人利用網址替換來進行詐騙， `pushState()` 第三個參數的網址內容，只能限定在相同網域下或是使用相對網址。
### 小知識
- 由於無法取得 URL 的完整歷史清單，所以在實務上 `history.go()` 不如 `back()` 或 `forward()` 實用，因為開發者無法掌握使用者最終會被 `history` 導致哪一頁。
## 了解更多
- [MDN－history](https://developer.mozilla.org/zh-CN/docs/Web/API/History)：了解 `history` 的概念。
- [MDN－pushState](https://developer.mozilla.org/zh-CN/docs/Web/API/History/pushState)：了解 `pushState()` 的使用方式。
- [MDN－SPA](https://developer.mozilla.org/zh-TW/docs/Glossary/SPA)：了解單頁式應用的意義。
- [Schaos－為什麼網站要做成 SPA？SSR 的優點是什麼？](https://medium.com/schaoss-blog/%E5%89%8D%E7%AB%AF%E4%B8%89%E5%8D%81-18-fe-%E7%82%BA%E4%BB%80%E9%BA%BC%E7%B6%B2%E7%AB%99%E8%A6%81%E5%81%9A%E6%88%90-spa-ssr-%E7%9A%84%E5%84%AA%E9%BB%9E%E6%98%AF%E4%BB%80%E9%BA%BC-c926145078a4)：學習 SPA 的功能與發展。