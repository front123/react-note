### fetch()
- `let promise = fetch(url, [options])`: can set methods, headers etc. on options
- `let response = await fetch(url)`
- First, the promise, returned by fetch, resolves with an object of the built-in Response class as soon as the server responds with headers.
- Second, to get the response body, we need to use an additional method call.

#### fetch() response methods
- promise-based methods, when use may need `await`
- `response.text()` – read the response and return as text
- `response.json()` – parse the response as JSON
- `response.formData()` – return the response as FormData object
- `response.blob()` – return the response as Blob (binary data with type)
- `response.arrayBuffer()` – return the response as ArrayBuffer (low-level representation of binary data)
- `response.read()` - return a promise, result={done, value}, read response by chunk
- `response.headers`: a Map-like headers object, use getter/setter
- `post request`
```js
let user = {
  name: 'John',
  surname: 'Smith'
};

let response = await fetch('/article/fetch/post/user', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json;charset=utf-8'
  },
  body: JSON.stringify(user)
  // body 
  // 1. can be a string(JSON encoded then set application/json. other then set text/plain)
  // 2. FormData object, to submit the data as multipart/form-data
  // 3. Blob/BufferSource to send binary data, e.g. image
  // 4. URLSearchParams, to submit the data in x-www-form-urlencoded encoding 
});

let result = await response.json();
```

### FormData
- sending HTML forms: with or without files, with additional fields and so on.
- `let formData = new FormData([formElem])`
- always sent as Content-Type: multipart/form-data.
- can set to fetch method body
- can sent file, use `<input type="file" name="image">` in form element; or `formData.append("image", imageBlob, "image.png")`
- get/set/append/delete/has


### URL object
- creating and parsing URLs
- `new URL(url, [base])`: url: the full URL or only path(if base is set)
- can use a URL object in fetch or XMLHttpRequest
- `url.searchParams`: ?query=JavaScript
```js
//URLSearchParams
append(name, value) – add the parameter by name,
delete(name) – remove the parameter by name,
get(name) – get the parameter by name,
getAll(name) – get all parameters with the same name (that’s possible, e.g. ?user=John&user=Pete),
has(name) – check for the existence of the parameter by name,
set(name, value) – set/replace the parameter,
sort() – sort parameters by name, rarely needed,
```
- `url.toString()`: auto encode url to valid string

### XMLHttpRequest
- let xhr = new XMLHttpRequest()
- xhr.open(method, URL, [async, user, password])
- xhr.send([body])
- xhr.onload = function(){}
- xhr.onerror = function(){}
- xhr.status/xhr.statusText/xhr.response

### Websocket
- let socket = new WebSocket("ws://javascript.info") or wss://
- `onopen` – socket.onopen = function(e){}, connection established
- `onmessage` – data received
- `onerror` – websocket error
- `onclose` – connection closed
- `socket.send(body)` allows body in string or a binary format, including Blob, ArrayBuffer
- `socket.close([code], [reason])`