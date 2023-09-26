#### Hooks
- useState("")
- useRef("")
- useEffect(()=>{})
- useReducer((state, action)=> newstate, initialArg)
- useMemo(()=> calculateValue, [Dependencies])

#### Syntax
- object spread syntax (shallow: it only copies one level deep.)

- Update Arrays in State

||avoid(mutates the array)|prefer(returns a new array|
|-|-|-|
|adding|push,unshift|concat,[...arr]|
|removing|pop,shift,splice|filter,slice|
|replacing|splice,arr[i]=x|map|
|sorting|reverse,sort|copy the array first|

- Update Objects in State
- Only component, initializer, and reducer functions need to be pure

- Pure component function call, eg. `onClick={handleClick}` or `onClick={()=>{handleClick(i)}}`
- Shallow array copy, eg. : const nextList = [...list]. nextList and list are two different arrays, nextList[0] and list[0] point to the same object

#### 自定义Hook

#### 第三方Hook
- **use-immer** 可取代useState，快速更新复杂对象

#### Redux

#### Side effects
```
While functional programming relies heavily on purity, at some point, somewhere, something has to change. That’s kind of the point of programming! These changes—updating the screen, starting an animation, changing the data—are called side effects. They’re things that happen “on the side”, not during rendering.

In React, side effects usually belong inside event handlers. Event handlers are functions that React runs when you perform some action—for example, when you click a button. Even though event handlers are defined inside your component, they don’t run during rendering! So event handlers don’t need to be pure.

If you’ve exhausted all other options and can’t find the right event handler for your side effect, you can still attach it to your returned JSX with a useEffect call in your component. This tells React to execute it later, after rendering, when side effects are allowed. However, this approach should be your last resort.

When possible, try to express your logic with rendering alone. You’ll be surprised how far this can take you!
```