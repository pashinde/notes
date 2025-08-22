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

## Section G: React Components & Props — The Heart of React

1. Create a functional component UserCard that takes name, age, and email as props and displays them.
2. Use destructuring to clean up props in your component.
3. Pass an array of user objects and map over it to render multiple UserCard components.
4. Set default props for your component.
5. Try to modify props inside a component and observe why it’s a bad idea.

## Section H: React State & Lifecycle — Making Components Interactive

1. Build a counter component that increments and decrements.
2. Build a todo list that adds and removes tasks using state.
3. Create a component that fetches data on mount using useEffect.
4. Explain what happens if you don’t provide the dependency array in useEffect.
5. Convert a class component with state and lifecycle methods into a functional component using hooks.

## Section I: Deep Dive — React Props vs State

1. Create a ProfileCard component that receives name, age, and bio as props and displays them.
2. Create a Toggle button that maintains its on/off state internally.
3. Build a TodoList component that:
   - Accepts initial todos via props
   - Allows adding new todos using local state
4. Refactor the above to lift the state to a parent component and pass data + handlers as props.
5. Explain what happens when you modify a prop inside a component and how React handles it.

## Section J: All About React Hooks

1. Build a counter using useState.
2. Build a timer using useEffect.
3. Use useRef to focus an input on mount.
4. Build a light/dark theme switcher using useContext.
5. Build a form reducer with useReducer.
6. Add useMemo to an expensive calculation (like factorial).
7. Use useCallback to memoize a button click handler.

## Section K: Deep Dive into Custom Hooks in React

1. Write a hook useToggle that manages boolean state (true/false) and returns current value + a toggle function.
2. Create useLocalStorage hook to sync state with localStorage.
3. Build usePrevious hook to get the previous value of a prop or state.
4. Make a useDebounce hook that delays updating a value by a set time (used in search inputs).
5. Combine useFetch and useLocalStorage to fetch data and cache it locally.

## Section L: Advanced React Hooks Topics

1. Implement a todo app using useReducer to manage todos (add, toggle complete, delete).
2. Create a theme context with a toggle function using useContext and useState.
3. Combine useReducer and useContext to manage global todo state and dispatch actions from child components.
4. Experiment with passing multiple contexts and consuming them using hooks.

## Section M: React Router with Hooks, React Query, and State Management Libraries

1. Build a small app with React Router using useNavigate and useParams.
2. Use React Query to fetch and display data from a public API.
3. Set up Redux Toolkit in a React app with a simple counter slice.
4. Compare state management with useContext + useReducer vs Redux Toolkit.

## Section N: React Router (with Hooks)

1. Build a multi-page app with nested routes (e.g., /dashboard/settings).
2. Use useNavigate to redirect after a login simulation.
3. Extract multiple params and query strings with useParams and useLocation.

## Section O: React Query (TanStack Query)

1. Fetch and display paginated API data with React Query.
2. Implement add/delete functionality with useMutation.
3. Use query invalidation to update UI after mutations.

## Section P: Redux Toolkit

1. Build a todo app with Redux Toolkit and add async API calls.
2. Add loading and error states for async actions.
3. Explore Redux DevTools for debugging.

## Section Q: React Hook Form

1. Build a form with validation for required fields.
2. Integrate form submission with API.
3. Use form-level and field-level validation.
