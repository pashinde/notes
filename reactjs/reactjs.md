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
