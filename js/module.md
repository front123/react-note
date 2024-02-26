### Module
- `export/import`
- `<script type="module">`
- Modules always work in strict mode
- `one-time evaluation`: If the same module is imported into multiple other modules, its code is executed only once. Exports are generated, and then they are shared between importers.
- `import.meta` contains the information about the current module
- modules are deferred, regular script runs immediately
- import must get either a relative or absolute URL
- `webpack`: bundle modules together


### export
- export before declarations
```js
export let v = "x";
export class User{} // no ;
export function f(){} // no ;
export const N = "n";

export {f1, f2} // export some function
export {sayHi as hi, sayBye as bye}; // outer should call hi/bye
```
- `export default`: only one default export per file
```js
export {sayHi as default}

export default class User {}
// then import
import User from './user.js'; // not {User}, just User

// when mixin
import {default as User, sayHi} from './user.js'
```
- export default with no name
```js
export default class {}
export default function() {}
export default [array]
```

### import
- `import {f1, f2} from './xx/js'`
- `import * as fs from './xx.js'`: import all as object fs

### re-export
- export {default [as y]} from "module" (re-export default)
- export {sayHi} from './say.js'
- export * from "module" (doesn’t re-export default).

### Dynamic imports
- `import(module)`: returns a promise
```js
import(modulePath)
  .then(obj => <module object>)
  .catch(err => <loading error, e.g. if no such module>)

let {hi, bye} = await import('./say.js');
```