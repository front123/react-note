### useRef

useRef returns a ref object with a single `current property `initially set to the `initial value `
```
const objRef = useRef(initialVal);
```

`Key points`
- Use `current` to store info (which doesn’t affect the visual output of your component), can read later, next-render useRef would return same object(but current value may change).
- Changing a ref does not trigger a re-render.


`Notes`
```
function MyComponent() {
  // ...
  // 🚩 Don't write a ref during rendering
  myRef.current = 123;
  // ...
  // 🚩 Don't read a ref during rendering
  return <h1>{myOtherRef.current}</h1>;
}

function MyComponent2() {
  // ...
  useEffect(() => {
    // ✅ You can read or write refs in effects
    myRef.current = 123;
  });
  // ...
  function handleClick() {
    // ✅ You can read or write refs in event handlers
    doSomething(myOtherRef.current);
  }
  // ...
}
```

`Manipulating the DOM with useRef`
```
// In Render
const inputRef = useRef(null);

// In Function
inputRef.current.focus();

// In DOM
<input ref={inputRef} />

// In own component
<MyInput ref={inputRef} />
```

`forwardRef`
help the parent component can get a ref to it.
```
import { forwardRef } from 'react';

const MyInput = forwardRef(({ value, onChange }, ref) => {
  return (
    <input
      value={value}
      onChange={onChange}
      ref={ref}
    />
  );
});

export default MyInput;
```