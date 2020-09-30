---
title: Introduction to React Hooks
theme: beige
highlightTheme: rainbow
revealOptions:
    slideNumber: 'c/t'

---
# Introduction to 
# React Hooks

## Rachel Davies
![Tes Logo](images/tes_logo.jpg)

Notes:  
Hooks were added to React last year. 
If you haven’t tried them out yet, this talk aims to give an introduction with some examples. 
We’ll also cover some factors to consider in using them and some examples of how to write tests for code using Hooks.

---

## A bit about me

* Full-stack software engineer
* Work remotely for Tes
* Busy writing Python nowadays

Notes: 

---

## A bit about Tes

* Digital education company
    * support and connect teachers and schools worldwide
* 50+ full-stack engineers in 10 teams
    * Javascript microservices 
    * Remote-first culture before COVID

Notes: 
       
---

## Your Background?

![Hands](images/hands.jpg)

Notes: 
Who is using React Hooks?

---

# Introduction to 
# React Hooks

---

## Hooks?

> _"Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class."_
February 6, 2019

Notes: 

---

## Functional Components

- Less code
- Easier to read and test
- Separate container and presentational components

Notes: 
At Tes we prefer to write functional rather than class components.

---

## Big 3 React Hooks 

- useState
- useEffect
- useContext

Notes: 


---

### More React Hooks

- useReducer
- useCallback
- useMemo
- useRef
- useImperativeHandle
- useLayoutEffect
- useDebugValue


---

### Custom Hooks

- you can write your own custom hooks
- you can use custom hooks from other frameworks
    - react-redux, react-router, graphql, etc

---

## State Hook

``` javascript
import React, { useState } from 'react';

const Counter = () => {
    const [count, setCount] = useState(0);
    return (
        <div>

            <p>You clicked {count} times</p>

            <button onClick={() => setCount(count + 1)}>
                Click me
            </button>
        </div>
    );
}
```

Notes: 
useState gives us the current state

---

## State Hook

![Units](images/setStateExample.png)

Notes: 
useState gives us the current state

---

## Effect Hook

let's you perform side effects in function components

``` javascript
import React, { useEffect } from 'react';

const Counter() => {
    // called after each render
    // similar to lifecycle componentDidMount and componentDidUpdate
  useEffect(() => {
    // manually change DOM in React using the browser API
    document.title = `You clicked ${count} times`;
  }, [count]); // Only re-run the effect if count changes
}
```

Called after **every** render. 
The function we pass in **is** our effect

Notes: 
Operations like fetching data from API, setting up subscriptions and manually changing the DOM in React Component are called “side effects” or effects for short as they can affect other components and can’t be done before rendering. 
second argument to useEffect that is the array of values that the effect depends on.

---

## Synchronous Effects

Effects scheduled with `useEffect` don’t block the browser from updating the screen. Can makes your app feel more responsive.
  
If you need to run your effect synchronously after all DOM mutations, another hook is available **useLayoutEffect** 

---

## Context Hook

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

Accepts a context object, a value returned from React.createContext, and returns the current context value for that context

``` javascript
// declared at top level in app
const ThemeContext = React.createContext(themes.light);

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </button>
  );
```


Notes: 
In a typical React application, data is passed top-down (parent to child) via props, but this can be cumbersome for certain types of props (e.g. locale preference, UI theme) that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree
https://reactjs.org/docs/context.html
Context is primarily used when some data needs to be accessible by many components at different nesting levels. Apply it sparingly because it makes component reuse more difficult.

---

## Rules of Hooks

- Only call Hooks at the top level
  - Don’t call Hooks inside loops, conditions, or nested functions!
- Only call Hooks from React functions (components or custom hooks)
  - Don’t call Hooks from regular JavaScript functions  

Notes: 
Ensure that Hooks are called in the same order each time a component renders. That’s what allows React to correctly preserve the state of Hooks between multiple useState and useEffect calls
Ensure that all stateful logic in a component is clearly visible from its source code.

---

## Enforce Rules with ESLint

- eslint-plugin-react-hooks

Notes: 

---

## Combining Hooks

- setState from useEffect?
    - commonly used for data fetching
- beware infinite re-render loop!
    - remember to pass array as a 2nd argument
    
TRY NOT TO DO THIS
``` javascript
useEffect(() => {
  setState({ ...state, a: props.a });
}, [props.a]);

useEffect(() => {
  setState({ ...state, b: props.b });
}, [props.b]);
``` 
https://codesandbox.io/s/confident-lederberg-dtx7w    
    
Notes: 
useEffect is called after each render and when setState is used inside of it, it will cause the component to re-render which will call useEffect and so on and so on.

One of the popular cases that using useState inside of useEffect will not cause an infinite loop is when you pass an empty array as a second argument to useEffect like useEffect(() => {....}, []) which means that the effect function should be called once: after the first mount/render only. 
This is used widely when you're doing data fetching in a component and you want to save the request data in the component's state.
https://stackoverflow.com/questions/53715465/can-i-set-state-inside-a-useeffect-hook

---

In **previous** code both useEffects run in the same react cycle.
When you run the second setState it will replace the first setState.

DO THIS INSTEAD

``` javascript
useEffect(() => {
  setState(state => ({ ...state, a: props.a }));
}, [props.a]);

useEffect(() => {
  setState(state => ({ ...state, b: props.b }));
}, [props.b]);
``` 
Check the solution here: https://codesandbox.io/s/mutable-surf-nynlx

---

## React Redux Hooks

from v7.1.0

``` javascriptimport React from 'react'
import { useSelector } from 'react-redux'

export const CounterComponent = () => {
  const counter = useSelector(state => state.counter)
  return <div>{counter}</div>
}
```

Notes:

---
## React Router Hooks

from v5.1

``` javascript
import { useRouteMatch } from "react-router-dom";

function BlogPost() {
  let match = useRouteMatch("/blog/:slug");

  // Do whatever you want with the match...
  return <div />;
}
```

Notes:


## GraphQL 

``` javascript
import { gql, useQuery } from '@apollo/client';

const GET_DOGS = gql`
  query GetDogs {
    dogs {
      id
      breed
    }
  }
`;

const Dogs = ({ onDogSelected }) => {
  const { loading, error, data } = useQuery(GET_DOGS);

  if (loading) return 'Loading...';
  if (error) return `Error! ${error.message}`;

  return (
    <select name="dog" onChange={onDogSelected}>
      {data.dogs.map(dog => (
        <option key={dog.id} value={dog.breed}>
          {dog.breed}
        </option>
      ))}
    </select>
  );
}
```

---

## Testing with React Hooks

> Sorry I ran out of time so nothing here yet

Notes:


---

## React Hooks help you to ..

* simplify component design

Notes: Summing up ^^

---

## Thank You
#### @rachelcdavies @tes_engineering
![Tes Logo](images/tes-career-hero.png)

Notes: 


---
## Render Props

The term “render prop” refers to a technique for sharing code between React components using a prop whose value is a function.


``` javascript 
<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
``` 

Notes:

