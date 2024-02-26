## Promise API
### Promise.all(iterable)
- call with `an array of promises`, they would execute in parallel. `Return a new promise`. 
- The new promise resolves when all listed promises are resolved, and the array of their results becomes its result(order by index). 
- If any of the promises is rejected, the promise returned by Promise.all immediately rejects with that error.

### Promise.allSettled(iterable)
- waits for all promises to settle, one promise error would not reject all.
- {status:"fulfilled", value:result} for successful responses.
- {status:"rejected", reason:error} for errors.

### Promise.race(iterable)
- waits only for the first settled promise and gets its result (or error)

### Promise.any(iterable)
- waits only for the `first fulfilled promise` and gets its result
- If all of the given promises are rejected, then the returned promise is `rejected` with `AggregateError` – a special error object that stores all promise errors in its errors property

### Promise.resolve(value)
- same as: `new Promise(resolve => resolve(value));`

### Promise.reject(error)
- same as: `new Promise((resolve, reject) => reject(error));`