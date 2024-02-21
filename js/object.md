### Object
#### Object copy
- `Object.assign(dest, ...sources)` simple clone, just copy nested object reference.
- `structuredClone` deep clone
- `lodash deep clone` _.cloneDeep(obj). 

#### GC
- reachability.  
- mark-and-sweep from roots. Mark the reachable object. Remove unmarked object.

JS engine optimizations:
- Generational collection
- Incremental collection
- Idle-time collection

#### this
Evaluate in run context. When obj.f() is called, the `this` is obj.

Calling function without an object: this == undefined. Like function sayHi() {
  alert(this); // this == undefined
}

Arrow functions have no “this”. () => {console.log(this.xx)}. The `this` is from the outer context.

`?.`  
The optional chaining ?. stops the evaluation if the value before ?. is undefined or null and returns undefined.  
let user = {};
user?.address?.street ==> undefined. delete user?.name;  
- `obj?.prop` – returns obj.prop if obj exists, otherwise undefined.
- `obj?.[prop]` – returns obj[prop] if obj exists, otherwise undefined.
- `obj.method?.()` – calls obj.method() if obj.method exists, otherwise returns undefined.

#### Object property key
- `string type` obj[1] == obj["1"]  obj[true] = obj["true"]
- `symbol type`, Symbol is a primitive type for unique identifiers.

demo
```javascript
let user = { // belongs to another code
  name: "John"
};
let id = Symbol("id");
user[id] = 1;
console.log(user[id]);
```
As user objects belong to another codebase, it’s unsafe to add fields to them, since we might affect pre-defined behavior in that other codebase. However, symbols cannot be accessed accidentally. The third-party code won’t be aware of newly defined symbols, so it’s safe to add symbols to the user objects. Avoid overwritten.
- Symbols are skipped by for…in, hiding symbolic properties
- Object.assign copies both string and symbol properties

#### Global symbol registry
- `Symbol.for(key)` create or reuse a global symbol. Can get same symbol again if symbol created.
- `Symbol.keyFor(sym)` return the key of the sym.


#### Object conversion
- `object-to-string` conversion, when we’re doing an operation on an object that expects a string. e.g. stu2[stu1] = 1. stu1 convert to [object Object].
- `object-to-number`

define function `[Symbol.toPrimitive](hint){}` for object to handle conversion.
- here goes the code to convert this object to a primitive
- `it must return a primitive value`
- hint = one of "string", "number", "default"
- If there’s no Symbol.toPrimitive then JavaScript tries to find methods toString and valueOf

By default, a plain object has following toString and valueOf methods:

The toString method returns a string "[object Object]".  
The valueOf method returns the object itself.