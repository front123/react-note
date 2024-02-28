## DOM events

- HTML attribute: onclick="...".
- DOM property: elem.onclick = function.
- Methods: elem.addEventListener(eventName, function(event){}) to add, removeEventListener to remove. elem.dispatchEvent(event)


### Event properties
- event.preventDefault()
- `event.target`: the “target” element that initiated the event, it doesn’t change through the bubbling process.
- `event.currentTarget`: current element that has a currently running handler on it.

### Event bubbling
When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.
- `event.stopPropagation()`: stop the bubbling

```js
// when click on p, then alert p->div->form
<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```

### Event delegation
Parent element can catch the sub element event and dispatch to corresponding handler, no need to assign different handlers to sub element. Using event.target.

The delegation algorithm:
1. Put a single handler on the container.
2. In the handler – check the source element event.target.
3. If the event happened inside an element that interests us, then handle the event.

## Element events

### Input
- change, input, cut, copy, paste
- focus/blur

### Form
- onsubmit


### Dispatching custom events

#### Built-in event
```js
let event = new Event(type[, options])
// type – event type, a string like "click" or our own like "my-event".
// options - the object {bubbles: false, cancelable: false}.
// - bubbles: true/false – if true, then the event bubbles.
// - cancelable: true/false – if true, then the “default action” may be prevented
```

#### Custom event
- `new CustomEvent(eventName, {})`
- the second argument (object) we can add an additional property detail for any custom information that we want to pass with the event.

### Events-in-events are synchronous
- wrap dispatchEvent with setTimeout(), then it runs asynchronously