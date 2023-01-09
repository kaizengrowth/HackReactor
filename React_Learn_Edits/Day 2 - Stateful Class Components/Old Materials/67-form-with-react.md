---
Type: Lesson
UID: 865e6ba5-d49a-4635-b9dc-2b017a6928d9
DefaultVisibility: hidden
---

# Loading The Form

"Let's now just hide the new component." You encourage your
teammate to comment out the new component in the _App.js_
function component.

```jsx
{/* <AttendeesList attendees={props.attendees} /> */}
```

"That way, when we are ready to show and hide it, we'll
just uncomment it with whatever other code we need." You
pause, thinking about what's next. "Let's recreate the
form to add locations as a React component. But, this time,
we'll create a class component which will hold its state."

You ask your teammate to create a new file named
_LocationForm.js_ in _ghi/app/src_. Then, you ask them to
type the following.

```jsx
import React from 'react';

class LocationForm extends React.Component {
  render() {
    return (
      <p>A location form</p>
    );
  }
}

export default LocationForm;
```

Then, you ask them to import it into the _App.js_ file and
put it above the commented out `AttendeesList` component.

```jsx
import Nav from './Nav';
import AttendeesList from './AttendeesList';
import LocationForm from './LocationForm';

function App(props) {
  if (props.attendees === undefined) {
    return null;
  }
  return (
    <>
      <Nav />
      <div className="container">
        <LocationForm />
        {/* <AttendeesList attendees={props.attendees} /> */}
      </div>
    </>
  );
}

export default App;
```

The Web page updates and all of you see the message "A
location form" on the screen. "Looks like that we've got it
set up correctly," you say.

You ask your teammate to go back to the _LocationForm.js_
file so that you can explain. "We're creating a class, here.
That means that it can have state when it gets created, just
like our model classes in Django. React takes care of
creating the instance of that class for us. Thanks, React."

Lina echoes you more enthusiastically, "Thanks, React!"

You smile. "All React component classes need a render
method. That's the method that returns the JSX for the
component." You point to where the `p` tag is. "That JSX
will get turned into an actual paragraph tag by React."
You pause to collect your thoughts. "Let's go ahead and copy
the HTML from the new location form into this component."

Your teammate grabs all of the HTML inside the `div
class="container"` from _new-location.html_ and pastes it
over the `p` tag in the `render` method of the
`LocationForm` component.

<!-- markdownlint-disable MD013 -->
```jsx
class LocationForm extends React.Component {
  render() {
    return (
      <div class="row">
        <div class="offset-3 col-6">
          <div class="shadow p-4 mt-4">
            <h1>Create a new location</h1>
            <form id="create-location-form">
              <div class="form-floating mb-3">
                <input placeholder="Name" required type="text" name="name" id="name" class="form-control">
                <label for="name">Name</label>
              </div>
              <div class="form-floating mb-3">
                <input placeholder="Room count" required type="number" name="room_count" id="room_count" class="form-control">
                <label for="room_count">Room count</label>
              </div>
              <div class="form-floating mb-3">
                <input placeholder="City" required type="text" name="city" id="city" class="form-control">
                <label for="city">City</label>
              </div>
              <div class="mb-3">
                <select required name="state" id="state" class="form-select">
                  <option selected value="">Choose a state</option>
                </select>
              </div>
              <button class="btn btn-primary">Create</button>
            </form>
          </div>
        </div>
      </div>
    );
  }
}
```
<!-- markdownlint-enable MD013 -->

The Web page fills with an error when the file is saved. You
notice the red squiggly lines under the `input` tags and
call your teammate's attention to them. They hover their
mouse over the `input` tag and see the following warning.

```text
JSX element 'input' has no corresponding closing
tag. ts(17008)
```

Lina points to the same error message printed on the Web
page.

"Oh, that's right!" You shake your head. "I forgot about
this. Malik explained it to me. In HTML, we can have tags
that don't have close tags, like the input tag and the link
tag. But, in React, everything **has** to have a close tag.
Or, you put this slash at the end of it." You show your
teammate to change the `>` at the end of all three `input`
tags to `/>`. With each forward slash they put near the end
of the tag, the red squiggly error indicators go away.

When all three are fixed, the form shows up in the browser
window. You ask your teammate to open up the Console in the
Developer Tools. All three of you see three errors. You ask
your teammate to scroll up to the first one.

```text
Warning: Invalid DOM property `class`. Did you mean
`className`?
```

