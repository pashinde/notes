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

# Section J: All About React Hooks

React Hooks let you use state and lifecycle features in functional components — no need for class components anymore!

## 📌 What Are Hooks?

Hooks are special functions that:

- Let you “hook into” React features like state and lifecycle
- Only work in functional components
- Start with the word "use"

### 1. useState – Add state to a functional component

```
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // [value, setter]

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>+1</button>
    </div>
  );
}
```

✔️ Used for local, reactive state.

### 2. useEffect – Side effects (data fetching, subscriptions, etc.)

```
import React, { useEffect, useState } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(setData);
  }, []); // [] means run only once (on mount)

  return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
}
```

✔️ Runs after render

✔️ Include dependencies in the array to control re-running

✔️ Use it for:

- Fetching data
- Setting timers
- Subscribing to events

### 3. useRef – Hold mutable value across renders OR access DOM

Example 1: Store a timer ID

```
const timerRef = useRef(null);
```

Example 2: Focus input on mount

```
function InputFocus() {
  const inputRef = useRef();

  useEffect(() => {
    inputRef.current.focus();
  }, []);

  return <input ref={inputRef} />;
}
```

✔️ Does not cause re-render

✔️ Can be used like instance variables or DOM refs

## ✨ Less Common but Powerful Hooks

### 4. useContext – Consume context values

```
const ThemeContext = React.createContext();

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemedComponent />
    </ThemeContext.Provider>
  );
}

function ThemedComponent() {
  const theme = useContext(ThemeContext);
  return <p>Current theme: {theme}</p>;
}
```

✔️ Avoids prop drilling

✔️ Works with React Context API

### 5. useReducer – Alternative to useState for complex logic

```
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <button onClick={() => dispatch({ type: 'increment' })}>
      Count: {state.count}
    </button>
  );
}
```

✔️ Use for:

- Complex state logic
- Multiple related state variables
- Redux-like architecture

### 6. useMemo – Memoize a calculated value

```
const expensiveValue = useMemo(() => {
  return computeHeavyStuff(input);
}, [input]);
```

✔️ Avoids recalculating expensive values unnecessarily

### 7. useCallback – Memoize a function

```
const handleClick = useCallback(() => {
  doSomething();
}, []);
```

✔️ Prevents re-creating functions every render

✔️ Great for optimizing child components

### 8. useLayoutEffect – Like useEffect, but fires before painting to screen

Used for measurements or DOM manipulation:

```
useLayoutEffect(() => {
  // Read DOM, do layout logic here
}, []);
```

✔️ Runs synchronously after render, before paint

❗ Use only when necessary (can block UI)

### 9. useImperativeHandle – Customize what a ref exposes (used with forwardRef)

```
useImperativeHandle(ref, () => ({
  focus: () => {
    inputRef.current.focus();
  },
}));
```

✔️ For library authors or advanced scenarios

### 10. useDebugValue – Show custom label in React DevTools

```
useDebugValue(user ? 'Logged In' : 'Logged Out');
```

✔️ Dev-only hook for debugging

### Hooks Usage Rules (Don’t Break These!)

1. Only call Hooks **at the top level** of your component (no conditionals or loops).
2. Only call Hooks from **React functions** (components or custom hooks).

### 11. Hooks Best Practices

| Best Practice                                                 | Why                                             |
| :------------------------------------------------------------ | :---------------------------------------------- |
| Use useEffect with proper dependency array                    | Prevents bugs from stale data or infinite loops |
| Use useRef for non-stateful mutable values                    | Avoids unnecessary re-renders                   |
| Split state into multiple useState calls if unrelated         | Keeps code clean                                |
| Use useReducer when state logic is complex                    | Better organization                             |
| Memoize expensive values/functions with useMemo / useCallback | Improves performance                            |

# Section K: Deep Dive into Custom Hooks in React

### 1. What are Custom Hooks?

- Custom hooks are JavaScript functions whose name starts with use.
- They let you extract and reuse stateful logic across multiple components.
- They can call other hooks inside them.
- They follow the same rules of hooks (top-level calls, etc.).

### 2. Why Use Custom Hooks?

- Avoid code duplication when multiple components share logic.
- Make components cleaner by moving logic outside JSX.
- Enhance readability and maintainability.
- Encapsulate complex behavior into reusable functions.

### 3. How to Create a Custom Hook?

1. The function name must start with use.
2. Inside, use built-in hooks like useState, useEffect, etc.
3. Return values or functions needed by the component.

### Example 1: useWindowWidth — Track Window Width

```
import { useState, useEffect } from 'react';

function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    function handleResize() {
      setWidth(window.innerWidth);
    }

    window.addEventListener('resize', handleResize);

    // Cleanup listener on unmount
    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return width;
}

// Usage in a component:
function ShowWidth() {
  const width = useWindowWidth();

  return <div>Window width: {width}px</div>;
}
```

### Example 2: useFetch — Data Fetching Hook

```
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    setLoading(true);
    fetch(url)
      .then(res => {
        if (!res.ok) throw new Error('Network error');
        return res.json();
      })
      .then(json => {
        setData(json);
        setError(null);
      })
      .catch(err => setError(err.message))
      .finally(() => setLoading(false));
  }, [url]);

  return { data, loading, error };
}

// Usage:
function DataDisplay() {
  const { data, loading, error } = useFetch('https://api.example.com/data');

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}
```

