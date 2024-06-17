---
title: '#48 DOM：選取方式差異'
category: DoJS
tags:
  - JavaScript
abbrlink: 497814301
date: 2023-12-11 00:00:00
---
DOM 選取方式有「選取結果」與「回傳結果」兩種差異。
<!--more-->
## 快速了解
DOM 選取方式主要有兩種差異：選取結果與回傳結果。
### 選取結果差異
 `document.getElementById` 和 `document.querySelector` 必定只會取得單一元素或節點，所以沒有 `index` 與 `length` 屬性。
 `document.getElementsBy**` 和 `document.querySelectorAll` 則會選取多個節點或元素。
| 選取方式 | 選取結果 | 有無 index 與 length 屬性 |
| --- | --- | --- |
|  document.getElementById  | 單一元素或節點 | 無 |
|  document.querySelector  | 單一元素或節點 | 無 |
|  document.getElementsBy**  | 多個元素或節點 | 有 |
|  document.querySelectorAll  | 多個元素或節點 | 有 |
### 回傳結果差異
 `document.getElementsBy**` 回傳 HTMLColleaction； `document.querySelectorAll` 則回傳 NodeList。
HTMLCollection 只收集 HTML 元素節點，而 NodeList 除了 HTML 元素節點，也包含文字節點、屬性節點等。
這兩種都可以用「陣列索引」的方式來存取內容。
HTMLCollection 與 NodeList 在大部分情況是**即時更新**的——即「動態的」，但透過 `document.querySelector` 、 `document.querySelectorAll` 取得的 NodeList 則是靜態的。
而 NodeList 和 HTMLCollection 的差別在於，NodeList 包含任何的節點類型，HTMLCollection 則只包含 HTML 元素節點 (Element nodes)。
動態集合代表：隨後在 DOM 上面新增、修改、刪除節點的操作，都會直接反應在先前得到的元素集合結果中。
| 選取方式 | 回傳結果 | 集合型態 |
| --- | --- | --- |
|  document.getElementsBy**  | HTMLCollection | 動態集合 |
|  document.querySelector  | NodeList | 通常是靜態，特殊情況是動態 |
### 小知識
- 注意！ `document.getElementsBy**` 的「Element」後面有個 s。
## 了解更多
- [Kuro－透過 DOM API 查找節點](https://ithelp.ithome.com.tw/articles/10191765)：本文最主要的參考範例。
- [Fooish－DOM 查找元素 (DOM Traversing)](https://www.fooish.com/javascript/dom/traversing.html)：了解 DOM 選取方式的差異。