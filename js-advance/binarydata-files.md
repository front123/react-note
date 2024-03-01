### ArrayBuffer binary data
- `let buffer = new ArrayBuffer(16)`: a reference to a fixed-length contiguous memory area.
- use a “view” object to operate ArrayBuffer, below:  
`Uint8Array` – treats each byte in ArrayBuffer as a separate number, with possible values from 0 to 255.  
`Uint16Array` – treats every 2 bytes as an integer, with possible values from 0 to 65535.  
`Uint32Array` – treats every 4 bytes as an integer, with possible values from 0 to 4294967295.
```js
// usage
let buffer = new ArrayBuffer(16);
let view = new Uint32Array(buffer);
// view.length == 4 just 16/4
// modify
view[0] = 123456;
```

### TypedArray(just like Uint32Array)
- have indexes and are iterable.
- new TypedArray(buffer, [byteOffset], [length])
- new TypedArray(object)
- new TypedArray(typedArray)
- new TypedArray(length)
- Out-of-bounds behavior would cut left
- can iterate, map, slice, find, reduce


### TextDecoder
- given the buffer and the encoding, read the value to js string
- `let decoder = new TextDecoder([label],[options])` label default is utf-8
- `let str = decoder.decode([input], [options])` input is buffer
```js
let uint8Array = new Uint8Array([72, 101, 108, 108, 111]);
alert( new TextDecoder().decode(uint8Array) ); // Hello
```

### TextEncoder
- converts a string into bytes.
- `let encoder = new TextEncoder();` support utf-8
- `encode(str)` – returns Uint8Array from a string.
- `encodeInto(str, destination)` – encodes str into destination that must be Uint8Array

### File
- inherits from Blob
- new File(fileParts, fileName, [options])
- fileParts – is an array of `Blob/BufferSource/String` values.
- fileName – file name string.

### FileReader
- read data from Blob or File object.
- `let reader = new FileReader();`
- `readAsArrayBuffer(blob)` – read the data in binary format ArrayBuffer.
- `readAsText(blob, [encoding])` – read the data as a text string with the given encoding
- `readAsDataURL(blob)` – read the binary data and encode it as base64 data url.
- has events when reading proceeds