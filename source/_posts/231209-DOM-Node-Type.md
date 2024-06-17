---
title: '#46 DOM：節點類型'
category: DoJS
tags:
  - JavaScript
abbrlink: 4150368758
date: 2023-12-09 00:00:00
---
DOM 有多種節點類型與常數。
<!--more-->
## 快速了解
 `document` 物件是整個 DOM tree 的根節點，因此，要存取 HTML 時，都是從 `document` 物件開始。
DOM 節點類型除了「元素節點」（element nodes）外，還有「文字節點」（text nodes）、「註解節點」（comment nodes）。
### 節點類型整理
常見的 DOM 節點類型常數 （Node type constants）有以下幾種：
| 節點類型常數 | 對應數值 | 說明 |
| --- | --- | --- |
| node.ELEMENT_NODE | 1 | HTML 元素的 Elements 節點 |
| node.TEXT_NODE | 3 | 實際文字節點，包含換行與空格 |
| node.COMMENT_NODE | 8 | 註解節點 |
| node.DOCUMENT_NODE | 9 | 根節點（Document） |
| node.DOCUMENT_TYPE_NODE | 10 | 文件類型的 Document 節點，例如： <! DOCTYPE html> 。 |
| node.DOCUMENT_FRAGMENT_NODE | 11 | DocumentFragment 節點 |

可以透過 `nodeType` 屬性判斷「常數」或「對應數值」來判斷節點類型。
```jsx
document.nodeType === Node.DOCUMENT_NODE; // true
document.nodeType === 9;
```
## 了解更多
- [Kuro－透過 DOM API 查找節點](https://ithelp.ithome.com.tw/articles/10191765)：本文最主要的參考範例。
- [Fooish－DOM 節點物件的屬性](https://www.fooish.com/javascript/dom/node-properties.html)：了解更多種 DOM 節點物件的屬性。