"Right! Malik explained this one to me, too. Because our JSX
gets turned into JavaScript, we can't use the word 'class'
because that's a keyword in JavaScript. Instead, we have to
use 'className'. Can you change all of those for us?"

Your teammate nods and does a Find & Replace for the terms
`class="` to `className="`. When the file is saved, you ask
your teammate to refresh the page. Now, you see only two
errors. Again, you ask your teammate to scroll up to the
first one.

```text
Warning: Invalid DOM property `for`. Did you mean `htmlFor`?
```

### !challenge

* type: multiple-choice
* id: 17538d0d-97cf-4034-9661-fc4643ec3dde
* title: Make an educated guess

##### !question

Why do you think React wants us to change `for` to
`htmlFor` in the JSX?

##### !end-question

##### !options

* `for` can refer to both HTML and CSS
* `for` is a reserved keyword, like `class`
* `for` is not a good name for an attribute

##### !end-options

##### !answer

* `for` is a reserved keyword, like `class`

##### !end-answer

### !end-challenge

"I don't know about this one..., but if I had to guess, I'd
say it's the same kind of error. Just like 'class' is a
keyword in JavaScript, so is 'for', like for a for loop. It
looks like we need to change all of the 'for' attributes in
our labels to be 'htmlFor'."

Your teammate does the same kind of Find & Replace operation
to replace the `for` attributes with `htmlFor` attributes.
After the file is saved, you ask for a refresh. Now, there's
only one error in the Console. The three of you review it.

```text
Use the `defaultValue` or `value` props on <select> instead
of setting `selected` on <option>.
```

"I don't know anything about this. Any guesses?"

Your teammate says, "Just remove the 'selected' attribute
from the option tag in the HTML?" You shrug and Lina nods.
Your teammate removes the attribute from the `option` tag,
then refreshes the page.

"No more errors," says Lina, with excitement.

Your teammate tries submitting the form but can't because of
the required fields. "Looks like the form is working. What's
next?"

"I think we should load the states in there for the
dropdown. Otherwise, we'll never be able to submit the
form."

"Okay. How do I do that?"

"I don't know? Let's see if we can figure this out?" Your
teammate opens a new tab to do an Internet search while Lina
and you pull out your phones. You do searches for a while,
reading results.

Lina sounds frustrated when she says, "All I see are these
things called hooks. We're not doing hooks, right?"

"No? I've seen those, too. They say we can't use hooks with
class components. We're doing a class component, so no
hooks."

After another minute, your teammate says, "I think I've got
it. There's a method called componentDidMount that we can
use to set up any kind of data that we need, like getting
data for the states."

"Let's try it," you say. "The JavaScript to fetch the states
is in the old location form JavaScript file."

Your teammate goes to the JavaScript file _new-location.js_
copies the pertinent JavaScript, creates a
`componentDidMount` method for the `LocationForm` class,
and pastes the JavaScript in there.

```javascript
class LocationForm extends React.Component {
  componentDidMount() {
    const url = 'http://localhost:8000/api/states/';

    const response = await fetch(url);

    if (response.ok) {
      const data = await response.json();

      const selectTag = document.getElementById('state');
      for (let state of data.states) {
        const option = document.createElement('option');
        option.value = state.abbreviation;
        option.innerHTML = state.name;
        selectTag.appendChild(option);
      }
    }
  }

  // render method...

}
```

When they save it, an error appears about using the `await`
keyword in a non-`async` function. Your teammate quickly
fixes that by adding `async` in front of
`componentDidMount`. They refresh the page and the `await`
error goes away. Your teammate clicks on the dropdown and
the states are there.

"I know," you say. We could do the getElementById thing.
But, that's not the way we're **supposed** to do it. We need
to introduce state for our component."

"How do we do that?" asks Lina.

"In our Django model classes, state is represented by the
properties of the class. Like, a specific instance of the
Location model has a name, a city, the number of
rooms at the location, etc. The Conference model has a name,
when it starts, when it ends, the description of the
conference, etc. State is the data inside the instance of
the class at any given time."

You drink a little bit of water. _This sure is a lot of
talking_, you think.

"In React class components, each component has its own
property called state that contains the data for the
component. Class components also have a method named
setState which takes whatever value you pass in and
**merges** it with the current state." Both Lina and your
teammate look a little lost, and you can't really blame
them.

"We've seen how the render method returns the JSX that React
will turn into the HTML, right?" They both nod. "We can use
whatever data is stored in the component when we render,
which is what we're about to do with that array of U.S.
states that we just got back from the API call. We're going
to take that array and put it into the state of the
component, the component state.

