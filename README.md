### 1. **React Code Splitting**  
Code splitting is a technique used in React to optimize performance by loading JavaScript in chunks instead of a single bundle. This helps improve initial load time by only downloading necessary code.  

#### How It Works:  
React leverages **dynamic imports** and **React.lazy** to achieve code splitting:  
- **React.lazy** allows you to import components dynamically.
- **Suspense** is used to wrap lazy-loaded components and display a fallback (like a loading spinner) while the component loads.

#### Example:  
```jsx
import React, { Suspense } from "react";

const LazyComponent = React.lazy(() => import("./LazyComponent"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}

export default App;
```
Other tools like **Webpack** and **React Router** also support code splitting at route level.

---

### 2. **Styled Components**  
Styled-components is a popular library for styling React components using tagged template literals. It enables writing CSS directly inside JavaScript, leading to component-scoped styles.

#### Benefits:  
- No class name conflicts  
- Dynamic styling using props  
- Supports themes  

#### Example:  
```jsx
import styled from "styled-components";

const Button = styled.button`
  background: ${(props) => (props.primary ? "blue" : "gray")};
  color: white;
  padding: 10px;
  border-radius: 5px;
`;

function App() {
  return <Button primary>Click Me</Button>;
}

export default App;
```
Styled-components help keep styles modular and reusable.

---

### 3. MATERIAL UI

### 4. Service layer Custom API methods Architechture

# Hooks

### 1. **useId**  
The `useId` hook generates unique IDs for accessibility and forms, preventing conflicts when multiple instances of the same component are rendered.

#### Example:
```jsx
import { useId } from "react";

function Form() {
  const id = useId();

  return (
    <div>
      <label htmlFor={id}>Name:</label>
      <input id={id} type="text" />
    </div>
  );
}

export default Form;
```
- **Use Case:** Useful when IDs are required but should not conflict in SSR or multiple instances.

---

### 2. **Custom Hook**  
A custom hook is a reusable function that encapsulates logic using built-in React hooks.

#### Example: Fetching Data Hook:
```jsx
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((data) => {
        setData(data);
        setLoading(false);
      });
  }, [url]);

  return { data, loading };
}

export default useFetch;
```
Usage:
```jsx
const { data, loading } = useFetch("https://api.example.com/users");
```
**Advantages:**  
- Promotes reusability  
- Makes components cleaner  

---

### 3. **React.memo() (useMemo)**  
- `React.memo()` is a higher-order component (HOC) that **prevents re-rendering** of a component if its props haven't changed.
- `useMemo` **memoizes values**, recomputing them only when dependencies change.

#### `React.memo` Example:
```jsx
const MyComponent = React.memo(({ name }) => {
  console.log("Rendered");
  return <div>Hello, {name}</div>;
});
```
Even if the parent re-renders, `MyComponent` won’t unless `name` changes.

#### `useMemo` Example:
```jsx
import { useMemo } from "react";

function ExpensiveCalculation({ number }) {
  const squared = useMemo(() => number * number, [number]);

  return <div>Squared: {squared}</div>;
}
```
**Use Case:** Prevents expensive calculations from running unnecessarily.

---

### 4. **useCallback**  
`useCallback` memoizes functions so they don't get re-created on every render.

#### Example:
```jsx
import { useCallback, useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount((prev) => prev + 1);
  }, []);

  return <button onClick={increment}>Count: {count}</button>;
}
```
**Use Case:** Useful when passing functions as props to prevent unnecessary re-renders.

---

### 5. **useLayoutEffect**  
Similar to `useEffect`, but runs **synchronously** after DOM mutations, before the browser paints.

#### Example:
```jsx
import { useLayoutEffect, useRef } from "react";

function Component() {
  const ref = useRef(null);

  useLayoutEffect(() => {
    console.log("Element width:", ref.current.offsetWidth);
  });

  return <div ref={ref}>Hello</div>;
}
```
**Use Case:** Used for measuring DOM elements before rendering to avoid flickering.

---

### 6. **useImperativeHandle**  
Used with `forwardRef` to control child component functions from the parent.

#### Example:
```jsx
import { useRef, useImperativeHandle, forwardRef } from "react";

const Child = forwardRef((props, ref) => {
  useImperativeHandle(ref, () => ({
    alertMessage: () => alert("Hello from Child!"),
  }));

  return <button>Child Button</button>;
});

function Parent() {
  const childRef = useRef();

  return (
    <>
      <Child ref={childRef} />
      <button onClick={() => childRef.current.alertMessage()}>
        Call Child Function
      </button>
    </>
  );
}

export default Parent;
```
**Use Case:** Useful when a parent needs to trigger methods in a child component.

---

### 7. **PropTypes**  
PropTypes validate prop types at runtime to catch errors early.

#### Example:
```jsx
import PropTypes from "prop-types";

function Greeting({ name, age }) {
  return (
    <div>
      Hello {name}, you are {age} years old.
    </div>
  );
}

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
};

export default Greeting;
```
**Use Case:** Helps catch incorrect prop types during development.

---
