# React

## Props

Props are inputs to react components, passed from a parent to a child compoinent.
Props can be be accessed via `props`.
Props are **read only**. Do not modify props!

## State

State can be be accessed and set via `useState(initialValue)`
For a particular piece of data there should only be _one_ component that owns it in its state.
If you need to synchronize between components, make the closest common ancestor the owner and pass it down as props.

## Side effects

To perform side effects you can use `useEffect(callBack)`.
By default `useEffect(cb)` runs after the initial render _and_ after each update.

## Events

In React u generally don't call `addEventListener`, you just provide a listener, when the element is initially rendered.

## Keys

You can render an array of items in React. In that case you need to assign a unique ID to each instance of your items.
Keys must only be unique among siblings, not globally.
Don't assign the key in the component declaration but in the place where you instantiate your component.
Keys don't get passed as props, i.e. you can't access `props.key`. If you need your key inside the component, pass it seperately as a prop with a different name.

## Context

To access a context you can use `useContext(context)`

## Lifecycle

There are different stages in the lifecycle of a component:

- **Mounting** - when it gets created and flushed into the DOM.
- **Update** - when the component gets updates
- **Unmounting** - when the component gets removed from the DOM

## Reducers

An alternative to `use state`. Usually used with complex state logic like multiple sub-values or when the next state depends on the previous one.
Accepts a reducer of type `(state, action) => newState`, returns the current state paired with a dispatch method.

## Refs

You can get a ref to an element via `useRef()`.

## Nesting Components

React components are just JavaScript Objects, and can be handled accordingly.
You can access all children passed into a component via `props.children`.
You can pass components as props into a component.
