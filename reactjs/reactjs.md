# Section A: Javascript Basics for React

## Variables and Data Types

- **Variables**: Store data values. Use let (changeable), const (constant), and var (old, avoid now).

```
let age = 25;
const name = 'Alice';
```

- **Data types**:
  - **Primitive**: Number, String, Boolean, Null, Undefined, Symbol
  - **Object types**: Objects, Arrays, Functions

## Functions & Arrow Functions

- Functions are reusable blocks of code.

```
function greet(name) {
  return `Hello, ${name}`;
}

const greetArrow = (name) => `Hello, ${name}`;
```

## Objects and Arrays

- Objects hold key-value pairs.

```
const person = {
  name: 'Alice',
  age: 25,
};
```

- Arrays hold ordered lists.

```
const fruits = ['apple', 'banana', 'cherry'];
```

## Destructuring

- Extract values from objects or arrays easily.

```
const { name, age } = person;
const [firstFruit, secondFruit] = fruits;
```

## Spread and Rest Operators

- Spread copies or expands arrays/objects.

```
const newFruits = [...fruits, 'date'];
```

- Rest collects remaining elements.

```
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```

## Template Literals

- Use backticks for strings with embedded expressions.

```
const greeting = `Hello, ${name}! You are ${age} years old.`;
```

## Conditional Statements and Ternary Operator

```
if (age > 18) {
  console.log('Adult');
} else {
  console.log('Minor');
}
```

// Ternary

```
const status = age > 18 ? 'Adult' : 'Minor';
```

## Loops

- For loops and array iteration.

```
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

// Using array methods (preferred in React)
fruits.forEach((fruit) => console.log(fruit));
```

## Array Methods (map, filter, find, etc.)

- **map**: transforms array elements.

```
const upperFruits = fruits.map(fruit => fruit.toUpperCase());
```

- **filter**: selects elements by condition.

```
const filtered = fruits.filter(fruit => fruit.startsWith('b'));
```

- **find**: finds first element matching condition.

```
const cherry = fruits.find(fruit => fruit === 'cherry');
```

# Section B: Modern JavaScript (ES6+) Features for React

## 1. let and const — Block Scoped Variables

- **var** was the old way to declare variables but it’s function-scoped and can cause bugs.
- **let** and **const** are block-scoped (only exist inside {} they’re declared in).

```
if (true) {
  let x = 10;
  const y = 20;
  console.log(x, y); // 10 20
}
console.log(x); // ReferenceError: x is not defined
```

- Use _const_ when variable won’t change, _let_ if it will.

## 2. Arrow Functions — Cleaner Function Syntax & this binding

- Arrow functions are concise and do not have their own this (useful in React).

```
const add = (a, b) => a + b;

// More complex with braces and return
const multiply = (a, b) => {
  const result = a * b;
  return result;
};
```

- In React, arrow functions inside components prevent issues with this.

## 3. Default Parameters

- Functions can have default values for parameters.

```
function greet(name = 'Guest') {
  return `Hello, ${name}!`;
}
console.log(greet()); // Hello, Guest!
```

## 4. Template Literals — Multi-line and interpolation

```
const user = { name: 'Alice', age: 25 };
const message = `
  Hello, ${user.name}!
  You are ${user.age} years old.
`;
console.log(message);
```

## 5. Object Property Shorthand and Method Shorthand

```
const name = 'Bob', age = 30;

// Shorthand for object properties
const user = { name, age };

// Method shorthand
const person = {
  greet() {
    return `Hi, I'm ${this.name}`;
  },
};
```

## 6. Destructuring

- Extract multiple properties at once.

```
const person = {
  name: 'Alice',
  age: 25,
  address: {
    city: 'New York',
    zip: 10001,
  },
};

const { name, age, address: { city } } = person;
console.log(name, age, city); // Alice 25 New York
```

## 7. Spread and Rest Operators

- **Spread** expands arrays or objects.

```
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]

const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 }; // {a:1, b:2, c:3}
```

- **Rest** collects remaining arguments or properties.

```
function sum(...nums) {
  return nums.reduce((acc, val) => acc + val, 0);
}
console.log(sum(1, 2, 3)); // 6

const { a, b, ...rest } = { a: 1, b: 2, c: 3, d: 4 };
console.log(rest); // { c: 3, d: 4 }
```

## 8. Classes — Blueprint for objects (React uses them but function components with hooks are preferred now)

```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    return `Hi, I'm ${this.name}`;
  }
}

