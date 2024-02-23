### Object property flags
- `writable`: if true, the value can be changed, otherwise it’s read-only
- `enumerable`: if true, then listed in loops, otherwise not listed
- `configurable`: if true, the property can be deleted and these property can be modified its flags, otherwise not

### Object property methods
- `let descriptor = Object.getOwnPropertyDescriptor(obj, propertyName)`
```js
// descriptor:
{
  "value": "John",
  "writable": true,
  "enumerable": true,
  "configurable": true
}
```
- `Object.defineProperty(obj, propertyName, descriptor)` to change property flags
- Object.defineProperties(obj, {
  prop1: descriptor1,
  prop2: descriptor2
  // ...
});


### Getters and setters
```js
let obj = {
  get propName() {
    // getter, the code executed on getting obj.propName
  },

  set propName(value) {
    // setter, the code executed on setting obj.propName = value
  }
};

//-----------------

Object.defineProperty(user, 'fullName', {
  get() {
    return `${this.name} ${this.surname}`;
  },

  set(value) {
    [this.name, this.surname] = value.split(" ");
  }
});
```

### [[Prototype]]
- object hidden property, is null or references another object.
- use `obj1.__proto__ = obj2` to set obj1.[[protorype]]
- `prototypal inheritance`: when we read a property from object, and it’s missing, JavaScript automatically takes it from its prototype.
- do not circles.
- `Object.getPrototypeOf/Object.setPrototypeOf` use these instead.
- prototype is only used for reading properties, setter/getter are exception. `No matter where the method is found: in an object or its prototype. In a method call, this is always the object before the dot.`
- for..in loop iterates over inherited properties too, if we’d like to exclude inherited properties, use `obj.hasOwnProperty(key)`
- all object inherit `Object.prototype`

### F.prototype
- only used when `new F` is called, it assigns [[Prototype]] of the new object.
- Every function has the "prototype" property
- The default "prototype" is an object with the only property `constructor` that points back to the function itself. Like: `Rabbit.prototype.constructor == Rabbit`
- can use constructor property to create a new object using the same constructor as the existing one. `new obj.constructor()`
- can add/remove properties to default prototype, but don't overwrite it as a whole, in order to preserve constructor property.

### Native prototype
- `Object.prototype`: all inherits from it
- `Array.prototype`
- `Function.prototype`
- `Number.prototype/String.prototype/Boolean.prototype`
- `strings, numbers and booleans`: if we try to access their properties, `temporary wrapper objects` are created using built-in constructors String, Number and Boolean. They provide the methods
- except null and undefined
- can be modified, if we add a method to String.prototype, it becomes available to all strings
- Borrowing methods from prototypes

### Modern methods to get/set a prototype
- `Object.getPrototypeOf(obj)`: returns the [[Prototype]] of obj
- `Object.setPrototypeOf(obj, proto)`: sets the [[Prototype]] of obj to proto
- `Object.create(proto[, descriptors])`: creates an empty object with given proto as [[Prototype]] and optional property descriptors. `Object.create(animal); // same as {__proto__: animal}`
- `__proto__`: is setter / getter method