### useState

useage
```
const [age, setAge] = useState(29);
const [name, setName] = useState('front');
const [todos, setTodos] = useState(()=>createTodos());
```

The set function that lets you update the state to a different value and trigger a `re-render`. 2ways use to update state.
```
setName('newName');
// only one argument and return next state
setName(prevName => prevName + 'go');
```

```
// a = 20
setA(a => a+1); //21
setA(a => a+1); //22
```
a => a + 1 is your updater function. It takes the pending state and calculates the next state from it.

React puts your updater functions in a queue. Then, during the next render, it will call them in the same order.

`useState(object)`
```
//should replace whole object
const [form, setForm] = useState({"name":"x","age":12})

setForm({
    ...form,
    name: "bbb"
})
```

`useState(nestedObj)`
```
const [person, setPerson] = useState({
    name: 'Niki de Saint Phalle',
    artwork: {
      title: 'Blue Nana',
      city: 'Hamburg',
      image: 'https://i.imgur.com/Sd1AgUOm.jpg',
    }
  });

setPerson({
    ...person,
    artwork: {
    ...person.artwork,
    title: e.target.value
    }
});
```

`useState(array)`
```
const initialTodos = [
  { id: 0, title: 'Buy milk', done: true },
  { id: 1, title: 'Eat tacos', done: false },
  { id: 2, title: 'Brew tea', done: false },
];

const [todos, setTodos] = useState(initialTodos);

// add element
setTodos([
    ...todos,
    {
        //xxx
    }
])

// delete element
setTodos(todos.filter(t => t.id != deleteId))

// change element
setTodos(todos.map(t => {
    if (t.id === targetId) {
        t.Desc = "xxx"
    }
    return t;
}))
```
` useImmer(array|object)` help to write simple code
```
import { useImmer } from 'use-immer';
const initialList = [
  { id: 0, title: 'Big Bellies', seen: false },
  { id: 1, title: 'Lunar Landscape', seen: false },
  { id: 2, title: 'Terracotta Army', seen: true },
];

const [list, updateList] = useImmer(initialList);

updateList(draft => {
    const artwork = draft.find(a =>
        a.id === artworkId
    );
    artwork.seen = nextSeen;
});
```

Pass initializer function vs Pass initial state
```
// more efficient
const [todos, setTodos] = useState(createInitialTodos);

// would run function every re-render
const [todos, setTodos] = useState(createInitialTodos());
```

`Resetting state with a key`
```
// A react component can be re-create by reset the key
// When the key changes, React re-creates the Form
// component (and all of its children) from scratch, so its
// state gets reset.

export default function App() {
  const [version, setVersion] = useState(0);
  function handleReset() {
    setVersion(version + 1);
  }
  return (
    <>
      <button onClick={handleReset}>Reset</button>
      <Form key={version} />
    </>
  );
}

function Form() {
  const [name, setName] = useState('Taylor');
  return (
    <>
      <input
        value={name}
        onChange={e => setName(e.target.value)}
      />
      <p>Hello, {name}.</p>
    </>
  );
}
```
