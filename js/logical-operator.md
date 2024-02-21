### Logical Operators

They can be applied to values of any type, not only boolean. Their result can also be of any type.  
If an operand is not a boolean, it’s converted to a boolean for the evaluation. Boolean(xxx)

`OR ||`  
(0 || "" || false || "good") return "good". A value is returned in its original form, without the conversion.
- Evaluates operands from left to right.
- For each operand, converts it to boolean. If the result is true, stops and returns the original value of that operand.
- If all operands have been evaluated (i.e. all were false), returns the last operand.
- A chain of OR || returns the first truthy value or the last one if no truthy value is found.

`AND &&`  
- Evaluates operands from left to right.
- For each operand, converts it to a boolean. If the result is false, stops and returns the original value of that operand.
- If all operands have been evaluated (i.e. all were truthy), returns the last operand.
- In other words, AND returns the first falsy value or the last value if none were found.

`NOT !`  
- Converts the operand to boolean type.
- Returns the inverse value.  
- A double NOT !! is sometimes used for converting a value to boolean type: !!null -> false same as Boolean(null).


`Nullish Coalescing ??`  
The result of a ?? b is:

- if a is defined, then a,
- if a isn’t defined, then b.
- In other words, ?? returns the first argument if it’s not null/undefined. Otherwise, the second one.
