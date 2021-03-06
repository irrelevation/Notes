# React

## 5 steps to create a React UI

1. Break the UI into a **component hierarchy**
   - Find out how the designer divided up the UI
   - Identify components in your mockup, draw boxes around them and name them
   - SOLID principles and other OO guidlines can guide that process
   - CSS classes and design layers are good starting points too
2. Build a **static version** in React
   - Build static components
   - Pass data via props
   - Don't use state yet
   - For simple UIs build top-down, for complex UIs build bottom-up
3. Identify minimal complete UI **state**
   - Use state only when necessary
   - Calculate everything else on demand (don't duplicate state that can be derived)
   - If it doesn't change, it isn't state.
   - If it is passed in via props, it isn't state.
4. Identify where your state should live
   - Identify all components that render the state
   - State can usually be put in the closest common ancestor or higher up the component tree
   - Otherwise you can create a component just to hold the state
5. Add inverse data flow
   - identify where your state gets updated
   - integrate state setter accordingly

## 3 phases of Reacts render cycle

1. **Trigger**
   - A render gets triggered initially when you call `ReactDOM.render()`.
   - A re-render gets triggered when states or props change.
2. **Render**
   - React renders the component and recursive renders all other components rendered within that component.
3. **Commit**
   - React updates the DOM to match the newly rendered output.
   - React minimizes the amount of channges to reach that state.
   - If parts of the output do not differ, React will _not_ change the corresponding part of the DOM.

## Props

Props are inputs to react components, passed from a parent to a child compoinent.
Props can be be accessed via `props`.
Props are **read only**. Do not modify props!

## State

State can be be accessed and set via the `useState()` hook.
`useState()` returns a state variable and a setter `[state, setState]`.
The state variable will persist data between renders.
The setter changes the data and triggers a re-render.
For a particular piece of data there should only be _one_ component that owns it.
If you need to synchronize between components, make the closest common ancestor the owner and pass it down as props.

## Side effects

To perform side effects you can use `useEffect`.
By default `useEffect` runs after the initial render _and_ after each update.

## Events

In React you generally don't call `addEventListener`, you just provide a listener, when the element is initially rendered.

## Keys

You can render an array of items in React. In that case you need to assign a unique ID to each instance of your items.
Keys must only be unique among siblings, not globally.
Don't assign the key in the component declaration but in the place where you instantiate your component.
Keys don't get passed as props, i.e. you can't access `props.key`. If you need your key inside the component, pass it seperately as a prop with a different name.

## Context

To access a context you can use `useContext(context)`

## Component Lifecycle

There are different stages in the lifecycle of a component:

- **Mounting** - when it gets created and flushed into the DOM.
- **Update** - when the component gets updates
- **Unmounting** - when the component gets removed from the DOM

When a component unmounts the allocated memory gets freed for garbage collection and its state is lost.
A components identity is determined via its position in the DOM and the reference of the function (or class) that created it.
That means if you conditionally render a component with a wrapper element (eg. a div) React will actually delete the old component and create a new component.
It also means you should never define a component inside another component. In that case the function ref will change whenever the parent component rerenders. React will unmount the old component and mount a new component. It's state will be lost.

## Hooks

Hooks need to maintain order between renders.
Only call Hooks at the **top level** of React _function_ components or in your own custom Hooks.

## Context

Use context to share data that can be considered "global" for a tree of React components (eg. theme, authenticated user, language, cache).
Create a provider component and a custom hook to use the provided data.

## Reducers

`useReducer(reducer, initialState)` is an alternative to `useState()`.
Reducers are usually used with complex state logic like multiple sub-values or when the next state depends on the previous one.
`useReducer(reducer, initialState)` accepts a reducer of type `(state, action) => newState` and returns the current state paired with a dispatch method.

Keep your reducers pure:

- no side effects, like timeouts, requests, etc.
- no mutation
- same inputs, same outputs

Define one action per interaction, even if the action changes multiple things.

## Refs

Use a ref if you want to remember state between re-renders but don't want to trigger a re-render when the ref changes.
You can get a ref to an element via `useRef(initialValue)`.
You can access the value via `ref.current`.
Unlike state you can mutate refs.

### Use Cases

- Storing timeout IDs
- Storing and manipulating DOM elements like
- Using Browser APIs that are not exposed by React, e.g.
   - focusing
   - scrolling
- Storing objects that are not necessary for rendering

## Nesting Components

React components are just JavaScript Objects, and can be handled accordingly.
You can access all children passed into a component via `props.children`.
You can pass components as props into a component.