### How to Think About Custom Hooks

- They are not components — do not return JSX.
- They return values or functions that components can use.
- They enable sharing logic, not UI.

### Custom Hook Best Practices

| Best Practice                                 | Why                                |
| :-------------------------------------------- | :--------------------------------- |
| Name your hooks starting with use             | To follow React’s conventions      |
| Keep hooks focused on a single responsibility | Easier to maintain and reuse       |
| Return only what components need              | Avoid exposing unnecessary details |
| Use other hooks inside your custom hooks      | Compose functionality cleanly      |
| Avoid side effects outside useEffect          | Maintain predictable behavior      |

# Section L: Advanced React Hooks Topics

## Part 1: useReducer Patterns

### 1. What is useReducer?

- An alternative to useState for complex state logic.
- Inspired by Redux’s reducer concept.
- Helps manage multiple related state variables or state w
  ith complex transitions.
- Accepts a reducer function and initial state.
- Returns [state, dispatch].

### 2. Basic Example of useReducer

```
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return initialState;
    default:
      throw new Error('Unknown action');
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Reset</button>
    </>
  );
}
```

### 3. When to Use useReducer Over useState?

- When state logic is complex or involves multiple sub-values.
- When next state depends on previous state.
- When you want to centralize state transitions.
- When using action-based state updates is clearer.

### 4. Advanced useReducer Pattern: Using Payloads

```
function reducer(state, action) {
  switch (action.type) {
    case 'add':
      return { todos: [...state.todos, action.payload] };
    case 'toggle':
      return {
        todos: state.todos.map(todo =>
          todo.id === action.payload ? { ...todo, completed: !todo.completed } : todo
        ),
      };
    default:
      return state;
  }
}
```

You dispatch actions with:

```
dispatch({ type: 'add', payload: { id: 3, text: 'Learn useReducer', completed: false } });
```

### 5. Side Note: useReducer with useContext

You can combine useReducer with React Context to manage global app state.

## Part 2: Context API + Hooks (useContext)

### 1. What is React Context?

- A way to pass data through the component tree without props drilling.
- Useful for global data like theme, authentication, user info.

### 2. How to Use Context with Hooks

#### Step 1: Create a Context

```
import React, { createContext } from 'react';

const ThemeContext = createContext('light'); // default value
```

#### Step 2: Provide Context Value

```
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```

#### Step 3: Consume Context with useContext

```
import React, { useContext } from 'react';

function Toolbar() {
  const theme = useContext(ThemeContext);

  return <div style={{ background: theme === 'dark' ? '#333' : '#ccc' }}>Toolbar</div>;
}
```

### 3. Example: Theme Toggle with Context + Hooks

```
import React, { useState, createContext, useContext } from 'react';

const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');

  function toggleTheme() {
    setTheme(theme === 'light' ? 'dark' : 'light');
  }

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function Toolbar() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div style={{ background: theme === 'dark' ? '#333' : '#eee', padding: 20 }}>
      <p>Current theme: {theme}</p>
      <button onClick={toggleTheme}>Toggle</button>
    </div>
  );
}

function App() {
  return (
    <ThemeProvider>
      <Toolbar />
    </ThemeProvider>
  );
}
```

### 4. Benefits of Using Context with Hooks

- Easy to share state across deeply nested components.
- No need for prop drilling.
- Combine well with useReducer for managing global complex state.

# Section M: React Router with Hooks, React Query, and State Management Libraries

## React Router with Hooks

### 1. What is React Router?

- The standard library for routing in React apps.
- Helps build Single Page Applications (SPA) with navigation between views.
- Manages URL changes and renders components accordingly.

### 2. React Router Hooks Overview

- useNavigate() – programmatic navigation.
- useParams() – access URL parameters.
- useLocation() – access current URL info.
- useMatch() – check if current URL matches a pattern.

### 3. Example: Simple Router Setup with Hooks

```
import { BrowserRouter, Routes, Route, Link, useParams, useNavigate } from 'react-router-dom';

function Home() {
  const navigate = useNavigate();
  return (
    <div>
      <h2>Home</h2>
      <button onClick={() => navigate('/profile/42')}>Go to Profile 42</button>
    </div>
  );
}

function Profile() {
  const { userId } = useParams();
  return <h2>Profile of User {userId}</h2>;
}

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/profile/1">Profile 1</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/profile/:userId" element={<Profile />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### 4. Why Use React Router Hooks?

- Cleaner, simpler code than older HOCs or render props.
- More intuitive API inside functional components.
- Direct access to navigation & route params.

## React Query (now called TanStack Query)

### 1. What is React Query?

- A library to fetch, cache, and update asynchronous data in React apps.
- Simplifies server state management.
- Provides features like:
  - Caching
  - Refetching
  - Background updates
  - Pagination support
  - Request cancellation

### 2. Basic Example of React Query

```
import { useQuery } from '@tanstack/react-query';

function fetchUser(userId) {
  return fetch(`https://api.example.com/users/${userId}`).then(res => res.json());
}

