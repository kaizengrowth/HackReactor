---
Type: Instructor
UID: 50ee7025-fa3a-4088-8ff6-705af83e2df8
---

# 👩🏽‍🏫 Stateful Components
<!-- markdownlint-disable MD013 -->

| Data point               | Data value       |
|--------------------------|------------------|
| **Demonstration length** | 40 minutes       |
| **Activity type**        | Code Walkthrough |

---

## Story

In this code walkthrough, you'll show students how to use
React to create stateful, class-based components.

## For your review

<details>
<summary>Learning objectives</summary>
<div style="background-color: white; padding: 1em 1em 48px 1em; border: 1px solid var(--gray)">

After this presentation, the students should be able to

* Explain a React class component
* Explain how to use Docker to have a React development
  environment

</div>
</details>

<details>
<summary>Preparation</summary>
<div style="background-color: white; padding: 1em 1em 48px 1em; border: 1px solid var(--gray)">

* Know some React
* Know more React
* Really, just know all the React

</div>
</details>

<details>
<summary>Tools</summary>
<div style="background-color: white; padding: 1em 1em 48px 1em; border: 1px solid var(--gray)">

You'll need

* Visual Studio Code
* Docker
* Google Chrome
* [React DevTools for Google Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

</div>
</details>

## Set up

* Create a directory for what you're about to do
* Create a Dockerfile with the following content

  ```Dockerfile
  # Use the latest version of Node.js
  FROM node:latest

  # Use the /app directory as the work directory
  WORKDIR /app
  ```

* Build the image.

  ```sh
  docker build . -t react-docker
  ```

* Run a container from the image

  ```sh
  docker run -it -v "$(pwd):/app" -p 3000:3000 react-docker bash
  ```

* Create and start a React application

  ```sh
  npx create-react-app example
  cd example
  npm start
  ```

* Open your browser

  <http://localhost:3000>

## Orient the students

* Where you're at
  * You have a new React application
* Where you're going
  * You're going to show them how to work with class-based
    React components
* Why this is important
  * Some components need state
  * This is especially true for components that have forms
  * React is the **most** popular front-end language
  * This is a big thing for the job market

## Create a new Form component

* Create a new file named _Form.js_
* In it, add the following code

  ```jsx
  import React from 'react';

  class Form extends React.Component {
    render() {
      return (
        <p>My form</p>
      );
    }
  }

  export default Form;
  ```

* Talk about the inheritance that provides functionality
  for stateful components
* Talk about the `render` method that returns the JSX

## Use the new Form component

* In _App.js_, import the `Form` component
* Replace the default JSX with the `Form` component

  ```jsx
  import Form from "./Form";

  function App() {
    return (
      <Form />
    );
  }

  export default App;
  ```

* Show that it works

## Add a form

* Add a form to the `Form` component

  ```jsx
  import React from 'react';

  class Form extends React.Component {
    render() {
      return (
        <form>
          <div>
            <input placeholder="text" type="text" />
          </div>
          <div>
            <input placeholder="date" type="date" />
          </div>
          <div>
            <input placeholder="email" type="email" />
          </div>
          <div>
            <textarea placeholder="long text"></textarea>
          </div>
          <div>
            <select>
              <option value="1">First option</option>
              <option value="2">Second option</option>
              <option value="3">Third option</option>
            </select>
          </div>
        </form>
      );
    }
  }

  export default Form;
  ```

* Point out the trailing slashes in for the `input` tags
* Show the ugly form in the browser on save

## Open dev tools

* Open the React Components tab in the dev tools
* Show them the `Form` component in there
* Click on it show them information about it

## Capture events from the text input

* Show them you can type in the text `input`
* Tell them that you cannot use `document.getElementById`
  for the `input` because React may choose to change it at
  any time
* Tell them you need to use an event handler
* Add `onChange` handler to the text `input`

  ```jsx
  <input onChange={this.textChanged} placeholder="text" type="text" />
  ```

* Create a method named `textChanged` that `console.log` the
  parameter

  ```javascript
  class Form extends React.Component {
    textChanged(event) {
      console.log(event);
    }

    render() {
    ...
  ```

* Switch over to the Console and show them that an event
  occurs for each key press
* Open an event and show them the `target` property is the
  `input`
* Change the `console.log` to read like this

  ```javascript
  console.log(event.target.value);
  ```

* Type, again, to see the value of the form field

## Update state of the component

* In the `textChanged` event, set the state of the component

  ```javascript
  textChanged(event) {
    console.log(event.target.value);

    this.setState({ text: event.target.value });
  }
  ```

* Refresh the page
* Type in the field
* See errors in Console
* Explain that JavaScript has a problem with using methods
  as functions
  * Point to `onChange={this.textChanged}` in the JSX
* Explain that Python does not have the problem
* Explain there are many ways to fix this but the most
  common approach is to use the `bind` method
* Add bound function in constructor

  ```javascript
  class Form extends React.Component {
    constructor(props) {
      super(props);
      this.textChanged = this.textChanged.bind(this);
    }

    textChanged(event) {
      ...
  ```

* Refresh the page
* Type, again with no error
* Switch to React Components tab and show state of `Form`
  component
* Type some more and watch state change

## Talk about `this`

You're going to get questions about `this`, so just work
through them.

## Talk about `setState`

Explain that `setState` **merges** the dictionary that
you're passing in with the current state. It does **not**
replace it.

## Add event handlers to other form elements

* Show how the `onChange` event works for all of the
  different types of form elements

## Handle submit

* Add `onSubmit` handler to the `form` tag
* Do the `event.preventDefault()` in it to prevent the form
  from submitting
* Use `console.log` to show the state of the component

  ```javascript
  console.log(this.state);
  ```

* Explain that you can use this data to create `fetch` calls
  to POST the data to an API endpoint
