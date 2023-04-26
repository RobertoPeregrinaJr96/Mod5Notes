### `Indoduction to hooks`

- Hooks are just functions that let you hook into React Features within functional components

- A hook will listen for a change from the components that will trigger a response( render/ re render base on data change)

-` Why use Hooks`
-Hooks were not originally built into React

- React originally used Class Components and lifecycle methods

- Functional components only rendered Ui

- Complex Class components become hard to understand

- Difficult to reuse certain logic between components

- Class components we too confusing

### `3 basic Hooks`

- `useState`: UseDate is a hook that allows us to have data and persist data through re-renders(different from reloading)

- `useEffect`: UseEffect allow for asynchronous behavior or any behavior that has side effect

- `useContext`: UsContext allows us to share out data throughout the entire application without doing what we call prop threading

### `Hook Rules`

- Only call Hooks from React Function Components

- cant be called in Class Components

- Don't all hooks inside loops , conditions, or nested functions

  - thats because hooks have to be called in the same order every single time

- Hooks must always be called in the same order

- userEffect hook MUST return a callback function

- Don't use async before the useEffect callback function

### `Intro to react Hooks`

- React Hooks are a way for function components to manage state and the component lifecycle.

- they control when parts of the DOM are rerendered (a.k.a. redrawn) to reflect text, color, layout or other changes to the display

- `What are hooks?`

  - A Hook is a special function that lets you “hook into” React features

  - a hook "listens" for changes in order to trigger a response.

  - Hooks solve a wide variety of seemingly unconnected problems in React.

    - Attach reusable behavior to a component

    - Extract stateful logic from a component for independent testing and reuse

    - Split one component into smaller functions based on related pieces

    - Simplify understanding and architecture

- `State Hooks`
  - useState: a `useState` declares a “state variable”. This is a way to “preserve” some values between the function calls (for a function component, that means rerenders).