function User({ userId }) {
  const { data, error, isLoading } = useQuery(['user', userId], () => fetchUser(userId));

  if (isLoading) return <p>Loading...</p>;
  if (error) return <p>Error loading user</p>;

  return <div>{data.name}</div>;
}
```

### 3. Why Use React Query?

- Less boilerplate code compared to manual useEffect data fetching.
- Automatically manages cache and updates UI.
- Supports polling, pagination, optimistic updates.

## State Management Libraries

### 1. Why use external state management?

- React’s built-in state & context work well, but large apps may need:
  - Global shared state
  - Predictable state transitions
  - Better debugging tools

### 2. Popular State Libraries

| Library       | Description                     | Use Case                             |
| :------------ | :------------------------------ | :----------------------------------- |
| Redux         | Predictable state container     | Large apps, complex state logic      |
| Redux Toolkit | Simplifies Redux boilerplate    | Modern Redux with better DX          |
| Recoil        | React-centric state management  | Fine-grained state with minimal code |
| Zustand       | Small, fast, and scalable state | Lightweight global state             |
| MobX          | Observable state and reactions  | Reactive state with simple setup     |

### 3. Example: Redux Toolkit Slice

```
// counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment(state) {
      state.value++;
    },
    decrement(state) {
      state.value--;
    }
  }
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;

// Counter.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from './counterSlice';

function Counter() {
  const count = useSelector(state => state.counter.value);
  const dispatch = useDispatch();

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={() => dispatch(increment())}>+</button>
      <button onClick={() => dispatch(decrement())}>-</button>
    </>
  );
}
```

# Section N: React Router (with Hooks)

### 1. React Router Basics

React Router helps build SPAs by mapping URL paths to React components, allowing navigation without full page reloads.

### 2. Key Components & Hooks

| Item             | Description                                 |
| :--------------- | :------------------------------------------ |
| \<BrowserRouter> | Wraps your app, enables history API routing |
| \<Routes>        | Container for all \<Route> elements         |
| \<Route>         | Defines a path and component mapping        |
| \<Link>          | Declarative navigation (like \<a>)          |
| useNavigate()    | Hook for programmatic navigation            |
| useParams()      | Hook to access dynamic URL params           |
| useLocation()    | Hook to get current URL/location object     |
| useMatch()       | Check if current path matches a pattern     |

### 3. Example Setup

```
import { BrowserRouter, Routes, Route, Link, useParams, useNavigate } from 'react-router-dom';

function Home() {
  const navigate = useNavigate();
  return (
    <div>
      <h1>Home Page</h1>
      <button onClick={() => navigate('/profile/123')}>Go to Profile 123</button>
    </div>
  );
}

