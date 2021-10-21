# React

## Props

Props are inputs to react components, passed from a parent to a child compoinent.
Props can be be accessed via `props`.

## State

State can be be accessed and set via `useState(initialValue)`
For a particular piece of data there should only be _one_ component that owns it in its state.
If you need to synchronize between components, make the closest common ancestor the owner and pass it down as props.

## Side effects

To perform side effects you can use `useEffect(callBack)`.
By default `useEffect(cb)` runs after the initial render _and_ after each update.

## Context

To access a context you can use `useContext(context)`

## Lifecycle

There are different stages in the lifecycle of a component:

- **Mounting** - when it gets created and flushed into the DOM.
- **Update** - when the component gets updates
- **Unmounting** - when the component gets removed from the DOM
