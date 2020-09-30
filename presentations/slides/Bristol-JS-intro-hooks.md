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
    * Remote-first culture
    * 200+ Javascript micro-services Node/React 

Notes: 
       
---

## Your Background?

![Hands](images/hands.jpg)

Notes: 
Who is using React Hooks?

---

# Introduction to 
# React Hooks

----

## What is a Hook?

> _"Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class."_
February 6, 2019

Notes: 
At Tes we prefer to write functional rather than class components.
Challenge 1 – Hard to reuse stateful logic between different components
Challenge 2 – Complex components are harder to understand

----

## Functional vs Class Components

- Less code
- Functional components are much easier to read and test
- Help separate container and presentational components

Notes: 
These can be typically defined using arrow functions
The simplest way to define a component in React is to write a JavaScript function which accepts props and returns a React element.

A class component requires you to extend from React.Component and create a render function which returns a React element
https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108
Stateless function components introduced in 2015 
https://reactjs.org/blog/2015/10/07/react-v0.14.html#stateless-functional-components

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
    - react-redux, 

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
    // similar to lifecycle events componentDidMount and componentDidUpdate
  useEffect(() => {
    // manually change DOM in React using the browser API
    document.title = `You clicked ${count} times`;
  });

}
```
Called after **every** render
The function we pass **is** our effect
Effects scheduled with useEffect don’t block the browser from updating the screen

Notes: 
If you’re familiar with React class lifecycle methods, you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.
Operations like fetching data from API, setting up subscriptions and manually changing the DOM in React Component are called “side effects” or effects for short as they can affect other components and can’t be done before rendering. 

---

## Synchronous Effects

Effects scheduled with `useEffect` don’t block the browser from updating the screen. This makes your app feel more responsive.
 
The majority of effects don’t need to happen synchronously.
 
To run your effect synchronously after all DOM mutations, try **useLayoutEffect** Hook 

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

## ESLint Plugin

- eslint-plugin-react-hooks

Notes: 

This ESLint plugin enforces the Rules of Hooks.

---

## Combining Hooks

- setState from useEffect?
    - commonly used for data fetching in a component
- beware infinite re-render loop
    - pass array as a 2nd argument
    
``` javascript    
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]); // Only re-run the effect if count changes
```    

Notes: 
useEffect is called after each render and when setState is used inside of it, it will cause the component to re-render which will call useEffect and so on and so on.

One of the popular cases that using useState inside of useEffect will not cause an infinite loop is when you pass an empty array as a second argument to useEffect like useEffect(() => {....}, []) which means that the effect function should be called once: after the first mount/render only. 
This is used widely when you're doing data fetching in a component and you want to save the request data in the component's state.
https://stackoverflow.com/questions/53715465/can-i-set-state-inside-a-useeffect-hook

---

## React Redux Hooks

> React Redux supports Hooks since v7.1.0

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

React Router supports hooks since v5.1

``` javascript
import { useRouteMatch } from "react-router-dom";

function BlogPost() {
  let match = useRouteMatch("/blog/:slug");

  // Do whatever you want with the match...
  return <div />;
}
```

Notes:

---

## Testing with React Hooks



Notes:


---

## React Hooks help you to ..

* simplify design

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