function Profile() {
  const { userId } = useParams();
  return <h1>Profile Page for User {userId}</h1>;
}

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/profile/123">Profile 123</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/profile/:userId" element={<Profile />} />
      </Routes>
    </BrowserRouter>
  );
}
```

- useNavigate() lets you navigate programmatically (e.g., after a form submission).
- useParams() extracts dynamic segments from the URL.
- Use \<Link> instead of \<a> to avoid full reloads.
- \<Routes> replaces the older \<Switch> component for route matching.

### 4. Nested Routes & Layouts

You can nest routes and render layouts for shared UI parts:

```
function DashboardLayout() {
  return (
    <div>
      <h2>Dashboard</h2>
      <Outlet /> {/* renders nested routes */}
    </div>
  );
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="dashboard" element={<DashboardLayout />}>
          <Route index element={<DashboardHome />} />
          <Route path="settings" element={<Settings />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}
```

# Section O: React Query (TanStack Query)

### 1. What is React Query?

A library to manage **server state** like fetching, caching, syncing, and updating remote data in React apps.

### 2. Why React Query?

- Handles caching & background updates automatically.
- Reduces boilerplate around fetch & state.
- Provides **status tracking** (loading, error).
- Supports **pagination, refetching, mutations,** and more.

### 3. Basic Usage

```
import { useQuery } from '@tanstack/react-query';

function fetchTodos() {
  return fetch('https://jsonplaceholder.typicode.com/todos').then(res => res.json());
}

function TodoList() {
  const { data, error, isLoading } = useQuery(['todos'], fetchTodos);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error loading todos</div>;

  return (
    <ul>
      {data.slice(0, 10).map(todo => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
}
```

### 4. Mutations (POST/PUT/DELETE)

```
import { useMutation, useQueryClient } from '@tanstack/react-query';

function addTodo(newTodo) {
  return fetch('https://jsonplaceholder.typicode.com/todos', {
    method: 'POST',
    body: JSON.stringify(newTodo),
    headers: { 'Content-Type': 'application/json' }
  }).then(res => res.json());
}

function AddTodo() {
  const queryClient = useQueryClient();
  const mutation = useMutation(addTodo, {
    onSuccess: () => queryClient.invalidateQueries(['todos'])
  });

  const handleAdd = () => mutation.mutate({ title: 'New Task', completed: false });

  return <button onClick={handleAdd}>Add Todo</button>;
}
```

### 5. Key Concepts

| Concept        | Description                        |
| :------------- | :--------------------------------- |
| useQuery       | Fetch and cache data               |
| useMutation    | Create/update/delete data          |
| useQueryClient | Access cache & trigger refetches   |
| Query Keys     | Unique identifiers for cached data |

# Section P: Redux Toolkit

### 1. What is Redux Toolkit?

- Official, recommended way to write Redux logic.
- Simplifies Redux setup and reduces boilerplate.
- Provides utilities like createSlice, createAsyncThunk.

### 2. Setup

```
npm install @reduxjs/toolkit react-redux
```

### 3. Example: Counter Slice

```
// counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const initialState = { value: 0 };

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment(state) {
      state.value++;
    },
    decrement(state) {
      state.value--;
    }
  }
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

#### Using in React

```
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from './counterSlice';

function Counter() {
  const count = useSelector(state => state.counter.value);
  const dispatch = useDispatch();

  return (
    <>
      <h1>Count: {count}</h1>
      <button onClick={() => dispatch(increment())}>+</button>
      <button onClick={() => dispatch(decrement())}>-</button>
    </>
  );
}
```

#### Store Setup

```
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

const store = configureStore({
  reducer: { counter: counterReducer }
});

export default store;
```

Wrap your app with _\<Provider store={store}>_ from react-redux.

#### Async with createAsyncThunk

```
import { createAsyncThunk, createSlice } from '@reduxjs/toolkit';

export const fetchUser = createAsyncThunk('user/fetchUser', async (userId) => {
  const response = await fetch(`https://api.example.com/user/${userId}`);
  return response.json();
});

const userSlice = createSlice({
  name: 'user',
  initialState: { data: null, status: 'idle', error: null },
  extraReducers: builder => {
    builder
      .addCase(fetchUser.pending, state => { state.status = 'loading'; })
      .addCase(fetchUser.fulfilled, (state, action) => {
        state.status = 'succeeded';
        state.data = action.payload;
      })
      .addCase(fetchUser.rejected, (state, action) => {
        state.status = 'failed';
        state.error = action.error.message;
      });
  }
});
```

# Section Q: React Hook Form

### 1. What is React Hook Form?

- Library to handle forms in React with minimal re-rendering.
- Works well with React Hooks and integrates with validation libraries.
- Provides register, handleSubmit, errors, etc.

### 2. Basic Usage

```
import { useForm } from 'react-hook-form';

function LoginForm() {
  const { register, handleSubmit, formState: { errors } } = useForm();

  const onSubmit = data => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register('username', { required: 'Username is required' })} />
      {errors.username && <p>{errors.username.message}</p>}

      <input type="password" {...register('password', { minLength: 6 })} />
      {errors.password && <p>Password must be at least 6 characters</p>}

      <button type="submit">Login</button>
    </form>
  );
}
```

### 3. Features

- Built-in validation support.
- Minimal re-renders for performance.
- Easy integration with UI libraries.
- Supports controlled and uncontrolled components.

# Section R: Zustand

### 1. What is Zustand?

- Small, fast state management library.
- Minimal API, simple to learn.
- Uses hooks for global state

### 2. Basic Example

```
import create from 'zustand';

const useStore = create(set => ({
  count: 0,
  increment: () => set(state => ({ count: state.count + 1 })),
  decrement: () => set(state => ({ count: state.count - 1 }))
}));

