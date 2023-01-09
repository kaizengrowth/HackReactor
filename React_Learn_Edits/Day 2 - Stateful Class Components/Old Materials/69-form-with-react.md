---
Type: Lesson
UID: d9c23b77-687b-4bb4-bd6c-c2a9247150d9
DefaultVisibility: hidden
---

# Submitting The Form

"How do we submit the form," Lina asks?

"I'm going to guess that we use the same kind of event
handler, but onSubmit instead of onChange," you say.

"Where's the data come from?" your teammate asks. "From the
state?"

"I think so," you reply. "But, the way that we have it now,
we're going to have to change it a little bit."

"Why's that?" Lina asks.

"Look at the state. In there, the property is named
roomCount, camel case. The JSON that's expected is
room_count, snake case."

"That shouldn't be too much of a problem," Lina announces.
She asks your teammate to create a new method named
`handleSubmit` and do the same 'bind' thing in the
constructor for it.

```javascript
class LocationForm extends React.Component {
  constructor(props) {
    super(props)
    this.state = {states: []};
    this.handleNameChange = this.handleNameChange.bind(this);
    this.handleCityChange = this.handleCityChange.bind(this);
    this.handleRoomCountChange = this.handleRoomCountChange.bind(this);
    this.handleStateChange = this.handleStateChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleSubmit(event) {

  }

  // the rest of the class
}
```

"Okay," says Lina, "Create a copy of the state."

"I'm not sure how to do that," your teammate replies.

"No worries." Lina directs them to type the following.

```javascript
handleSubmit(event) {
  event.preventDefault();
  const data = {...this.state};
  data.room_count = data.roomCount;
  delete data.roomCount;
  delete data.states;
  console.log(data);
}
```

"What's that triple dot thing?" you ask.

"That copies all of the properties and values from
this.state into a new object. It's an easy way to make a
copy of objects in JavaScript. Then, we're creating a new
key named 'room_count' and setting it to the value of
'roomCount'. Then, we're deleting the keys 'roomCount' and
'states' because I'm guessing we don't want to send that
data to the server. It's just JavaScript object
manipulation."

"And, objects are like dictionaries, right?" you ask.

"Yes, that's right. They both can have keys and values in
them."

Then, Lina asks them to put the `onSubmit` event handler on
the `form` tag in the JSX.

```jsx
<form onSubmit={this.handleSubmit} id="create-location-form">
```

"Try filling out the form and submitting it?" Your teammate
fills out the data and clicks the "Create" button. In the
Console, the three of you see this, after your teammate
clicks on the little triangle.

```text
▼ {name: 'AZ PYCON', city: 'Tempe', state: 'AZ', room_count: '12'}
    city: "Tempe"
    name: "AZ PYCON"
    room_count: "12"
    state: "AZ"
```

"That seems to work!" you say while giving Lina a thumbs up.

"Thanks, she says.

You ask your teammate to grab the POST code from
_new-location.js_. They do, and add it to the `handleSubmit`
function. They fix a couple of variable names and end up
with this.

```javascript
async handleSubmit(event) {
  event.preventDefault();
  const data = {...this.state};
  data.room_count = data.roomCount;
  delete data.roomCount;
  delete data.states;
  console.log(data);

  const locationUrl = 'http://localhost:8000/api/locations/';
  const fetchConfig = {
    method: "post",
    body: JSON.stringify(data),
    headers: {
      'Content-Type': 'application/json',
    },
  };
  const response = await fetch(locationUrl, fetchConfig);
  if (response.ok) {
    const newLocation = await response.json();
    console.log(newLocation);
  }
}
```

They fill out the form, again, and submit it. This time,
everyone sees the data from the form and, then a moment
later, the data from the locations API. The three of you
give each other congratulations.

You see the form isn't cleared on successful save and say
so. "I remember seeing this. We need to set the state to
empty strings and use those values for the form elements."

You ask your teammate to add the following code to the end
of the `handleSubmit` function in the `if` block.

```javascript
  if (response.ok) {
    const newLocation = await response.json();
    console.log(newLocation);

    const cleared = {
      name: '',
      roomCount: '',
      city: '',
      state: '',
    };
    this.setState(cleared);
  }
```

Then, you ask them to add to each `input` and `select` tag
in the JSX a value attribute for set to the corresponding
value in the state.

* For the **Name** input, add `value={this.state.name}`
* For the **Room count** input, add
  `value={this.state.roomCount}`
* For the **City** input, add `value={this.state.city}`
* For the **State** dropdown, add `value={this.state.state}`

They add those into the JSX and refresh the page. Everything
loads fine. Then, they type in the "Name" field and a
warning pops up into the Console.

```text
Warning: A component is changing an uncontrolled input to be
controlled. This is likely caused by the value changing from
undefined to a defined value, which should not happen.
Decide between using a controlled or uncontrolled input
element for the lifetime of the component. More info:
https://reactjs.org/link/controlled-components
```

You let out a little gasp of frustration. You ask your
teammate to click on that link
<https://reactjs.org/link/controlled-components>. After
reading a moment, you see what the problem is. "OH! We have
to set an initial state for the input tags!"

You ask your teammate to change the constructor to provide
empty strings for the state properties for the input fields
in the form. They add some more code to the constructor so
it looks like this.

```javascript
class LocationForm extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      name: '',
      roomCount: '',
      city: '',
      states: []
    };
    this.handleNameChange = this.handleNameChange.bind(this);
    this.handleCityChange = this.handleCityChange.bind(this);
    this.handleRoomCountChange = this.handleRoomCountChange.bind(this);
    this.handleStateChange = this.handleStateChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  // The rest of the component
}
```

They refresh the page and try typing in the fields, again.
No warnings! No errors! Everything seems to be okay! And,
when the form is successfully submitted, it clears!

"Great work, everyone!" you say as you smile at Lina and
your teammate.
