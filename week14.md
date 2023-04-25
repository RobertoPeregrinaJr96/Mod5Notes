# Week 14

# `Monday's Homework`

- `ES6`

  - import = we can use import to import relalive npm Packages ,importing Css pathways as well as importing from moduels
  - named export = we can have as many named exports as we want on the file, named exports have to be imported with the same name that they were exported
  - default export = we can only have one to a file it will usally be reserved for Redux reducer or when you export Functional componets , default exports when imported can be named whatever we want as they arn't within curly braces

- `JavaScript eXtension`

  - JSX = JavaScript eXtension
  - JSX uses familiar Html sytax in JavaScript files that can be transpiled by tools like babel

- `Creating Elemtes`
  - we create varibles that have the value of HTML sytax
  - virtual DOM = these varible that contain HTML sytax are refered to as virtual dom nodes
  - not real HTML = even though we are assigning values that look like HTML sytax they are indeed not atchuly HTML
  - React converts the virtual DOM nodes created from the JSX into real DOM elements
- Example

```js
const navBar = (
  <nav>
    <ul>
      <li>Home</li>
      <li>Profile</li>
      <li>Settings</li>
    </ul>
  </nav>
);
```

- `HTML attributes in JSX`
  - in JSX html attributes are placed as they would be in html in the virtual DOM variable
  - there are a few exception like the class attribute as JSX use's the method ClassName
- Example

```js
const navList = (
  <ul>
    <li className="selected">
      <a href="/pets">Pets</a>
    </li>
    <li>
      <a href="/owners">Owners</a>
    </li>
  </ul>
);
```

- `Converting to virtual DOM`
  - you will use `ReactDOM.render` method which will take a Real DOM node with React virtual DON node and a convert the virtual DOM node into a real DOM and nest it under the given realDOM node
    - Remember, you can get a real DOM node by using `document.querySelector`, or `document.getElementById` (if the element has an id attribute).
- Example

```js
// Put the element tree in a variable
const navList = (
  <ul>
    <li className="selected">
      <a href="/pets">Pets</a>
    </li>
    <li>
      <a href="/owners">Owners</a>
    </li>
  </ul>
);

// Get a DOM node for React to render to
const mainElement = document.querySelector("main");

// Give React the element tree and the target
ReactDOM.render(navList, mainElement);
```

![Alt text](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Modular-Curriculum/content/react-redux/topics/intro-to-react/assets/react-example-conversion-real-dom.svg)

- It takes that real DOM and inserts it as the content of the target that you gave it which, in this case, is the main element in the body of the document.

- Updates

  - When you call `ReactDOM.render` again for the same component and target, React takes the existing virtual DOM it knows about last time it rendered the element tree, compares it to whatever new thing you want to render, and determines which (if any) of the living DOM needs to change.

    ![Alt text](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Modular-Curriculum/content/react-redux/topics/intro-to-react/assets/react-example-virtual-dom-diff.svg)

### SECTION QUIZ

- `Question 1`

  - Which of the following HTML terms have a different form for the equivalent term in JSX? Check all that apply.
    - class
    - aria-label
    - onchange
    - for
  - `EXPLANATION`

```
   - In JSX, HTML's class becomes className, for becomes htmlFor, and onchange becomes onChange.
```

- `Question 2`

  - What is JSX's equivalent to HTML's class attribute?
    - jsx-class
    - className
    - htmlClass
    - class
  - `EXPLANATION`

```
    - className is used in JSX instead of class because class is a reserved keyword in JavaScript.
```

- `Question 3`

  - What happens when you call ReactDOM.render again for the same component and target?
    - React randomly decides to update or reload your component.
    - React converts your newest virtual DOM tree into a new real DOM tree and replaces the older real DOM with the newest version.
    - React compares the updated version you've made with the most recent version that was rendered and determines if the real DOM needs to be updated.
    - React reloads your page to update your content.
  - `EXPLANATION`

    ```
        - If you call ReactDOM.render on the same component and target again, React will compare your latest virtual DOM update to the most recently rendered version of the virtual DOM and decide which nodes, if any, should be updated.
    ```

- `Question 4`

  - When does React convert virtual DOM nodes into real DOM nodes?
    - When React wants to
    - When you call ReactDOM.render
    - When you call React.render
    - When you call your .js file with node
  - `EXPLANATION`

  ```
     You can start the conversion process by using the ReactDOM.render method, which will convert the virtual DOM node into a real DOM node and nest it under the given real DOM node.
  ```

