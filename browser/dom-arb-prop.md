### DOM properties
- `DOM node(just a regular js object)` properties, some mapping from html attributes
- `case-sensitive`
- can have any value

### HTML attributes
- attach on HTML tag, like: id on div `<div id="d"></div>`
- if an attribute is non-standard, there won’t be a DOM-property for it.
```js
// helpful methods to handle non-standard attr
elem.attributes
elem.hasAttribute(name) – checks for existence.
elem.getAttribute(name) – gets the value.
elem.setAttribute(name, value) – sets the value.
elem.removeAttribute(name) – removes the attribute.
```
- `case-insensitive`
- `values are always strings`
- Property-attribute synchronization

### Non-standard attributes, dataset
- like `<div show-info="name"></div>`
- `data-* attributes`: All attributes starting with “data-” are reserved for programmers’ use. They are available in the `dataset` property. Like `<body data-about="Elephants">` then `document.body.dataset.about = Elephants`
- `data-order-state` -> `dataset.orderState`