---
title: '#70 表單相關事件 '
category: DoJS
tags:
  - JavaScript
abbrlink: 90660923
date: 2024-01-02 00:00:00
---
表單事件通常與表單狀態改變有關。
<!--more-->
## 快速了解
多數表單相關事件被用來處理表單元素，例如： `<input>` 、 `<select>` 、 `<textarea>` 等。
- `input` 事件：當 `input` 、 `textarea` 及帶有 `contenteditable` 的元素內容被改變時，就會觸發事件。
- `select` 事件：當使用者在 `input` 、 `textarea` 元素選取文字時觸發。
- `change` 事件：當 `input` 、 `select` 、 `textarea` 、 `radio` 、 `checkbox` 等表單元素被改變時觸發。但與 `input` 事件不同的是， `input` 事件會在輸入框輸入內容的當下觸發，而 `change` 事件則是在目前焦點離開輸入框後才觸發。
- `submit` 事件：當 `<form>` 被送出時觸發，通常表單驗證都會在這一步處理，若驗證未通過則 `return false;` 。
- `reset` 事件：當 `<form>` 被重置時觸發。
- `focus` 事件：當表單元素被聚焦時觸發。
- `blur` 事件：當表單元素失去焦點時觸發。
### select 事件補充
 `input` 、 `textarea` 元素中被選取的文字可以在 `event.target` 裡的 `selectionEnd` 、 `selectionStart` 及 `value` 的屬性中取得。
```jsx
element.addEventListener("select", function(e){
	// 被選取文字範圍的起點
	console.log(e.target.selectionStart);
	// 被選取文字範圍的終點
	console.log(e.target.selectionEnd);
	// 透過 e.target.value.substr() 取出被選取的文字區段
	console.log(e.target.value.substr(e.target.selectionStart, e.target.selectionEnd));
}, false);
```
## 了解更多
- [Kuro－那些你知道與不知道的事件們](https://ithelp.ithome.com.tw/articles/10192175)：本文最主要的參考範例。