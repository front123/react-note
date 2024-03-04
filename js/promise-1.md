### Promise
```js
let promise = new Promise(function(resolve, reject) {
  // executor (the producing code, "singer")
});
```
- When new Promise is created, the executor runs automatically
- resolve/reject are callback function. when executor obtains result or error, it should call resolve/reject.
- `resolve(value)` — if the job is finished successfully, with result value.
- `reject(error)` — if an error has occurred, error is the error object. Use Error or other objects that inherit from Error.
- call only one resolve or one reject, later call resolve/reject would ignore.

### Promise object properties
- `state`: `pending` -> `fulfilled` when resolve called; `rejected` when reject called
- `result`: `undefined` -> `value` when resolve(value) called; `error` when reject(error) called

### Consumers: then, catch
```js
promiseObj.then(
  function(result){/* handle a successful result */},
  function(error){/* handle a error */}
)
```
- first func: uns when the promise is resolved and receives the result
- second func: runs when the promise is rejected and receives the error
- can add then handler many times

```js
.then(null, errorHandlingFunction)
// same as
.catch(errorHandlingFunction)
```
- The `final .catch` not only catches explicit rejections, but also accidental errors in the handlers `then`.
- `.finally(()=>{..})`: performing cleanup/finalizing

### Promise chain
- `promiseObj.then(res=>{}).then(res=>{})`:the result is passed through the chain of .then handlers. `then` handler should return the result.

### fetch(url)
- return a promise
- can `.then(response=>{})`

### Unhandle rejection
```js
window.addEventListener('unhandledrejection', function(event) {
  // the event object has two special properties:
  alert(event.promise); // [object Promise] - the promise that generated the error
  alert(event.reason); // Error: Whoops! - the unhandled error object
});

new Promise(function() {
  throw new Error("Whoops!");
}); // no catch to handle the error
```
