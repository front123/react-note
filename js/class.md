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
- check on object prototype chain
- `obj instanceof Class`: returns true if obj belongs to the Class or a class inheriting from it
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