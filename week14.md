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

`--------------------------------------------------------------------------------------------------------------`

### Function Component

- Creat a Function Component
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