const alice = new Person('Alice', 25);
console.log(alice.greet()); // Hi, I'm Alice
```

## 9. Modules — Import and Export

- Allows code to be split into reusable files.

```
// utils.js
export function add(a, b) {
  return a + b;
}

// main.js
import { add } from './utils.js';
console.log(add(2, 3)); // 5
```

React uses modules extensively.

## 10. Promises — Handling asynchronous code

```
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Data fetched!');
  }, 1000);
});

fetchData.then(data => console.log(data)); // Data fetched!
```

## 11. Async/Await — Syntactic sugar over promises

```
async function getData() {
  const data = await fetchData;
  console.log(data);
}
getData();
```

## 12. Optional Chaining — Safe navigation of nested properties

```
const user = { name: 'Alice', address: null };
console.log(user.address?.city); // undefined (no error)
```

# Section C: JavaScript Data Structures & Methods Crucial for React

### 1. Arrays — The Backbone of Rendering Lists in React

React apps display lists a lot — from menus to dynamic content. Understanding array methods is critical.

Key methods:

- **map()** — transforms each item into something else (often JSX)

```
const numbers = [1, 2, 3];
const doubled = numbers.map(n => n * 2); // [2, 4, 6]

const listItems = numbers.map(num => <li key={num}>{num}</li>);
```

- **filter()** — select items that match a condition

```
const even = numbers.filter(n => n % 2 === 0); // [2]
```

- **find()** — find first item that matches condition

```
const firstEven = numbers.find(n => n % 2 === 0); // 2
```

- **reduce()** — reduce array to a single value (sum, product, etc.)

```
const sum = numbers.reduce((acc, curr) => acc + curr, 0); // 6
```

### 2. Objects — Passing Props and Managing State

Objects represent structured data. React props and state are often objects.
Accessing and updating:

```
const person = { name: 'Alice', age: 25 };
console.log(person.name); // Alice

const updatedPerson = { ...person, age: 26 }; // create new object with updated age
```

### 3. Sets — Unique collections (React uses for unique IDs or caching)

```
const fruits = new Set(['apple', 'banana', 'apple']);
console.log(fruits); // Set { 'apple', 'banana' }
```

### 4. Maps — Key-value pairs, keys can be any datatype

```
const map = new Map();
map.set('name', 'Alice');
map.set(1, 'one');
console.log(map.get('name')); // Alice
```

### 5. Array & Object Destructuring — Clean data access

```
const user = { id: 1, name: 'Alice', age: 30 };
const { name, age } = user;

const arr = [10, 20, 30];
const [first, second] = arr;
```

### 6. Array Mutation vs Immutability

- React expects state updates to be immutable.
- Instead of modifying arrays or objects directly, create new copies.

```
const arr = [1, 2, 3];
const newArr = [...arr, 4]; // add 4 immutably
```

### 7. Common Array Methods in React State Updates

- concat(), slice(), filter() to return new arrays.
- Avoid push(), pop(), splice() on state arrays (they mutate)

### 8. Important String Methods

- includes(), startsWith(), endsWith() — often used for filtering.

```
const str = "ReactJS";
console.log(str.includes('JS')); // true
```

# Section D: JavaScript Asynchronous Programming for React

### 1. What is Asynchronous Programming?

- Normally, JS executes code synchronously: one line at a time, blocking until the task completes.
- **Asynchronous** allows JS to start a task (like fetching data) and continue running other code while waiting for that task to finish.
- This prevents the UI from freezing while waiting.

### 2. Callbacks — The Old School Way

Functions passed as arguments to be called later.

```
function fetchData(callback) {
  setTimeout(() => {
    callback('Data received!');
  }, 1000);
}

fetchData(data => console.log(data)); // prints after 1 second
```

**Problem**: Callback Hell — nested callbacks become messy.

### 3. Promises — Cleaner Async Handling

- A Promise is an object representing a task that may complete in the future.
- States: pending → fulfilled (success) or rejected (error).

```
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Data received!');
    // or reject('Error occurred!');
  }, 1000);
});

fetchData
  .then(data => console.log(data)) // success
  .catch(error => console.error(error)); // error
