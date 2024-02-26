### for...of
- iterate Map/Set/Array/String
- get value directly
- would not iterate prototype chain
- `Symbol.iterator` make object iterable
```js
let range = {
  from: 1,
  to: 5,

  [Symbol.iterator]() { // called once, in the beginning of for..of
    return {
      current: this.from,
      last: this.to,

      next() { // called every iteration, to get the next value
        if (this.current <= this.last) {
          return { done: false, value: this.current++ };
        } else {
          return { done: true };
        }
      }
    };
  }
};

for(let value of range) {
  alert(value); // 1 then 2, then 3, then 4, then 5
}
```

### for await..of
- Symbol.asyncIterator

### for...in
- iterate the properties(enumerable) of object. Only lists enumerable properties
- can use on array, you get the index not value
- may iterate object prototype chain