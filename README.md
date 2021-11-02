### Today's Plan:

- [x] What is React?
- [x] Building a project w/ Create-React-App
- [x] What is JSX?
- [x] Components
- [x] Event Handlers
- [x] Review of Closures
- [x] State
- [x] Props

### React

- From the landing page of [React](https://reactjs.org/):
  > A JavaScript library for building user interfaces
- Open source project maintained by Facebook
- React is built around the concept of managing data
  - Changes to the underlying data result in changes to the UI
  - In React, state === data
- Component-based: UI is composed of small pieces
- Declarative: We describe the final outcome of our code and not the step-by-step process to achieve that result

### JSX

- It stands for JavaScript XML.
- To describe what the UI should look like.
- We will have to these rules to write JSX correctly:

#### Rule 0

`import React from "react";` AND `export default _______` <- your function name here

#### Rule 1 - All Tags MUST be closed.

```jsx
<div>
  {/* ... Components or other HTML in here ...  which are also closed correctly! */}
</div>
```

Or

```jsx
<ListItem />
```

#### Rule 2 - Child tags MUST close before the parent.

```jsx
<ul>
  <li>Child1</li>
  <li>Child2</li>
  <li>Child3</li>
  <li>Child4</li>
</ul>
```

#### Rule 3 - All JSX expressions MUST have a parent (or root) element.

```jsx
return (
  <div>
    <span>Name: Chuck Norris </span>
    <p>Chuck Norris threw a grenade and killed 50 people, then it exploded.</p>
  </div>
);
```

### Components

- Components are the building blocks of a webpage (eg. search input, navigation bar, contact us form)
- Ideally, components should be reusable (which means that their state should be passed into them via props rather than maintaining their own state)
- Deciding which DOM elements become components and which don't is a skill that comes with practice and experience
- We will be building all of our components using functions
- The functions return value contains a mixture of HTML and JS; React calls this `JSX`

```jsx
// basic component
import React from "react";

const MyComponent = () => {
  return (
    <div className="my-component">
      <h1>Hello World</h1>
    </div>
  );
};

export default MyComponent;
```

### Event Handlers

- Functions that are extecuted when some event has raised.
- Don't forget to pass a function as the event handler, not a funciton call.

```jsx
// basic component
import React from "react";

const CounterButton = () => {
  let [counter, setCounter] = useState(0);

  return (
    <div className="counterButton">
      <h2>The value of the counter is {counter}</h2>
      <button
        onClick={() => {
          setCounter(counter + 1);
        }}
      >
        Increase
      </button>
    </div>
  );
};

export default MyComponent;
```

### Review of Closures

- From MDN:
  > A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the **lexical environment**). In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function **creation** time.
- In other words, functions remember where they were declared and what variables were in scope (they had access to) at the time they were declared
- This allows us to preserve _state_ in between function calls (subsequent calls to the function can use the updated state value)
- Contrasting with JS Classes (how we used to create React components): components as objects were instantiated from a Class and it was the same object that was used over and over again. Therefore it always had access to its own internal state. Functional components need some way of creating a _closure_ so that we can achieve the same result.
- Enter `useState` (and other `use` functions) which keep track of state for us between function calls and allow us to retrieve and edit variables every time the function is invoked (eg. the component is created/updated)

### State

- State (data) is created in a component by using the `State` hook (`useState`)
- `useState` takes an initial value for state which will be used on the first render
- `useState` returns the current value of state and a function (a way to set the value)

```js
// it's common to destructure the return value from useState
const [username, setUsername] = useState("");
```

#### NOTE: We need to use `useState` to keep track of our data so that React will know when changes occur

### Passing Props

- Child components can be passed pieces of state (data) from their parent component
- These props are accepted in the child component as an argument (usually called `props`)

```jsx
// in parent component
import MyComponent from "./components/MyComponent.jsx";

// inside the parent's return
<MyComponent studentName="Alice"></MyComponent>;

// inside child component
const MyComponent = (props) => {
  console.log(props); // we will see an object with keys studentName.
  return (
    <div>
      <h1>Hello {props.studentName}!</h1>
    </div>
  );
};
```

- Props are not limited to JS primitives and data structures; you can also pass behaviour from parent-to-child in the form of functions

### Useful Links

- [ReactJS Docs](https://reactjs.org/docs/getting-started.html)
- [MDN: Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- [npx VS. npm](https://stackoverflow.com/questions/50605219/difference-between-npx-and-npm)
