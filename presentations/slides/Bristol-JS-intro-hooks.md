---
title: Introduction to React Hooks
theme: beige
highlightTheme: rainbow
revealOptions:
    slideNumber: 'c/t'

---
# Introduction to 
# React Hooks

#### @rachelcdavies @tes_engineering
![Tes Logo](images/tes_logo.jpg)

Notes:  
Hooks were added to React last year. If you haven’t tried them out yet, this talk aims to give an introduction with some examples. We’ll also cover some factors to consider in using them and some examples of how to write tests for code using Hooks.

---

## A bit about me

* Full-stack software engineer
* Work remotely from home in Bath
* XP/TDD fan since 2000

Notes: 
I started coding 30 years ago before the web and Javascript existed.
I spent time coding in Ada, C, C++, Java and Ruby. 
Relatively new to JavaScript.
20 years ago I was an early adopter of eXtreme Programming an Agile software development approach.
After some years consulting, I made a shift back to coding.
so I could stop commuting to London.
Moved to Bath before Xmas and work from home for Tes.

---

## A bit about Tes

* Digital education company
* 200+ Javascript micro-services Node/React 
* 50+ full-stack engineers in 12 product squads
* Remote-first culture

Notes: We support and connect teachers and schools worldwide, 
helping them to improve children's lives through education
       
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

Notes: 
At Tes we prefer to write functional rather than class components.
Challenge 1 – Hard to reuse stateful logic between different components
Challenge 2 – Complex components are harder to understand

----

## Functional vs Class-Components

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

## Big Three 

- useState
- useEffect
- useContext
- Custom

Notes: 


---

### Additional Hooks


- useReducer
- useCallback
- useMemo
- useRef
- useImperativeHandle
- useLayoutEffect
- useDebugValue

---

## State Hook

``` javascript
import React, { useState } from 'react';

const Example = () => (
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
);
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

The Effect Hook lets you perform side effects in function components

``` javascript
import React, { useEffect } from 'react';

const Example() => {
}
```

Notes: 
The Effect Hook lets you perform side effects in function components
If you’re familiar with React class lifecycle methods, you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.
Operations like fetching data from API, setting up subscriptions and manually changing the DOM in React Component are called “side effects” or effects for short as they can affect other components and can’t be done before rendering. 


---

## Rules of Hooks

- Only Call Hooks at the Top Level
  - Don’t call Hooks inside loops, conditions, or nested functions!
- Only Call Hooks from React Functions (components or custom hooks)
  - Don’t call Hooks from regular JavaScript functions  

Notes: 
Ensure that Hooks are called in the same order each time a component renders. That’s what allows React to correctly preserve the state of Hooks between multiple useState and useEffect calls
Ensure that all stateful logic in a component is clearly visible from its source code.

---
## setState inside useEffect?

- infinite re-render loop!
- pass an empty array as a second argument because an empty set does never change, the effect will run only once
- commonly used for data fetching in a component

Notes: 
setState inside useEffect can create an infinite loop that most likely you don't want to cause.

useEffect is called after each render and when setState is used inside of it, it will cause the component to re-render which will call useEffect and so on and so on.

One of the popular cases that using useState inside of useEffect will not cause an infinite loop is when you pass an empty array as a second argument to useEffect like useEffect(() => {....}, []) which means that the effect function should be called once: after the first mount/render only. 
This is used widely when you're doing data fetching in a component and you want to save the request data in the component's state.
https://stackoverflow.com/questions/53715465/can-i-set-state-inside-a-useeffect-hook

---
## Do React Hooks Replace Redux?

> Redux is a predictable state management library and architecture which easily integrates with React.
- Redux for application state
>   Hooks and Redux – friends, not enemies
> React Redux offers a set of hooks which can be used as an alternative for connect()

Notes:
React Redux since v7.1.0 supports Hooks API and exposes hooks like useDispatch or useSelector.
React Router supports hooks since v5.1.
https://medium.com/javascript-scene/do-react-hooks-replace-redux-210bab340672
the hooks API has made the native React state API a lot more usable
https://tsh.io/blog/react-state-management-react-hooks-vs-redux/
React Redux offers a set of hooks which can be used as an alternative for connect()
https://react-redux.js.org/api/hooks v7.1
Reduce boilerplate https://www.youtube.com/watch?v=3zoIigieur0
---
## Render Props

Notes:

---

## React Pitfalls

- eslint-plugin-react-hooks

Notes:
https://www.youtube.com/watch?v=VIRcX2X7EUk

---

## Testing



Notes:

synchronising side effects to state 

---

## The Difference Between useEffect and useLayoutEffect

- 99% of the time, useEffect

---
## React Hooks help you to ..

* do stuff

Notes: Summing up ^^

---

## Thank You
#### @rachelcdavies @tes_engineering
![Tes Logo](images/tes-career-hero.png)

Notes: 
