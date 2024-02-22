### 7 primitve types
string, number, bigint, boolean, symbol, null, undefined
- except null and undefined, some primitive has methods.
- `num.toString(16)` get num hex value string, argument can be 2 to 36. eg. 3..toString(2) -> 11
- 0b binary, 0o octal, 0x hex.
- `0.1 + 0.2 == 0.30000000000000004` A number is stored in memory in its binary form, a sequence of bits. 对于分数就会出现像十进制里面1/3这种无限循环分数情况。使用+sum.toFixed(2)去获取期望值。
- `parseInt  parseFloat` convert 12px to 12, 12.3em to 12.3,  a123 to NaN
- `parseInt(str, radix)` radix进制，表示当前str的进制表示。转换后是10进制值。
- `Math.random()` return [0,1)
- `Math.max(a, b, c...) and Math.min(a, b, c...)`
- `Math.pow(n, power)` pow(2,4) -> 16

### string method
- `str.at(-1)`
- `str.toUpperCase()`
- `str.indexOf(substr, startPos)`
- `str.includes(substr, startPos)`
- `str.startWiths(substr, startPos) str.endWiths(substr, endPos)`
- `str.slice(start [, end])` not including end
- `str.substring(start [, end])` not including end
- `str.substr(start [, length])`
- `str.codePointAt(0)` get the character for the code
- `String.fromCodePoint(code)` 90 -> Z
- `str.trim()`
- `str.repeat(n)`
- `str.localeCompare(str2)`
- `str.split(delim)` str.split('') return a letters array

### 1 object type
object
- `for (let key in arr)` 遍历key

### Array type is object
- `arr.push(obj1,obj2...) arr.pop()` operate end of array
- `arr.shift()` remove first element
- `arr.unshift(obj1,obj2...)` insert element to begin
- `for(let ele of arr)` 遍历
- `for(let key in arr)` never use 避免此种遍历，可能会出现非index的key
- `arr.length = 0` 清空数组
- `delete arr[0]` removes a value by the key. 仅情况位置上的内容，位置将保留。
- `removedArr = arr.splice(start[, deleteCount, elem1, ..., elemN])` do insert, remove and replace elements. It modifies arr starting from the index start: removes `deleteCount` elements and then inserts elem1, ..., elemN at their place. Returns `the array of removed elements.`
- `arr.slice([start], [end])` returns a new array copying to it all items from index start to end (not including end).
- `arr.concat(arg1, arg2...)` creates a new array, arg can be a array
- `arr.forEach(function(item, index, array) {}`
- `arr.indexOf(item, startFromIndex)` search item
- `arr.includes(item, startFromIndex)`
- `arr.lastIndexOf()`
- `let result = arr.find(function(item, index, array) {}` return true then item return and iteration stop.
- `let results = arr.filter(function(item[, index, array]) {}` return true then item append to results and continue.
- `let result = arr.map(function(item[, index, array]){}` 遍历每个元素，返回新的元素值
- `arr.sort(comparefn(a,b))` sorts the array in place, changing its element order. comparrefn return >0 if a > b; return <0 if a < b.
- `arr.reverse()` 翻转数组
- `arr.join(glue)`
- `Array.isArray`
- `arr.some(fn)/arr.every(fn)` like || and &&
- `let value = arr.reduce(function(accumulator, item, index, array) {}, [initial])` calculate a single value(accumulator) based on the array. accumulator – is the result of the previous function call

### Map type
- new Map()
- map.set(k, v) or map.set(k1,v1).set(k2,v2)...
- map.get(k)
- map.has(k)
- map.delete(k)
- map.clear()
- map.size  
#### Map iteration
- map.keys()
- map.values()
- map.entries() return entry[k,v]
- map.forEach((value, key, map) => {})
#### Map & Object convertion
- new Map(Object.entries(obj)): obj to map
- Object.fromEntries(map.entries()): map to object

### Set type
- new Set([array])
- set.add(v)
- set.delete(v)
- set.has(v)
- set.clear()
- set.size
#### Set iteration
- for (let value of set)
- set.forEach((value, valueAgain, set) => {})
- set.keys()
- set.values()
- set.entries() return entry[value,value]

### WeakMap & WeakSet
Help for GC. Can only add object as key. If obj set to null(become unreachable), then it would auto remove from map or set. The most notable limitation of WeakMap and WeakSet is the absence of iterations, and the inability to get all current content.
#### use cases
- additonal data
- cache

### Object.keys(obj), Object.values(obj), Object.entries()
returns an array

### Destructuring assignment from array or object or any iterable
- `let [item1, ,item2] = arr`: arr[0] to item1, ignore arr[1], arr[2] to item2
- `let [name1, name2, ...rest] = ["Julius", "Caesar", "Consul"]`: the rest is a array contain rest elements
- `let [name = "Guest", surname = "Anonymous"] = ["Julius"]`: surname use default value
- `let {height, width, title} = { title: "Menu", height: 200, width: 100 }`
- `let {width: w, height: h, title} = options`: rename left-side
- `let {width = 100, height = 200, title} = options`: set default value
- `let {width: w = 100, height: h = 200, title} = options`
- `function({incomingProperty: varName = defaultValue})`  
https://javascript.info/destructuring-assignment

### Date and time
- `new Date("2017-01-26")`
- `new Date(year, month, date, hours, minutes, seconds, ms)`: year 4 digits, month 0~11, date is day of month.
- `Date.parse(str)`: YYYY-MM-DDTHH:mm:ss.sssZ

### JSON methods
- `JSON.stringify` to convert objects into JSON.
- `JSON.parse` to convert JSON back into an object