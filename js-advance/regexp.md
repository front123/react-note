### Create regexp
- `regexp = new RegExp("pattern", "flags")`
- `regexp = /pattern/` or with flags `regexp = /pattern/igm`


### Flags
- `i`: With this flag the search is case-insensitive: no difference between A and a
- `g`: With this flag the search looks for all matches, without it – only the first match is returned
- `m`: Multiline mode
- `s`: Enables “dotall” mode, that allows a dot . to match newline character \n
- `u`: Enables full Unicode support
- `y`: “Sticky” mode: searching at the exact position in the text

### str.match(regexp)
- finds all matches of regexp in the string str. return an array
- if not find any, return null
```js
// example
let str = "We will, we will rock you";

// let result = str.match(/we/ig); // return an array
let result = str.match(/we/i); // return the first substring that matchs as an array, then related capturing groups.
```
- 

### str.replace(regexp, replacement)

### regexp.test(str)
- looks for at least one match, if found, returns true, otherwise false
```js
// example
let str = "I love JavaScript";
let regexp = /LOVE/i;
regexp.test(str) // true
```

### Capture groups
- It allows to get a part of the match as a separate item in the result array.
- If we put a quantifier after the parentheses, it applies to the parentheses as a whole.
```js
// example 
'Gogogo now!'.match(/(go)+/ig) // return Gogogo
```