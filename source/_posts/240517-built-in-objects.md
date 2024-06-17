---
title: '#105 內建物件'
category: DoJS
tags:
  - JavaScript
abbrlink: 1429919898
date: 2024-05-17 00:00:00
---
JS 的內建物件是透過物件「原型」提供的方法繼承而來。
<!--more-->
## 快速了解
依照功能不同，JS 的內建物件可分成三種類型：
- 封裝類物件：包含 `Array()` 、 `Object()` 、 `Function()` 、 `String()` 、 `Number` 、 `Boolean()` 等，用來代表 JS 各種資料型態的原型物件。
- 工具類物件： `Math` 、 `Date` 、 `RegExp` 等具有特殊用途的物件。
- 錯誤／例外處理類物件： `Error` 、 `ReferenceError` 、 `SyntaxError` 、 `TypeError` 等，代表程式執行過程中發生錯誤（error）或出現例外情況（exception）的錯誤物件。
### 資料封裝類物件
在 JS 中，所有物件（包括陣列、函式）都繼承自 `Object` ，可以透過物件原型提供的 `constructor` 屬性查找到各資料型態真正的原型建構子。
因為這樣的特性，使開發者可以透過 `new` 運算子加上原型建構子來產生該型別的物件。此外，若沒有使用 `new` 運算子，則可以透過基本型別包裹器來轉換資料型別。
### 工具類物件
工具類物件以 `Math` 、 `Date` 、 `RegExp` 為代表。

1. Math()

    所有 `Math` 的屬性和方法都是靜態「唯讀」，並非建構式，因此無法由 `new` 運算子來產生新物件，且會使用大寫表示 `Math` 物件的屬性，例如： `Math.PI` 、 `Math.SQRT2` 。    
2. Date()

     `Date()` 是建立 `Date` 物件的建構子函式，用來表示日期與時間，且只能透過 `new` 運算子來產生。若省去 `new` 運算子，直接把 `Date` 作為一般函式呼叫，將會得到一個代表當下時間的字串，而非 `Date` 物件。    
3. RegExp()

     `RegExp()` 物件，是用來表示正規表達式（Regular Expression, RegExp, RE）的一種物件，可以透過正規表達式字面值（regular expression literal）或 `new` 運算子來建立。
### 錯誤／例外處理類物件
常被用來代表「過程中發生錯誤（error）」或「出現例外狀況（exception）」的錯誤物件有 `Error` 、 `ReferenceError` 、 `SyntaxError` 與 `TypeError` 等。例如：當我們嘗試在 console 主控台呼叫一個不存在的函式時，主控台會顯示 `ReferenceError` 的錯誤。
在 JS 中，可以透過 `try…catch` 語法來捕獲錯誤，例如，當我們想要呼叫不存在的 `hello()` 函式時：
```jsx
try {
	hello();
}
catch(e) {
	console.log(e.name + ': ' + e.message);
}
finally {
	...
}
```
以上述程式碼為例，實際執行時因為 `hello()` 函式並不存在，程式會跑進 `catch` 區塊中，並傳遞該錯誤或例外的物件 `e` ，以取得其的 `name` 與 `message` 等屬性，讓開發者可以明確知道錯誤的類別與相關訊息。此外，還可在捕獲錯誤的最後加上 `finally` 語法，其代表不論 `try` 區塊有無發生錯誤，都會執行 `finally` 區塊的程式碼。
### 小知識
- `Math` 物件提供的數學方法之精度會取決於實作方法。換句話說，不同瀏覽器可能會得到不同結果，甚至同樣的 JS 引擎在不同作業系統或架構上，所得到的結果都可能有差異。
## 了解更多
- [MDN－標準內建物件](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects)：了解 JS 的標準內建物件。
- [MDN－Math](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Math)：了解 `Math` 物件的意義。
- [MDN－Date](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Date)：了解 `Date` 物件的意義。
- [MDN－RegExp](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)：了解 `RegExp()` 物件的意義。
- [MDN－try…catch 語法](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Statements/try...catch)：了解 `try…catch` 的意義。