function Counter() {
  const { count, increment, decrement } = useStore();

  return (
    <>
      <h1>{count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </>
  );
}
```

### 3. Why Zustand?

- Simple API, no boilerplate.
- Supports middleware, persistence.
- Selective re-rendering with selectors.
- Works great for medium apps or as a companion to other libs.

# Section S: Debugging React Applications: Tools, Techniques & Best Practices

## 1. Essential Tools for Debugging React

### 1. React Developer Tools (Browser Extension)

- Official browser extension for Chrome and Firefox.
- Lets you inspect the React component tree.
- View props, state, context, and hooks.
- Profile renders to detect performance bottlenecks.
- Highlight components that re-render too often.

#### How to use:

- Install from Chrome Web Store / Firefox Add-ons.
- Open DevTools > React tab.
- Select any component to inspect current props/state.
- Use Profiler tab to record render times and identify slow components.

### 2. Browser DevTools (Console, Network, Sources)

- Console: Check errors, warnings, and logs (console.log, console.error).
- Sources: Set breakpoints, step through code.
- Network: Inspect API calls, status, response data.
- Performance: Record UI thread and scripting for slow interactions.

### 3. Debugging in IDE (VSCode)

- Use Chrome Debugger extension or VSCode’s built-in JS debugger.
- Set breakpoints in .jsx files, step through React code.
- Inspect variables, call stacks, and component prop-

## 2. Common Debugging Techniques

### 1. Use Console Logging Wisely

- console.log() is simplest, but too many logs clutter output.
- Use console.table() for arrays/objects.
- console.error() and console.warn() highlight issues.
- Clean up logs after debugging.

Example:

```
console.log('Current user:', user);
```

### 2. Use React Developer Tools to Inspect Component State

- Inspect prop values passed to components.
- Check local state with hooks.
- Validate if expected values exist or not.

### 3. Breakpoints & Step Debugging

- Pause code execution at certain lines.
- Step over/into functions to see flow.
- Inspect call stack to trace origin of errors.

### 4. Error Boundaries for React Runtime Errors

- React 16+ supports error boundaries to catch JS errors in components.
- Use to display fallback UI instead of breaking the app.

Example:

```
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }
  componentDidCatch(error, errorInfo) {
    console.error("Error caught:", error, errorInfo);
  }
  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```

### 5. Use PropTypes or TypeScript for Type Checking

- Catch bugs caused by wrong props passed.
- PropTypes: runtime validation.
- TypeScript: static type checks during development.

### 6. Debugging Hooks

- Verify hook usage rules (e.g., don’t call hooks conditionally).
- Use React DevTools to inspect hook states.
- Use custom debug hooks if needed to log hook values.

### 7. Network/API Debugging

- Check API responses in DevTools Network tab.
- Use tools like Postman or Insomnia for API testing.
- Handle fetch errors and loading states in U-

### 8. Profiling for Performance Issues

- Use React Profiler to find unnecessary renders.
- Optimize with memoization (React.memo, useMemo, useCallback).
- Lazy load components and code split.

## 3. Best Practices for React Debugging

| Best Practice                    | Explanation                                          |
| :------------------------------- | :--------------------------------------------------- |
| Write clean, readable code       | Easier to debug and maintain.                        |
| Use meaningful component names   | Helps identify components in React DevTools.         |
| Use error boundaries             | Prevent UI crashes and show fallback UI.             |
| Use source maps in production    | Get readable stack traces in production errors.      |
| Log errors to monitoring service | Sentry, LogRocket for real-time error tracking.      |
| Test components independently    | Use Storybook or unit tests to isolate bugs.         |
| Avoid inline anonymous functions | Improves React DevTools readability and performance. |

## 4. Example Debugging Workflow

Scenario: A button click does not update UI state

1. Open React DevTools and select the component with the button.
2. Check if the component state updates after the button click.
3. Add a console.log inside the click handler to confirm it fires.
4. Set a breakpoint in VSCode on the click handler.
5. Step through handler to see if setState or useState setter is called.
6. Confirm props/state flow from parent component.
7. If state updates but UI doesn’t, check render logic or conditional rendering.

## 5. Useful Debugging Tips & Tricks

- Use debugger; statement in your code to programmatically trigger breakpoints.
- Use React.StrictMode to identify unsafe lifecycles and side effects.
- Wrap async functions with try/catch and log errors explicitly.
- Keep an eye on warnings React gives — often they point to bugs.
- Use console.trace() to see the call stack for a log.
- Test on multiple browsers and devices.

## 6. Tools & Libraries to Enhance Debugging

- Sentry — Real-time error tracking in production.
- LogRocket — Session replay for frontend bugs.
- why-did-you-render — Detect unnecessary React renders.
- React Profiler API — Programmatic profiling for deeper insights.

### Summary Checklist

| Step                    | Tool / Technique             |
| :---------------------- | :--------------------------- |
| Inspect component state | React Developer Tools        |
| Track network requests  | Browser DevTools Network Tab |
| Debug JS flow           | Console.log, Breakpoints     |
| Catch UI errors         | Error Boundaries             |
| Check performance       | React Profiler               |
| Type safety             | PropTypes / TypeScript       |

# Section T: Testing React Applications: Unit Tests & End-to-End Tests

## 1. Testing Types Overview

| Test Type              | What it Tests                                      | Scope Tools Commonly Used                                           |
| :--------------------- | :------------------------------------------------- | :------------------------------------------------------------------ |
| Unit Tests             | Individual components, functions                   | Smallest parts in isolation Jest, React Testing Library             |
| Integration Tests      | Interaction between multiple components or modules | Combined parts working together Jest + React Testing Library        |
| End-to-End (E2E) Tests | Full app flow in browser, simulating user behavior | Whole app running in real environment Cypress, Playwright, Selenium |

## 2. Popular Testing Tools for React

### Unit & Integration Testing

- **Jest**

  - Facebook’s testing framework, default in Create React App.
  - Runs tests, mocks dependencies, provides coverage reports.

- **React Testing Library (RTL)**
  - Focuses on testing UI from user perspective (queries by text, role).
  - Encourages good testing practices rather than testing implementation details.

### End-to-End Testing

- **Cypress**
  - Modern, easy-to-use E2E testing framework.
  - Runs tests in real browsers with excellent debugging tools.
- **Playwright**
  - Cross-browser E2E testing by Microsoft.
- **Selenium**
  - Older, widely-used E2E framework (more complex to set up).

## 3. Setting up Unit Tests with Jest & React Testing Library

### Installation

If you’re using Create React App, Jest and RTL come pre-installed.
For other setups:

```
npm install --save-dev jest @testing-library/react @testing-library/jest-dom
```

### Writing Your First Unit Test

Say we have a simple button component:

```
// Button.js
export default function Button({ onClick, children }) {
  return <button onClick={onClick}>{children}</button>;
}
```

Test file: Button.test.js

```
import { render, screen, fireEvent } from '@testing-library/react';
import Button from './Button';