"The problem is, when we change the data that is inside the
component, we need a way to tell React that we're changing
the data. Because it's just JavaScript under the covers, it
can't figure that out. So, we use the setState method which
does two things. First, it adds whatever data we have to the
component's internal data that we can use in the render
method. Then, it tells React that it should update the HTML
in our component.

"Let's try it out and see if it makes more sense with code."

You ask your teammate to get rid of all of the lines of
JavaScript after the `const data` that have to do with
creating `option` elements and updating the `selectTag`.
That leaves just this.

```javascript
class LocationForm extends React.Component {
  componentDidMount() {
    const url = 'http://localhost:8000/api/states/';

    const response = await fetch(url);

    if (response.ok) {
      const data = await response.json();

    }
  }

  // render method...

}
```

They save the JavaScript and click on the dropdown, again.
There are no states in the list, this time.

"Now, we want to add that data to the state of the
`LocationForm` component. Please type this.setState and pass
in a dictionary that has the key 'states' and data.states as
its value."

Your teammate types the following line after the `const
data` line to set the state of the component.

```javascript
this.setState({states: data.states});
```

You ask your teammate to install the [React Developer
Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)
from the Google Chrome Web store. They install it. You ask
them to check their Developer Tools to see if there's a
"Components" tab, now.

**Note to reader**: If you install this extension, you may
need to restart your browser to see the new tab in the
Developer Tools.

You have them click on the `LocationForm` entry in the
left side.

![LocationForm state](../../images/react-tools-location-form-state.png)

On the right, all three of you can see that the component's
state now contains an entry named `states` with an array of
values. "We can use the component state in our render
method."

You ask them to type the following code to "loop over" the
values in the `states` array inside the JSX in the `render`
method after the `option` tag.

```jsx
<select required name="state" id="state" className="form-select">
  <option value="">Choose a state</option>
  {this.state.states.map(state => {
    return (
      <option value={state.abbreviation}>
        {state.name}
      </option>
    );
  })}
</select>
```

While they're typing, you say, "It's really unfortunate that
we're using the state of the component to contain a list of
states, each one being a state. That's a lot of use of the
word 'state' where there's two different concepts."

"I think I can keep it straight," says Lina. You nod at her
with a smile.

When your teammate has finished typing the code and saved
the page, some new errors appear in the Console window. They
all read something like

```text
Cannot read properties of null (reading 'states')
```

"Oh, we had this problem with the function component, too,"
you say. "It's a timing issue. When the component first
loads, there is no array of U.S. states in the component's
state. When it tries to render the first time, the value of
'this.state.states' is empty. We have to give it a default
value. Can you add a constructor, please?"

Your teammate types a constructor at the top of the `class`.

```javascript
class LocationForm extends React.Component {
  constructor() {

  }

  // The componentDidMount and render methods...
}
```

"The constructor needs a props parameter," you say. Your
team member updates the code.

```javascript
class LocationForm extends React.Component {
  constructor(props) {

  }

  // The componentDidMount and render methods...
}
```

"Just like with inheritance in Python, we need to call the
constructor on the parent class. Can you do that with the
super keyword?" Your teammate adds that line to the
constructor.

```javascript
class LocationForm extends React.Component {
  constructor(props) {
    super(props)
  }

  // The componentDidMount and render methods...
}
```

"Okay, now we just need to add the default state. Just type
this.state equals a new dictionary with the states key and
an empty list."

```javascript
class LocationForm extends React.Component {
  constructor(props) {
    super(props)
    this.state = {states: []};
  }

  // The componentDidMount and render methods...
}
```

"Save it now?" When your teammate saves the file, the
form shows back up and the errors are now replaced with a
new one.

```text
Each child in a list should have a unique "key" prop.
```

"Right, we ran into this one, too, yesterday, me and Malik."

You explain the `key` property to them the way Malik did to
you. Then, you have them add the `key` property to the JSX
in the `render` method in a similar way to what you did for
the table rows in the `AttendeesList` function component.

## Finish this step

Can you make the error go away? You'll want to refresh the
browser every time you change the code. Sometimes, you will
fix the error, but you will still see it in the Console.
Refreshing the page will make sure old errors are cleared
out.

<details>
<summary>Adding the key</summary>

Since the abbreviation property is guaranteed to be unique
(see the `State` model class), you can safely use it as a
value for the `key` attribute that React so badly wants.

```jsx
{this.state.states.map(state => {
  return (
    <option key={state.abbreviation} value={state.abbreviation}>
      {state.name}
    </option>
  );
})}
```

</details>
