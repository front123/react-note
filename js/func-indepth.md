### func parameters
- func sum(item1, ...arr)
- func sum() { // arguments[0] }

### Inner/Outer Lexical Environmen (Function Closure)
- All function has a lexical env, that contain its all variables and nested func. When a function runs, at the beginning of the call, a `new Lexical Environment` is created automatically to store local variables and parameters of the call.
- Inner lexical env has a reference to outer lexical env, so that inner can access outer variables.
- When the code wants to access a variable – the inner Lexical Environment is searched first, then the outer one, then the more outer one and so on until the global one.
- All functions have the hidden property named [[Environment]], that keeps the reference to the Lexical Environment where the function was created.

### New Function
- `let func = new Function ([arg1, arg2, ...argN], functionBody)`: let sum = new Function('a', 'b', 'return a + b'); sum(1,2)

### let timerId = setTimeout(func|code, [delay], [arg1], [arg2], ...)
- func: function, can be `() => {}`
- delay: in milliseconds(1000ms = 1s)
- args: Arguments for the function
- clearTimeout(timerId)
- Any setTimeout will run only after the current code has finished

### func.call(context, …args)
call func with context(this)

### func.apply(context, args)

### Function binding
Some scenarios would lost `this`, once a method is passed somewhere separately from the object.
Solution:
- `a wrapper`: function() { obj.funcToCall() }
- `bind`: let boundFunc = obj.funcToCall.bind(obj)
- `let bound = func.bind(context, [arg1], [arg2], ...)`: It allows to bind context as this and starting arguments of the function.

### Arrow functions =>
- Arrow functions have no “this”, If this is accessed, it is taken from the outside.(outer lexical environment)
- can’t run with new
- have no “arguments” variable