test('renders button and handles click', () => {
  const handleClick = jest.fn(); // mock function

  render(<Button onClick={handleClick}>Click Me</Button>);

  const button = screen.getByText(/click me/i);
  expect(button).toBeInTheDocument();

  fireEvent.click(button);

  expect(handleClick).toHaveBeenCalledTimes(1);
});
```

#### Explanation

- render() mounts the component in a virtual DOM.
- screen queries DOM elements similar to user perspective (by text, role, label).
- fireEvent.click() simulates user clicking.
- jest.fn() mocks a function to track calls.

### Testing Props & Conditional Rendering

Suppose a component that renders different text based on prop:

```
function Greeting({ isLoggedIn }) {
  return <h1>{isLoggedIn ? 'Welcome back!' : 'Please sign in.'}</h1>;
}
```

Test:

```
test('renders welcome message when logged in', () => {
  render(<Greeting isLoggedIn={true} />);
  expect(screen.getByText(/welcome back/i)).toBeInTheDocument();
});

test('renders sign-in prompt when not logged in', () => {
  render(<Greeting isLoggedIn={false} />);
  expect(screen.getByText(/please sign in/i)).toBeInTheDocument();
});
```

## 4. Writing More Complex Tests

#### Testing Async Behavior (API calls)

Use waitFor or findBy queries for async UI updates.

```
import { render, screen, waitFor } from '@testing-library/react';
import userEvent from '@testing-library/user-event';

test('loads and displays user data', async () => {
  render(<UserProfile userId={1} />);

  // Initially show loading
  expect(screen.getByText(/loading/i)).toBeInTheDocument();

  // Wait for user name to appear after fetch
  const userName = await screen.findByText(/john doe/i);
  expect(userName).toBeInTheDocument();
});
```

#### Snapshot Testing

Capture UI output and track changes over time.

```
import renderer from 'react-test-renderer';

test('button renders correctly', () => {
  const tree = renderer.create(<Button>Click</Button>).toJSON();
  expect(tree).toMatchSnapshot();
});
```

## 5. End-to-End (E2E) Testing with Cypress

#### Setup Cypress

```
npm install --save-dev cypress
```

#### Add script in package.json:

```
"scripts": {
  "cypress:open": "cypress open"
}
```

#### Run tests:

```
npm run cypress:open
```

#### Writing a Basic E2E Test

```
// cypress/integration/login.spec.js
describe('Login Flow', () => {
  it('allows user to login', () => {
    cy.visit('/login');
    cy.get('input[name=username]').type('user1');
    cy.get('input[name=password]').type('password');
    cy.get('button[type=submit]').click();
    cy.url().should('include', '/dashboard');
    cy.contains('Welcome, user1');
  });
});
```

#### Explanation

- cy.visit() opens a page.
- cy.get() finds DOM elements.
- .type() simulates typing.
- .click() simulates clicking.
- .should() asserts conditions (URL, content, etc.).

## 6. Best Practices for Testing React Apps

| Best Practice                     | Explanation                                                    |
| :-------------------------------- | :------------------------------------------------------------- |
| Test behavior, not implementation | Use React Testing Library queries to simulate user experience. |
| Write small, focused tests        | Each test should check one thing only.                         |
| Use mocks and spies wisely        | Avoid over-mocking to keep tests realistic.                    |
| Keep tests fast and deterministic | Avoid flakiness with controlled mocks and timers.              |
| Test edge cases and error states  | Cover unexpected input or failures.                            |
| Use snapshots sparingly           | For stable UI components only, not frequently changing ones.   |
| Combine unit & E2E testing        | Unit tests for logic, E2E for user flows.                      |
| Integrate tests into CI/CD        | Run tests automatically on commits/pull requests.              |

## 6. Summary Workflow for React Testing

1. Write unit tests for components and logic with Jest + RTL.
2. Mock API calls using jest.mock() or libraries like msw (Mock Service Worker).
3. Run tests locally and on CI.
4. Write E2E tests with Cypress for critical user journeys.
5. Use code coverage reports to find untested code.
6. Refactor and keep tests updated as app evolves.

#### Useful Libraries for React Testing

| Library                     | Purpose                                   |
| :-------------------------- | :---------------------------------------- |
| @testing-library/react      | Render and interact with React components |
| @testing-library/user-event | More realistic user interactions          |
| jest                        | Test runner & assertion framework         |
| msw                         | Mock Service Worker for API mocking       |
| cypress                     | E2E testing framework                     |
| react-test-renderer         | Snapshot testing                          |

## 7. Walkthrough: Building Unit & E2E Tests for a Sample React App

### Sample App: Todo List

We'll create a small Todo List app where users can:

- Add todos
- Mark todos as completed
- See a list of todos

### Step 1: Set Up the React App

If you don’t have a React app yet, create one using Create React App (CRA):

```
npx create-react-app todo-app
cd todo-app
```

### Step 2: Build a Simple Todo Component

Create a file src/TodoApp.js with this basic component:

```
import React, { useState } from 'react';

