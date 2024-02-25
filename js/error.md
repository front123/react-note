### Try catch
- try {} catch(err) {}
- only catch runtime exception
- err object properties: name, message, stack(current call stack)

### Throw a error
- throw <custom error>
- throw new Error("message")
- standard errors: `Error/SyntaxError/ReferenceError/TypeError` 
- check the error type: `  if (err instanceof ReferenceError) {}`
- `try…catch…finally`: execute always, after try or catch block. finally block excuted before any return statement.
- `try...finally`

### Global catch
- `window.onerror = function(message, url, line, col, error) {}`

### Custom error
```js
class MyError extends Error {
  constructor(message) {
    super(message);
    this.name = "MyError"
    //...
  }
}
```
