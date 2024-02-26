### Microtasks
- promiseJobs, enqueue FIFO
- excute asynchronously

### Async/await
#### async
- `async function f(){}`
- make a function always returns a promise. The f() can return a promise, return other values are wrapped in a resolved promise automatically.
- can chain the async function with `then/catch`


#### await
- `let val = await promise;`
- await makes JavaScript wait until that promise settles and returns its result.
- works only inside async functions.
- The wait time, that doesn’t cost any CPU resources, because the JavaScript engine can do other jobs in the meantime: execute other scripts, handle events, etc
- wrapping
```js
(async () => {
  let response = await fetch('xx');
  let user = await response.json();
  ...
})();
```
- await accepts “thenables”, can use on non-promise but promise-compatible object
- await the promise may throw error in rejection, use `try...catch` to wrap await code and handle error