- `Question 5`
  - How can you create virtual DOM nodes with JSX?
    - By calling the renderAsHTML method available in React
    - By adding a jsx attribute to the HTML in your HTML documents
    - By writing JavaScript in the `<body>` of an HTML document
    - By defining HTML syntax in a JavaScript file
- `EXPLANATION`

```
     You can create virtual DOM nodes in React with JSX by defining HTML syntax in a JavaScript file.
```

## Function Component

- `Create a Function Component`
  - A React function component is a function that returns a JSX element
    - The name of the function is PascalCase by convention.
- Example

```js
function NavBar() {
  return (
    <nav>
      <h1>Pet App</h1>
      <ul>
        <li className="selected">
          <a href="/pets">Pets</a>
        </li>
        <li>
          <a href="/owners">Owners</a>
        </li>
      </ul>
    </nav>
  );
}
```

- To convert this into real DOM, you can use the ReactDOM.render function and use the NavBar component as a JSX element.

```js
// Get a DOM node for React to render to
const rootElement = document.getElementById("root");

// Give React the element tree and the target
ReactDOM.render(<NavBar />, rootElement);
```

- Notice how the NavBar function component isn't called explicitly in the code? Instead, it's wrapped in JSX tags and looks just like an HTML tag. This will nest the real DOM converted from the nav JSX element returned from the NavBar function in the real DOM element with the id of root.

  - Note: you cannot define HTML attributes when rendering a function component as a JSX element:
    ` <NavBar className="nav-bar" />` will not apply an HTML attribute of class onto any of the rendered elements in NavBar.

- `Showing nothing`

  - You must return something from a function component
  - You cannot return undefined from a function component. React will not build correctly when trying to render a component that returns undefined If you don't want to render anything from a component, then return null instead.

- `Example`

```js
const str = "hello";

function ExampleComponent() {
  if (str === "hello") return null;
  else return <div>World!</div>;
}
```

- When rendered, this component will not show anything on the page if str is "hello". If str isn't "hello", the component will show a div with the text "World!" inside of it.

- `Nested Function Component`

  - To render a function component in another function component, you can apply the same principle above.
  - Wrap the desired nested function component in JSX tags just like you would a regular HTML tag in the return of the outer function component.

- `Example`

```js
function NavLinks() {
  return (
    <ul>
      <li className="selected">
        <a href="/pets">Pets</a>
      </li>
      <li>
        <a href="/owners">Owners</a>
      </li>
    </ul>
  );
}

function NavBar() {
  return (
    <nav>
      <h1>Pet App</h1>
      <NavLinks />
    </nav>
  );
}
```

- The NavBar component is the parent of the NavLinks component, which means NavBar is rendering the NavLinks component as its child.

- `Component organization`

  - When breaking down components into smaller components, you can also divide them up into multiple files.
  - it's common to have one component per file and export/import them when you need them in other components.

- `Example`

```js
// NavLinks.js

function NavLinks() {
  return (
    <ul>
      <li className="selected">
        <a href="/pets">Pets</a>
      </li>
      <li>
        <a href="/owners">Owners</a>
      </li>
    </ul>
  );
}

export default NavLinks;
```

- NavBar can also be defined in its own file called NavBar.js. To use the NavLinks component, it can import it at the top of the file. It should also export itself from this file.

```js
// NavBar.js
import NavLinks from "./NavLinks.js";

function NavBar() {
  return (
    <nav>
      <h1>Pet App</h1>
      <NavLinks />
    </nav>
  );
}

export default NavBar;
```

- `React.fragment`

  - React function components need to always return one JSX element as the highest level tag.
    - There will be a React compilation error if there is more than one outermost parent element returned from a function component.

- `Example`

```js
// THIS COMPONENT WILL NOT WORK
function IncorrectComponent() {
  // returns two div tags (WILL NOT WORK)
  return (
    <div></div>
    <div></div>
  );
}
```

- There are two ways to solve this issue.

  - wrap the elements in a parent element like another div
    - but this would generate another real HTML element.
  - rap the elements in a JSX element called React.fragment and no other real HTML element will be created.

- `Example`

```js
import React from "react";

function CorrectComponent() {
  // returns two div tags wrapped in React.fragment (WILL WORK)
  return (
    <React.fragment>
      <div></div>
      <div></div>
    </React.fragment>
  );
}
```

- You can also return empty tags that will be read in JSX as React.fragment.

```js
import React from "react";

function CorrectComponent() {
  // returns two div tags wrapped in empty tags (WILL WORK)
  return (
    <>
      <div></div>
      <div></div>
    </>
  );
}
```
