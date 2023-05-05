### Intro: React Context

- not tobe confused with JacaScript Context ,React context provides us with a wasy to pass down data through the component tree without haveing to pass props manually at every single level.
- Conttect is designed to share data that can be considered "global" for a tree of React components, such as currnet aurthenticated user, theme, or prreferred langugage

- Context is primarily used when dsome data needs to be accessible by MANY components at different nesting levels .Applyu it sparingly because it makes component reuse more difficult

- Prop threading : Data is received from a parent component and passed down to a child componenet . if a child of that copent needs the same prop it is passed AGAIN to the next child compoent and son on... A=-> B => C -> D \_. E

- React Context: Data is passed down from a parent component to ANY nested child component. A => E

### The 3 important parts of the React Context API

- Provider: Acomponent that is used to wrap otthwe conponentes in order to give access to the contest's value. In our vcase, we will wrap the entire application , `<App />`.

= CONSTUMER : Is a React components that reada a context's value. Consumer components must always be nested under Provider components bvecoaouse the Provider must render FIRST in order to pass that data down the tree. IN other words, needs to exist vefore someone can talk to it

- CONTEXT : Allows "global" data in a React appication and stores a single value
  - createContesxt() : creates a global object
  - useCOntext() : consumes that global information
