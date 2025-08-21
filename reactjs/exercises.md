# Exercises:

## Section A: Exercises for Javascript Basics

1. Declare variables for your name, age, and hobbies (array).
2. Write a function that greets you with your name.
3. Create an object representing a user with name and age.
4. Use destructuring to get the name and age.
5. Use the spread operator to add a new hobby to hobbies.
6. Write a function that sums any number of arguments.
7. Use map to create an array of greetings for each hobby.
8. Use a ternary to display if you are an adult.

## Section B: Modern JavaScript (ES6+) Features for React

1. Rewrite a normal function to an arrow function.
2. Use destructuring to extract deeply nested properties from an object.
3. Combine two arrays using spread operator.
4. Create a class for a Car with methods for start and stop.
5. Write a simple module to export a function and import it in another file.
6. Create a promise that resolves after 2 seconds and use async/await to get its result.
7. Use optional chaining to safely access nested properties in an object.

## Section C: JavaScript Data Structures & Methods Crucial for React

Given an array of user objects:

```
const users = [
  { id: 1, name: 'Alice', age: 30 },
  { id: 2, name: 'Bob', age: 25 },
  { id: 3, name: 'Carol', age: 35 },
];
```

- Use map to create an array of user names.
- Use filter to get users older than 28.
- Use find to get the user with id 2.
- Use reduce to find the sum of all ages.

## Section D: JavaScript Asynchronous Programming for React

1. Create a Promise that resolves with your name after 2 seconds.
2. Convert a callback-based function to use Promises.
3. Use async/await to fetch data from an API and log the result.
4. Handle errors gracefully in your async function.
5. Use Promise.all to fetch two resources simultaneously and log both results.
6. Try to implement a React component that fetches and displays data with loading and error states.

## Section E: Closures, Scope & Higher-Order Functions in JavaScript (Vital for React)

1. Write a closure that maintains a private variable and exposes increment and get functions.
2. Write a higher-order function that takes a function and returns a new function logging the arguments before calling the original.
3. Use an array’s .map() method to transform an array of numbers into their squares.
4. Explain what happens with closures in the React useEffect hook with a dependency array.
5. Write a React function component demonstrating a closure in an event handler.

## Section F: Event Handling & Synthetic Events in React

1. Create a button that alerts a custom message on click.
2. Create an input that logs its value on every change.
3. Create a form that prevents the default submit and logs form data.
4. Create a list of buttons dynamically and handle clicks for each button with its index.
5. Use arrow functions to avoid explicit .bind() in a class component event handler.
