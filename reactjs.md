# Javascript Basics for React

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
