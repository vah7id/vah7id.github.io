---
layout: post
title: useState in plain react function component
---



Since I started to keep my react components state-less, I had to figure out a way to handle my global state inside the state-less component instead of passing several props from the class components. It might be your question now, why we started to keep doing that?

1.  Since they are pure functions your assertions are very straightforward and we all know writing the unit test for stateful components is quite a hassle and therefore plain function components are generally preferable.
2.  Secondly, all the annoying and confusing quirks with Javascript’s  **this**  keyword are avoided. The entire component becomes easier to understand without  **this**  keyword
3.  Easy to understand! When you see a stateless functional component, you know it’s simply a function that takes props and spits out HTML.

Since React 16.8, react introduced the hooks and we are able to use the react state hook features inside the stateless components as well. React hook is a special function that lets you “hook into” React features.

**useState**  is a hook that lets you add react state to function components easily. Let’s take a look at the official example from facebook.

    import React, { useState } from 'react';
    import ReactDOM from "react-dom";
    function Increment(initialCount) {
	    const [count, setCount] = useState(initialCount);
	    return (<div>
		    <p>You clicked {count} times</p>
		    <button onClick={() => setCount(count + 1)}>
		    Click me
		    </button>
	    </div>);
    }
    const App = () => Increment(10);
    const rootElement = document.getElementById("root");
    ReactDOM.render(<App />, rootElement);

I used to handle the state inside my state-less components with binding functions from the class components and passing them to our state-less components. It was quite hassling to write the binding functions and was not easy to ready and clean by reading the state-less component to find out what’s going on with the state.

You might have noticed the square brackets!  [Array destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Array_destructuring)  is a cool feature that came along with ES6. Basically this expression helps you to make it possible to unpack values from arrays, or properties from objects, into distinct variables. Therefore you can name them anything that you want.

    const a, b;  
    [a, b] = [1, 2];  
    console.log(a); // 1  
    console.log(b); // 2

So in your stateless component by calling useState hook, It declares a “state variable”. Our variable is called  `count`

The only argument to the  `useState()`  is the initial state and it doesn't need to be an object and it returns a pair of values: the current state and a function that updates it exactly like  **setState**  function.

Quite easy to use ha? let’s convert your components to state-less now!
