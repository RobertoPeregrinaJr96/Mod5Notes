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
  - `useState`: a useState declares a “state variable”. This is a way to “preserve” some values between the function calls (for a function component, that means rerenders).
    - Normally, variables “disappear” when the function exits, but state variables are preserved by React.
- What do you pass to useState as an argument?

  - The only argument to the useState() hook is the initial state
    - You can keep a number, a string, an object, an array, etc.

- `Effect Hooks`

  - useEffect: a Effect Hook tells React that your component needs to do something after render so React will remember it and call it later after preforming the DOM updates

    - The first and only required argument is the function to call

  - if place the useEffect inside the component then it will allow you to access any state vaeriable or prop right from the effect as it will be inside the function scope

  - useEffect runs both after the first render and after every update (rerender)

- `Other Hooks`

- `useCallback` : This allows you to wrap a function definition, so it only gets remade when certain values change (rather than on every single rerender).

- `useContext` : Allow you read a context and subscribe to its changes. You will study this soon!

- `useRef` : A mutable (that is, changeable) ref object often used to store a pointer to dom elements. You will have the opportunity to explore this later in this course.

- `useReducer` : Alternative to useState for cases where you have complex objects and want to optimize performance.

### `State`

- State is a variable where one can store and preserve values betwwen re-renders

  - A render or re-render is when the function component,which is just a function is invoked again\

  - State does not persist after reloading the page

    - when we reload a page we are recreating the DOM tree

    - when we rerender we re-invoke or invoke the functional Component which will in turn render the return in the function component

- `Two Kinds Of State`

  1. Component or Local State (useState)

  2. Global State (react Context, Redux)

- `useState Hook Syntax`

  - the useState hook is a function that takes an optional initial value as an argument and returns an array with two indexes which we destructure

  ```js
  const [title, setTitle] = useState("React Hooks")``;
  ```

  - `First Index`: current State

  - `Second index`: update function

## `Declare UI` > `DOM Events` > `Update State` > `Update Virtual DOM` > `Update DOM`

- `Example`

```js
const StateComponent = () => {
  const [title, setTitle] = useDate("Initial Value");
  return (
    <div>
      <h2>
        The state Variable, 'title',holds this value:
        <span>className='spanner'>{title}</span>
      </h2>
    <button
        onClick ={( =>
            setTitle(
            'I clicked the button and updated the state,which triggered the component to Re-Render!'
            )
         )
        }
    >
    Update State
    </button>
    </div>
  );
};
```

`What is a state variable in React?`

- The function that updates state

- A variable that describes how a component renders

- A variable whose value gets preserved across rerenders

- A variable that holds the values passed from the parent component

- `EXPLANATION`

```
State variables are a way to preserve some values between function calls/rerenders.
```

`What argument can useState take?`

- Any data type, including a function

- Only arrays

- Only a primitive data type

- Only objects

- `EXPLANATION`

```
The argument passed to the useState hook is used only when the component gets evaluated for the first time. It can be any data type and value that you want to use as the initial value.
```

`How can you update the value of a state variable that came from the useState hook?`

- By setting the value of the variable directly

- By using the setState method

- By using the useUpdate hook

- By calling the updater function that is returned from the useState hook

- `EXPLANATION`

```
  The value that comes from the useState hook can, and should only, be updated by calling the updater function that comes as the second value in the array returned by the useState hook.
```

`What is returned when you call useState?`

- An updater function

- The current state

- An array with the current state and an updater function

- All the previous states

- `EXPLANATION`

```
  Since JavaScript functions can return only one value, the useState hook returns a single array that holds the value of the current state and an updater function.
```

### `useEffect Hook Intro`

- the useEffect hook handeles asynchronus opersations and invokes side effects in function al copoentts

- side effects? = Anything that saffects somethingsoutside the scope of the current function being executed

- When to use useEffect Hook

  1. Data Fetching
  2. Handdling Subvvscriptions
  3. Timers
  4. Directlyh changing the DOM
  5. Updating based on tstate or props

- `useEffect syntax - useEffect(function , array)`

```js
useEffect(
  () => {
    /*
    logic goes here
    */
  },
  [
    /*  dependency array  */
  ]
);
```

- Example

```js
const Dog = () => {
    const [dogImage,setDogImage] = useState('');

    useEffect(() => {
        cosnt fetchDogs = asynce () => {
            const response = await fetch(
                'api.url'
            );
            if(response.ok){
                const dog = await response.json();
                setDogImage(dog.message);
            }
        }
        fetchDogs();
    }, [])
return (
    <div className = 'home-container'>
    <h1>Doberman</h1>
    {dogImage === ''}
    <h1>loading...<h1>
    ) : (
        <div>
            <img src={dogImage} alt = {dogImage} />
        </div>
    )

}

```

- `When does a useEffect run?`

  - Impossible to gauge

  - Synchronously with the painting of the DOM

  - Before the component renders for the first time

  - After the component's first render and every subsequent render

`EXPLANATION`

```
By default, a useEffect hook runs after the first render of a component and after every subsequent render. (If a dependency array is supplied, then the useEffect will run after the first render and after any subsequent render when a dependency in the array has changed.)
```

- `The dependency array in a useEffect hook`

  - Stores state values

  - Listens for changes in state and props

  - Stores prop values

- `EXPLANATION`

```
  A dependency array is an optional argument for a useEffect hook that listens for changes in state and/or props. A useEffect with a dependency array will run only after renders in which such changes have been detected (including--always--the first render).
```

- `The one required argument for a useEffect hook is`

  - An object

  - An async function

  - An anonymous function

  - A dependency array

- `EXPLANATION`

```
  The only required argument for a useEffect hook is an anonymous function.
```

- `What could the callback function in a useEffect hook return?`

  - An object containing the new values of any state variables the useEffect has changed

  - A cleanup function

  - A boolean signifying whether or not the useEffect ran successfully

  - A dependency array

- `EXPLANATION`

```
  The callback function in a useEffect hook may optionally return a cleanup function that will be run before the useEffect runs again and after the component unmounts.
```

- `Select all that apply: A good use case for a useEffect with an empty dependency array is`

  - To change an image in the component as a state variable changes

  - To make a fetch call to a third-party API

  - To declare state variables

  - To render a component

  - To toggle a data display on and off in response to a button click

- `EXPLANATION`

```
  A useEffect with an empty dependency array will run only once, after the first render. Making a fetch call to a third-party API and then setting the state with the fetched data is a common use for such a useEffect.
```
