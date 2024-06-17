---
title: '#89 JS 運作方式'
category: DoJS
tags:
  - JavaScript
abbrlink: 712895601
date: 2024-05-01 00:00:00
---
JS 要透過直譯器編譯後，才生成執行環境看得懂的程式碼。
<!--more-->
## 快速了解
我們之前提過：JS 是一種直譯式語言。
這代表「JS 無法直接被瀏覽器或電腦給閱讀，要經過編譯（Compile）才能運行這段程式碼」。
### JS 如何運作
直譯式語言會透過「直譯器」生成電腦看得懂的代碼，並將錯誤直接反映在執行環境中，以 JS 為例，錯誤會直接反映在瀏覽器的主控台（console）上。
JS 直譯器轉換時，會先將語法基本單元化（Tokenizing），再解析成抽象結構樹（AST），最後生成代碼：
1. 語法基本單元化（Tokenizing）會將原始碼拆解成一個一個小單元。在此階段，直譯器僅僅只是解析字詞而已，還無法判斷每個小單元的作用。
2. 抽象結構樹（AST，Abstract Syntax Tree）會把前一階段解析的 token 轉換成其被賦予的意義。
3. 直到最後生成代碼，程式碼才會運行。
### 小知識
- 瀏覽器、Node.js 等環境的代碼生成過程不盡相同。
## 了解更多
- [Esprima](https://esprima.org/demo/parse.html#)：可以觀察直譯器轉換過程的小工具。
- [CHEN－語法作用域 lexical scope](https://its-okay.medium.com/%E8%AA%9E%E6%B3%95%E4%BD%9C%E7%94%A8%E5%9F%9F-lexical-scope-e121679a105b)：了解語法作用域的意義。
- [#1 JS 是什麼？](https://chunjull.github.io/javascript/20231025/1925797630/)：回顧 JS 是一種什麼樣的程式語言。