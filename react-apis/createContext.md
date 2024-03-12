## createContext(defaultValue)
similar to golang context

### Usage
```js
import { createContext } from 'react';
const ThemeContext = createContext('light');
```
- `defaultValue`: The value that you want the context to have when there is `no matching context provider` in the tree above the component that reads context
- return context object, then use SomeContext.Provider in components above to specify the context value, and call useContext(SomeContext) in components to read it

### SomeContext.Provider
- lets you provide the context value to components.
```js
function App() {
  const [theme, setTheme] = useState('light');
  // ...
  return (
    <ThemeContext.Provider value={theme}>
      <Page />
    </ThemeContext.Provider>
  );
}
```
- `value`: The value that you want to pass to all the components reading this context inside this provider, no matter how deep. The context value can be of any type. A component calling `useContext(SomeContext)` inside of the provider receives the value of the innermost corresponding context provider above it.

### Example
```js
// contexts.jsx
export const ThemeContext = createContext('light');
export const AuthContext = createContext(null);

// app.jsx
function App() {
  const [theme, setTheme] = useState('dark');
  const [currentUser, setCurrentUser] = useState({ name: 'Taylor' });
  // ...

  return (
    <ThemeContext.Provider value={theme}>
      <AuthContext.Provider value={currentUser}>
        <Page />
      </AuthContext.Provider>
    </ThemeContext.Provider>
  );
}

// profile.jsx
function Profile() {
  // get the most inner AuthContext.Provider value, if not set, get the defaultValue
  const currentUser = useContext(AuthContext); 
  // ...
}
```