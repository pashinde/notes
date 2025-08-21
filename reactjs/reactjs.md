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