export default function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [inputValue, setInputValue] = useState('');

  const addTodo = () => {
    if (inputValue.trim() === '') return;
    setTodos([...todos, { text: inputValue, completed: false }]);
    setInputValue('');
  };

  const toggleComplete = (index) => {
    const newTodos = [...todos];
    newTodos[index].completed = !newTodos[index].completed;
    setTodos(newTodos);
  };

  return (
    <div>
      <h1>Todo List</h1>
      <input
        placeholder="Enter todo"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
        aria-label="todo-input"
      />
      <button onClick={addTodo}>Add Todo</button>
      <ul>
        {todos.map((todo, i) => (
          <li
            key={i}
            onClick={() => toggleComplete(i)}
            style={{ textDecoration: todo.completed ? 'line-through' : 'none', cursor: 'pointer' }}
            aria-label={`todo-item-${i}`}
          >
            {todo.text}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

Modify src/App.js to render this:

```
import React from 'react';
import TodoApp from './TodoApp';

function App() {
  return <TodoApp />;
}

export default App;
```

Run the app with npm start to check it works.

### Step 3: Write Unit Tests with Jest & React Testing Library

#### 3.1 Install Testing Dependencies (if needed)

If you used CRA, Jest & RTL are pre-installed. Otherwise:

```
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

#### 3.2 Create src/TodoApp.test.js

```
import { render, screen, fireEvent } from '@testing-library/react';
import TodoApp from './TodoApp';

describe('TodoApp component', () => {
  test('renders input, button and empty todo list', () => {
    render(<TodoApp />);

    expect(screen.getByRole('textbox', { name: /todo-input/i })).toBeInTheDocument();
    expect(screen.getByRole('button', { name: /add todo/i })).toBeInTheDocument();
    expect(screen.queryAllByRole('listitem')).toHaveLength(0);
  });

  test('adds a todo to the list when Add Todo button clicked', () => {
    render(<TodoApp />);

    const input = screen.getByRole('textbox', { name: /todo-input/i });
    const button = screen.getByRole('button', { name: /add todo/i });

    fireEvent.change(input, { target: { value: 'Write tests' } });
    fireEvent.click(button);

    expect(screen.getByText('Write tests')).toBeInTheDocument();
    expect(screen.getAllByRole('listitem')).toHaveLength(1);
  });

  test('toggles todo completion on click', () => {
    render(<TodoApp />);

    const input = screen.getByRole('textbox', { name: /todo-input/i });
    const button = screen.getByRole('button', { name: /add todo/i });

    fireEvent.change(input, { target: { value: 'Write tests' } });
    fireEvent.click(button);

    const todoItem = screen.getByText('Write tests');

    // Initially not completed (no line-through)
    expect(todoItem).toHaveStyle('text-decoration: none');

    // Click toggles completion
    fireEvent.click(todoItem);
    expect(todoItem).toHaveStyle('text-decoration: line-through');

    // Click again toggles back
    fireEvent.click(todoItem);
    expect(todoItem).toHaveStyle('text-decoration: none');
  });

  test('does not add empty todos', () => {
    render(<TodoApp />);

    const button = screen.getByRole('button', { name: /add todo/i });

    fireEvent.click(button);

    expect(screen.queryAllByRole('listitem')).toHaveLength(0);
  });
});
```

#### 3.3 Run Unit Tests

```
npm test
```

- Jest will pick up .test.js files and run the tests.
- You should see all tests passing!

### Step 4: Write End-to-End (E2E) Tests with Cypress

#### 4.1 Install Cypress

```
npm install --save-dev cypress
```

Add this to your package.json scripts:

```
"scripts": {
  "cypress:open": "cypress open"
}
```

#### 4.2 Initialize Cypress

```
npm run cypress:open
```

This opens the Cypress test runner for the first time and creates a default folder structure: cypress/.

#### 4.3 Create E2E Test: cypress/e2e/todo.spec.js

```
describe('Todo App E2E Tests', () => {
  beforeEach(() => {
    cy.visit('http://localhost:3000'); // Adjust if your dev server is on different port
  });

  it('should load the todo app', () => {
    cy.contains('Todo List');
    cy.get('input[aria-label="todo-input"]').should('exist');
    cy.get('button').contains('Add Todo').should('exist');
  });

  it('should add a new todo', () => {
    cy.get('input[aria-label="todo-input"]').type('Learn Cypress');
    cy.get('button').contains('Add Todo').click();
    cy.get('li').should('have.length', 1).and('contain.text', 'Learn Cypress');
  });

  it('should toggle todo completion on click', () => {
    cy.get('input[aria-label="todo-input"]').type('Test completion');
    cy.get('button').contains('Add Todo').click();

    cy.get('li').contains('Test completion').as('todoItem');

    // Check initial state (no line-through)
    cy.get('@todoItem').should('have.css', 'text-decoration').and('not.contain', 'line-through');

    // Click to toggle complete
    cy.get('@todoItem').click();
    cy.get('@todoItem').should('have.css', 'text-decoration').and('contain', 'line-through');

    // Click to toggle back
    cy.get('@todoItem').click();
    cy.get('@todoItem').should('have.css', 'text-decoration').and('not.contain', 'line-through');
  });

  it('should not add empty todos', () => {
    cy.get('button').contains('Add Todo').click();
    cy.get('li').should('have.length', 0);
  });
});
```

#### 4.4 Run Cypress Tests

- Make sure your React app is running (npm start).
- Run Cypress test runner:

```
npm run cypress:open
```

- Click the test file in Cypress UI to run tests in browser.
- Watch tests run interactively and check results.

## 8. Deep Dive: Mocking APIs in React Testing

### 1. Why Mock APIs?

When your React app fetches data from an API (e.g., using fetch or axios), in tests you don’t want to:

- Depend on real network calls (can be slow, flaky, or unstable).
- Rely on backend being up or data state.

Mocking lets you replace the real network call with a fake one that returns controlled data.

### 2. Common Mocking Strategies

| Approach                                      | Description                                                                 | When to Use                               |
| :-------------------------------------------- | :-------------------------------------------------------------------------- | :---------------------------------------- |
| **Jest manual mocks**                         | Mock fetch or axios directly in tests using Jest mocks.                     | Simple, for small test cases.             |
| **MSW (Mock Service Worker)**                 | Intercepts network calls at network level, works in both tests and browser. | More realistic and scalable.              |
| **Mock libraries (e.g., axios-mock-adapter)** | Mock axios requests specifically.                                           | When axios is used heavily.               |
| **Mock functions / dependency injection**     | Pass mock functions as props or context to simulate API responses.          | For components accepting fetch functions. |

### 3. Mocking with Jest: Example Using fetch

#### Example: Component that fetches and displays user data

```
// UserProfile.js
import React, { useEffect, useState } from 'react';

export default function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
      .then((res) => {
        if (!res.ok) throw new Error('Network error');
        return res.json();
      })
      .then((data) => {
        setUser(data);
        setLoading(false);
      })
      .catch((err) => {
        setError(err.message);
        setLoading(false);
      });
  }, [userId]);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <div>
      <h2>{user.name}</h2>
      <p>{user.email}</p>
    </div>
  );
}
```

#### Writing a test with fetch mocked by Jest

```
import { render, screen, waitFor } from '@testing-library/react';
import UserProfile from './UserProfile';

