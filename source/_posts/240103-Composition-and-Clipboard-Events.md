---
title: '#71 特殊事件'
category: DoJS
tags:
  - JavaScript
abbrlink: 4271922278
date: 2024-01-03 00:00:00
---
組成事件與剪貼簿事件都是常見的特殊事件。
<!--more-->
## 快速了解
### 組成事件
組成事件（Composition Event）指 `conpositionstart` 、 `compositionend` 及 `compositionupdate` 這三個事件。
透過 `Composition Events` ，可以觀察使用者在輸入框內開啟輸入法（Input Method Editor, IME）時，組字或選字的狀態。
 `Composition Events` 的三個監聽事件之意義：
- `compositionstart` 事件：輸入框內開啟輸入法，且**正在拼字時**觸發。
- `compositionupdate` 事件：輸入框內開啟輸入法，且**正在拼字**或**選字時**更改了內容時觸發。
- `compositionend` 事件：輸入框內開啟輸入法，拼字或選字**完成**，正要送出至輸入框時觸發。
組成事件可以解決一連串和「輸入框」有關的問題，例如：
1. 當要動態監聽輸入框的文字變化時，通常會以 `keydown` 、 `keypress` 、 `keyup` 等鍵盤事件來判斷是否變動，但若是「複製貼上」之類的操作，就無法透過鍵盤事件判斷。
2. 即使是 `change` 事件，也是在使用者改變內容，且焦點離開輸入框的前一刻才被觸發。
3. 雖然使用 `input` 事件，其「會在輸入框的內容被改變時即時觸發」的特性，可以解決在 `onChange` 及鍵盤相關事件功能不足的情況。然而，這會導致新的問題——透過類似 `autocomplete` （自動完成）的方式給使用者建議時，使用「注音符號」或「拼音文字」給搜尋建議沒有太大意義。
這些問題都可以透過 `Composition Events` 增強輸入框的行為，而得到修正。
### 剪貼簿事件
與剪貼簿操作相關的事件有以下三個：
- `cut` 事件：當使用者在網頁上選取某段文字，並進行「剪下」動作時觸發。
- `copy` 事件：當使用者在網頁上選取某段文字，並進行「複製」動作時觸發。
- `paste` 事件：當使用者將剪貼簿的文字貼上時觸發。
## 了解更多
- [Kuro－那些你知道與不知道的事件們](https://ithelp.ithome.com.tw/articles/10192175)：本文最主要的參考範例。
- [Kuro－透過 Composition Events 增強非拉丁語系輸入法對輸入框的支援](https://kuro.tw/posts/2016/10/11/%E7%AD%86%E8%A8%98-%E9%80%8F%E9%81%8E-Composition-Events-%E5%A2%9E%E5%BC%B7%E9%9D%9E%E6%8B%89%E4%B8%81%E8%AA%9E%E7%B3%BB%E8%BC%B8%E5%85%A5%E6%B3%95%E5%B0%8D%E8%BC%B8%E5%85%A5%E6%A1%86%E7%9A%84%E6%94%AF%E6%8F%B4/)：了解 Composition Events 的使用方式。