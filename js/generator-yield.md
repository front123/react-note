### Generator function
```js
function* generateSequence() {
    yield 1;
    yield 2;
    return 3;
}

let generator = generateSequence();
```
- can return (“yield”) multiple values, one after another
- `next()`: when called, it runs the execution until the nearest `yield <value>` statement (value can be omitted, then it’s undefined). Then the function execution pauses, and the yielded value is returned to the outer code.
- the result of next()  is a object. `{"value": // the yield value; "done": // true if the function code has finished, otherwise false.}`
- generator is iterable
```js
// only get yield value
for(let value of generator) {}
```
- `generator.next(arg)`: pass value to yield line when resume.
```js
// like a ping-pong interactive
function* gen() {
  let ask1 = yield "2 + 2 = ?";

  alert(ask1); // 4

  let ask2 = yield "3 * 3 = ?"

  alert(ask2); // 9
}

let generator = gen();

alert( generator.next().value ); // "2 + 2 = ?"

alert( generator.next(4).value ); // "3 * 3 = ?"

alert( generator.next(9).done ); // true
```
- `generator.throw(err)`: pass an error into a yield. the err is thrown in the line with that yield.
- `generator.return(value)`: finishes the generator execution and return the given value. This call return `{value, done:true}`


### yield*
-  to “embed” (compose) one generator into another.