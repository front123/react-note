### Constructor
- has default constructor if not define
- if inherit a class, super(...) need call in first line of constructor. 
### Super
- `super.method(...)`
- `super(...)`: can only call in first line of constructor.
- Arrow functions don’t have their own this or super, so they transparently fit into the surrounding context.

### Class field initialization order
- Before constructor for the base class
- Immediately after super() for the derived class

### Method(){} not method: function(){}

### [[HomeObject]]
- Methods remember their class/object in the internal [[HomeObject]] property. That’s how super resolves parent methods.

### Static method/property
- `static method1(){}`
- own to class, usage: User.method1()
- “factory” method: static method to return new instance. like: `return this(a,b)`
- Static methods are callable on classes, not on individual objects.
- `Static properties`: static publisher = "xx"
- Static properties and methods are inherited

### Class instance properties and methods
- no need let/var/const
- `publicField = 'public property'`
- `#privateField = 'private property'`
- `_protectedField = 'protect property'`:  protected fields are naturally inheritable
- `#method1(){}`: private method

### Class checking instanceof 
- to check whether an object belongs to a certain class
- check on obj prototype chain
- `obj instanceof Class`: returns true if obj belongs to the Class or a class inheriting from it
```js
// check (rabbit.prototype or rabbit.prototype.prototype or ...) ==? Animal.prototype 
(rabbit instanceof Animal)
```
- custom the rule check instanceof
```js
// define this static method in class
static [Symbol.hasInstance](obj) {
if (xxx) return true;
}
```
- `obj instanceof Class` can be rephrased as `Class.prototype.isPrototypeOf(obj)`.

### type-checking
- `typeof`: primitives return string
- `instanceof`: objects return true/false
- `{}.toString`: primitives, built-in objects, objects with Symbol.toStringTag return string. `window[Symbol.toStringTag]` = Window

### Mixins
- js does not support multiple inheritance
- a mixin is a class containing methods that can be used by other classes without a need to inherit from it.
- `Object.assign(User.prototype, sayHiMixin)` like bind extra methods to class.
- `event mixins`: Object.assign(Menu.prototype, eventMixin), then Menu instance can call on/off/trigger methods.
```js
let eventMixin = {
  /**
   * Subscribe to event, usage:
   *  menu.on('select', function(item) { ... }
  */
  on(eventName, handler) {
    if (!this._eventHandlers) this._eventHandlers = {};
    if (!this._eventHandlers[eventName]) {
      this._eventHandlers[eventName] = [];
    }
    this._eventHandlers[eventName].push(handler);
  },

  /**
   * Cancel the subscription, usage:
   *  menu.off('select', handler)
   */
  off(eventName, handler) {
    let handlers = this._eventHandlers?.[eventName];
    if (!handlers) return;
    for (let i = 0; i < handlers.length; i++) {
      if (handlers[i] === handler) {
        handlers.splice(i--, 1);
      }
    }
  },

  /**
   * Generate an event with the given name and data
   *  this.trigger('select', data1, data2);
   */
  trigger(eventName, ...args) {
    if (!this._eventHandlers?.[eventName]) {
      return; // no handlers for that event name
    }

    // call the handlers
    this._eventHandlers[eventName].forEach(handler => handler.apply(this, args));
  }
};
```