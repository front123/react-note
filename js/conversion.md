## Conversion

`String(xxx)` convert to string type.

`Number(xxx)`  
Numeric conversion in mathematical functions and expressions happens automatically.  
- Number("123") -> 123  
- Number("abc") -> NaN  
- Number(null) -> 0
- Number(undefined) -> NaN
- Number(true or false) -> 1/0

`Boolean(xxx)`  
- Values that are intuitively “empty”, like 0, an empty string, null, undefined, and NaN, become false.
- Other values become true. Any non-empty string is true.

#### When comparing values of different types, JavaScript converts the values to numbers.
- '2' > 1  return true
- '01' == 1 return true
- 0 == false return true

A strict equality operator === checks the equality without type conversion.

An equality check == and comparisons > < >= <= work differently.  
`null == undefined` --> true.  
`null > 0`  --> Number(null) > 0 return false.  
`null == 0` --> false, the equality check == for undefined and null is defined such that, without any conversions, they equal each other and don’t equal anything else.