beforeEach(() => {
  // Reset fetch mock before each test
  global.fetch = jest.fn();
});

afterEach(() => {
  jest.resetAllMocks();
});

test('displays user data after successful fetch', async () => {
  const mockUser = { name: 'John Doe', email: 'john@example.com' };

  // Mock fetch response
  global.fetch.mockResolvedValueOnce({
    ok: true,
    json: async () => mockUser,
  });

  render(<UserProfile userId={1} />);

  expect(screen.getByText(/loading/i)).toBeInTheDocument();

  // Wait for user name to appear
  const userName = await screen.findByText('John Doe');
  expect(userName).toBeInTheDocument();
  expect(screen.getByText('john@example.com')).toBeInTheDocument();
});

test('displays error message on fetch failure', async () => {
  global.fetch.mockResolvedValueOnce({
    ok: false,
  });

  render(<UserProfile userId={1} />);

  const errorMsg = await screen.findByText(/error/i);
  expect(errorMsg).toBeInTheDocument();
});
```

### 4. Mocking with MSW (Mock Service Worker)

#### Why MSW?

- Intercepts actual network requests at the network layer.
- Works seamlessly in both unit tests and development environment.
- Supports REST and GraphQL APIs.
- Easy to define request handlers and return mocked responses.

#### Installation

```
npm install msw --save-dev
```

#### Basic Setup

1. Create a file src/mocks/handlers.js with handlers:

```
import { rest } from 'msw';

export const handlers = [
  rest.get('https://jsonplaceholder.typicode.com/users/:userId', (req, res, ctx) => {
    const { userId } = req.params;

    return res(
      ctx.status(200),
      ctx.json({ id: userId, name: 'Jane Doe', email: 'jane@example.com' })
    );
  }),
];
```

2. Setup MSW server for testing src/mocks/server.js:

```
import { setupServer } from 'msw/node';
import { handlers } from './handlers';

export const server = setupServer(...handlers);
```

3. Initialize server in your test setup file src/setupTests.js (CRA picks this up automatically):

```
import { server } from './mocks/server.js';

// Start MSW before all tests
beforeAll(() => server.listen());

// Reset handlers after each test (so tests don't affect each other)
afterEach(() => server.resetHandlers());

// Clean up after tests are finished
afterAll(() => server.close());
```

#### Test example using MSW with UserProfile component

```
import { render, screen } from '@testing-library/react';
import UserProfile from './UserProfile';

test('loads and displays user data with MSW', async () => {
  render(<UserProfile userId={123} />);
  expect(screen.getByText(/loading/i)).toBeInTheDocument();

  const userName = await screen.findByText('Jane Doe');
  expect(userName).toBeInTheDocument();
  expect(screen.getByText('jane@example.com')).toBeInTheDocument();
});
```

### 5. When to Use Which?

| Approach           | Pros                                        | Cons                                   |
| :----------------- | :------------------------------------------ | :------------------------------------- |
| Jest fetch mocks   | Simple to set up, good for isolated tests   | Can become complex with many endpoints |
| MSW                | More realistic, reusable across dev & tests | Slightly more setup upfront            |
| axios-mock-adapter | Easy for axios users, mocks at axios level  | Only works with axios, not fetch       |

### 6. Bonus Tips

- For error states, simulate server errors with MSW:

```
server.use(
  rest.get('https://jsonplaceholder.typicode.com/users/:userId', (req, res, ctx) => {
    return res(ctx.status(500), ctx.json({ message: 'Internal Server Error' }));
  })
);
```

- For **delays**, add latency with ctx.delay(150) to simulate network delays.
- Combine **MSW** with **React Testing Library** for robust integration tests that behave like real app usage.