```

### 4. Async/Await — Syntactic Sugar for Promises

- Makes async code look synchronous.
- Use async before a function and await before a Promise.

```
async function getData() {
  try {
    const data = await fetchData;
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

getData();
```

### 5. Fetch API — Real-life Data Fetching

- Browser API for network requests, returns a Promise.

```
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => response.json()) // parse JSON body
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

With async/await:

```
async function getPost() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
getPost();
```

### 6. Handling Multiple Promises

- Promise.all waits for multiple promises to finish.

```
const p1 = Promise.resolve(3);
const p2 = 42;
const p3 = new Promise(resolve => setTimeout(resolve, 100, 'foo'));

Promise.all([p1, p2, p3]).then(values => {
  console.log(values); // [3, 42, "foo"]
});
```

### 7. React and Asynchronous Code

- Fetch data inside React lifecycle or hooks (useEffect).
- Use async/await to handle API calls cleanly.
- Manage loading and error states in components.
  Example React snippet:

```
import React, { useState, useEffect } from 'react';

function User() {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchUser() {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
        if (!response.ok) throw new Error('Network response was not ok');
        const data = await response.json();
        setUser(data);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    }

    fetchUser();
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return <div>{user && <h1>{user.name}</h1>}</div>;
}

export default User;
```

# Section E: Closures, Scope & Higher-Order Functions in JavaScript (Vital for React)

### 1. Scope: Where variables live

- Global scope: Variables accessible everywhere.
- Function scope: Variables declared inside functions are local to that function.
- Block scope: Variables declared with let or const inside {} are local to that block.

```
let x = 10; // global scope

function foo() {
  let y = 20; // function scope
  if (true) {
    let z = 30; // block scope
  }
  // z is NOT accessible here
}
```

### 2. Closures: Functions remembering their environment

- A **closure** is a function that “remembers” the variables from where it was created, even if called later.

```
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // 1
counter(); // 2
counter(); // 3
```

Closures allow React hooks like useState and useEffect to capture values across renders.

### 3. Higher-Order Functions (HOF): Functions taking or returning functions

- HOFs are functions that either accept other functions as arguments or return them.
- Array methods like .map(), .filter() take functions as arguments — they’re HOFs.
- We can write your own:

```
function greetMaker(greeting) {
  return function(name) {
    console.log(`${greeting}, ${name}!`);
  };
}

const sayHello = greetMaker('Hello');
sayHello('Alice'); // Hello, Alice!
```

- React components themselves can be HOFs — e.g., higher-order components (HOCs) that wrap other components.

### 4. Using Closures in React

Closures come handy in event handlers and hooks to “remember” state or props.

```
function Counter() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setTimeout(() => {
      // Closure remembers 'count' at time of creation
      alert(`Count is: ${count}`);
    }, 1000);
  }

  return <button onClick={handleClick}>Show Count</button>;
}
```

### 5. Arrow Functions and this Binding

- Arrow functions don’t have their own this, they inherit from their parent scope — useful to avoid _.bind(this)_ in React class components.

# Section F: Event Handling & Synthetic Events in React

### 1. What is Event Handling in React?

- React uses a system called Synthetic Events, which is a cross-browser wrapper around native browser events.
- This system makes event handling consistent across browsers.
- React events are named using camelCase, e.g., onClick, onChange, not lowercase like HTML.

### 2. How to handle events in React?

- Pass a function as the event handler in JSX.
- Unlike HTML, you pass a function, not a string.

```
function Button() {
  function handleClick() {
    alert('Button clicked!');
  }

  return <button onClick={handleClick}>Click me</button>;
}
```

### 3. Event object in React

- Event handlers receive a SyntheticEvent object.
- It wraps the native event and works identically across all browsers.

```
function Input() {
  function handleChange(event) {
    console.log(event.target.value);
  }

  return <input onChange={handleChange} />;
}
```

### 4. Binding this in Class Components (Legacy)

- In React class components, you often bind event handlers in the constructor to keep _this_ context.

```
class Button extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    alert(this.props.message);
  }

  render() {
    return <button onClick={this.handleClick}>Click me</button>;
  }
}
```

- Alternatively, use arrow functions to avoid binding:

```
handleClick = () => {
  alert(this.props.message);
};
```

### 5. Passing Arguments to Event Handlers

```
function Button({ id }) {
  function handleClick(id, event) {
    console.log('Clicked button:', id);
  }

  return <button onClick={e => handleClick(id, e)}>Click me</button>;
}
```

### 6. Common React Events

| Event            | Usage                  |
| :--------------- | :--------------------- |
| onClick          | Mouse click            |
| onChange         | Input or select change |
| onSubmit         | Form submission        |
| onMouseEnter     | Mouse hover            |
| onKeyDown        | Keyboard key press     |
| onFocus / onBlur | Input focus/blur       |

### 7. Preventing Default Behavior

Use event.preventDefault() to stop default form submit or link navigation.

```
function Form() {
  function handleSubmit(event) {
    event.preventDefault();
    alert('Form submitted!');
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

# Section G: React Components & Props — The Heart of React

### 1. What is a React Component?

- A component is a reusable piece of UI, like a JavaScript function or class that returns JSX (HTML-like syntax).
- Components let you split the UI into independent, reusable pieces.

### 2. Types of Components

Functional Components (Modern, recommended)

```
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
```

or using ES6 arrow function:

```
const Welcome = (props) => <h1>Hello, {props.name}!</h1>;
```

Class Components (Legacy, less used now)

```
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

### 3. JSX — How Components Return UI

- Components return JSX, which looks like HTML but is actually JavaScript.
- JSX lets you write UI declaratively.

```
const element = <h1>Hello, world!</h1>;
```

### 4. What are Props?

- **Props** (short for “properties”) are inputs to components.
- Props are _read-only_ and passed from parent to child.
- They allow you to customize components.

```
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

<Greeting name="Alice" />
```

### 5. Passing Props

- Props are passed like attributes in JSX.
- Props can be any data type: string, number, boolean, function, object, array.

```
<MyComponent
  title="My Title"
  count={10}
  isActive={true}
  onClick={() => alert('Clicked!')}
/>
```

### 6. Accessing Props in Functional Components

```
function User(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>Age: {props.age}</p>
    </div>
  );
}
```

You can use destructuring for cleaner code:

```
function User({ name, age }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
    </div>
  );
}
```

### 7. Props are Read-Only

- You should never modify props inside a component.
- If you need to change data, use state.

### 8. Default Props & PropTypes (Basic Validation)

- You can set default props so your component has fallback values.

```
function Button({ text }) {
  return <button>{text}</button>;
}

Button.defaultProps = {
  text: 'Click me',
};
```

- You can also use PropTypes package to validate props (good for bigger apps).

### 9. Nesting Components

- Components can be nested to build complex UIs.

```
function App() {
  return (
    <div>
      <Greeting name="Alice" />
      <Greeting name="Bob" />
    </div>
  );
}
```

# Section H: React State & Lifecycle — Making Components Interactive

### 1. What is State in React?

- **State** is a special object that holds data that can change over time.
- Unlike **props**, state is **managed inside** the component.
- When state changes, React **re-renders** the component to update the UI.

### 2. State vs Props — Quick Recap

| Aspect      | Props               | State                    |
| :---------- | :------------------ | :----------------------- |
| Data source | Passed from parent  | Managed inside component |
| Mutability  | Read-only           | Mutable                  |
| Purpose     | Configure component | Track component data     |
| Update By   | parent              | By the component itself  |

### 3. Adding State in Functional Components — useState Hook

In modern React, **hooks** are used to manage state in functional components.

```
import React, { useState } from 'react';

function Counter() {
  // Declare a state variable "count" with initial value 0
  const [count, setCount] = useState(0);

  // Function to update the state
  function increment() {
    setCount(count + 1);
  }

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increase</button>
    </div>
  );
}
```

- useState returns an **array**: [stateVariable, setterFunction].
- Call setCount(newValue) to update state — this triggers re-render.

### 4. Rules of Using useState

- Only call hooks at the top level of your component or custom hooks.
- Don’t call hooks inside loops, conditions, or nested functions.
- Hooks must be called in the same order on every render.

### 5. State Updates are Asynchronous and Batched

- React batches multiple state updates for performance.
- You can pass a function to the setter to get the latest state value.

```
setCount(prevCount => prevCount + 1);
```

This is important when updating state based on previous state.

### 6. Lifecycle in React Functional Components — useEffect

- React functional components don’t have lifecycle methods like classes.
- Instead, they use the useEffect hook to perform side effects (data fetching, subscriptions, manual DOM updates).

```
import React, { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const intervalId = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);

    // Cleanup function runs when component unmounts or before effect runs again
    return () => clearInterval(intervalId);
  }, []); // Empty dependency array means effect runs once after first render

  return <div>Seconds: {seconds}</div>;
}
```

- useEffect runs after rendering.
- The cleanup function (returned from effect) runs before the component unmounts or before running the effect again.
- The dependency array controls when the effect runs.

### 7. Lifecycle in Class Components (Brief)

- Mounting: constructor → render → componentDidMount
- Updating: render → componentDidUpdate
- Unmounting: componentWillUnmount

Example (less used now):

```
class Timer extends React.Component {
  state = { seconds: 0 };

  componentDidMount() {
    this.intervalId = setInterval(() => {
      this.setState(prev => ({ seconds: prev.seconds + 1 }));
    }, 1000);
  }

  componentWillUnmount() {
    clearInterval(this.intervalId);
  }

  render() {
    return <div>Seconds: {this.state.seconds}</div>;
  }
}
```

### 8. Why Prefer Functional Components & Hooks?

- Simpler and more readable.
- No this keyword confusion.
- Easier to reuse logic with custom hook-

### 9. Common State Patterns

- Multiple state variables:

```
const [name, setName] = useState('');
const [age, setAge] = useState(0);
```

- Single object state:

```
const [user, setUser] = useState({ name: '', age: 0 });

setUser(prevUser => ({ ...prevUser, name: 'Alice' }));
```

_Note_: Updating nested objects requires careful use of spread/rest syntax.

# Section I: Deep Dive — React Props vs State

### 1. Why This Matters

You might have already seen:

- **Props** = external, passed into a component
- **State** = internal, owned by a component

  But to master React, you need to understand:

- When to use each
- How they affect component design
- How they impact re-rendering
- Common pitfalls and best practices

### 2. Quick Recap: Definitions

| Concept           | Meaning                                                                                |
| :---------------- | :------------------------------------------------------------------------------------- |
| Props             | Data passed from a parent component to a child component                               |
| State             | Data that is managed within the component itself                                       |
| Mutability        | Props are immutable (read-only), state is mutable (updatable via setState or useState) |
| Ownership         | Props belong to parent, state belongs to the component itself                          |
| Re-render trigger | Props change when parent re-renders, state change triggers self re-render              |

### 3. Understanding Through Analogy

Imagine components as functions in math:

```
function Square({ side }) {
  return side * side;
}
```

- The input side is like props — the caller gives them.
- But if the function keeps internal data (like how many times it was called), that’s like state.

### 4. When to Use Props vs State

Use **Props** when:

- You want to pass **data from parent to child**
- The component doesn’t need to modify the data
- You want to **reuse** the same component with different data

```
  function Greeting({ name }) {
    return <h1>Hello, {name}!</h1>;
  }
```

Use **State** when:

- The component needs to **remember or update data**
- Data **changes based on user actions**, API calls, etc.
- You need to trigger **re-renders** on data change

```
  function Counter() {
    const [count, setCount] = useState(0);
    return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
  }
```

### 5. Real-World Example: Todo App

Step 1: App (Parent) holds a list of todos in state

```
function App() {
  const [todos, setTodos] = useState([
    { id: 1, text: 'Learn React', completed: false },
    { id: 2, text: 'Build a project', completed: true },
  ]);

  return (
    <div>
      {todos.map(todo => (
        <TodoItem key={todo.id} todo={todo} />
      ))}
    </div>
  );
}
```

Step 2: TodoItem receives each todo via props

```
function TodoItem({ todo }) {
  return <li>{todo.text} — {todo.completed ? 'Done' : 'Not done'}</li>;
}
```

- ✅ Props used to display data.
- ❌ Don’t update todo inside TodoItem — it’s a prop.

### 6. Combining Props + State

It’s very common to receive data via props and then maintain some local state based on it.

```
function Toggle({ initial }) {
  const [isOn, setIsOn] = useState(initial); // initial value from prop

  return (
    <button onClick={() => setIsOn(prev => !prev)}>
      {isOn ? 'ON' : 'OFF'}
    </button>
  );
}
```

🧠 **Best Practice:**

- Use props to pass initial values, not to control updates unless using controlled components.

### 7. 🚨 Common Mistakes & How to Avoid Them

| Mistake                          | Why it's bad                       | How to fix                    |
| :------------------------------- | :--------------------------------- | ----------------------------- |
| Modifying props inside child     | Violates React's one-way data flow | Use callback to notify parent |
| Using state where props suffice  | Makes component harder to reuse    | Keep it stateless if possible |
| Not using state for dynamic data | UI won't update                    | Use useState or useReducer    |

### 8. Prop Drilling vs Lifting State

- Prop Drilling: Passing props through many layers of components.
- Lifting State Up: Moving state to a common ancestor to share between components.

Example:

```
function App() {
  const [value, setValue] = useState('');

  return (
    <div>
      <Input value={value} onChange={setValue} />
      <Display value={value} />
    </div>
  );
}

function Input({ value, onChange }) {
  return <input value={value} onChange={e => onChange(e.target.value)} />;
}

function Display({ value }) {
  return <p>You typed: {value}</p>;
}
```

- **State is lifted** to App
- **Props are passed down** to children
