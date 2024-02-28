### window

### DOM(document object model)
- Describes the document structure, manipulations, and events
- `document`
- `documnet node navigation`: childNodes include text node.
![document-node.png](/images/dom-node-navigation.PNG)
---
- `document-element-only navigation`: just get the tag element
![document-element-only.png](/images/document-element-only.PNG)

### DOM top nodes
- `<html> = document.documentElement`
- `<body> = document.body`
- `<head> = document.head`

### Search document element
- `document.getElementById(id)`
- `document.getElementsByName(name)`
- `elem.querySelectorAll(css)`: returns all elements inside elem matching the given CSS selector.

### DOM classes
- EventTarget
- Node
- Element
- HTMLElement
- HTMLDivElement/HTMLInputElement...

### BOM(browser object model)
- objects provided by the browser (host environment)
- `navigator`
- `screen`
- `location`
- `frames`
- `history`
- `XMLHttpRequest`
- `alert/confirm/prompt`
- `setTimeout/setInterval`