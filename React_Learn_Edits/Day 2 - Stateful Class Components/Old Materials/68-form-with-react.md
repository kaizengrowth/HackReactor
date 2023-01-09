---
Type: Lesson
UID: 03f0356c-39e1-4dd1-a981-5c77a2841af0
DefaultVisibility: hidden
---

# Saving Form State

"Now, we need to keep track of the state of the different
inputs," you say. "This is so when people type in the
different input fields, we can get the data into the state
of the component."

"Can I try to figure it out?" asks Lina.

Your teammate answers for you. "Sure, Lina. I'm going to go
get some more water while you do that."

Your teammate gets up and stretches their arms above their
head as they walk toward the café area. Lina types a search
into her phone and starts scrolling through the results.
She taps on a couple of links before her eyes squint in what
you interpret as concentration and, then, recognition. Lina
sits back in her chair and asks you, "It's the onChange
event handler, right?"

"You got it."

Her smile gets bigger.

Your teammate returns, sits, and looks expectantly at Lina.
"It's the onChange event handler," she says. Lina then asks
to add an `onChange` attribute to the `input` tag that
handles the location's name. Your teammate adds the code and
adds some new lines so everyone can easily see all of the
code.

```jsx
<input onChange="" placeholder="Name" required
       type="text" name="name" id="name"
       className="form-control" />
```

Lina says, "Instead of quotation marks, you should use curly
braces." The code is quickly updated.

```jsx
<input onChange={} placeholder="Name" required
       type="text" name="name" id="name"
       className="form-control" />
```

"Now," Lina says. "Um...." Her voice trails off as she looks
at the code on her phone. "Um, is it okay if you just look
at my phone and type what you see?"

"Sure," your teammate responds. Glancing between the phone
and the code on their screen, the first thing updated is
the content of the curly braces.

```jsx
<input onChange={this.handleNameChange} placeholder="Name" required
       type="text" name="name" id="name"
       className="form-control" />
```

Then, they create a new method named `handleNameChange` as
part of the class.

```javascript
class LocationForm extends React.Component {
  // constructor ...

  handleNameChange(event) {
    const value = event.target.value;
    this.setState({name: value})
  }

  // componentDidMount and render ...
}
```

"What's that event.target thing?"

Lina reads the page on the phone and says, after a moment of
figuring out what she's reading, "The event parameter is the
event that occurred. The target property on it is the HTML
tag that caused the event. So, in this case, the
event.target is the input for the location's name. Then, the
value property is the value in the input."

"Thanks!"

Lina holds the phone back up so the teammate can complete
their transcription. They add a line to the constructor of
the class component.

```javascript
class LocationForm extends React.Component {
  constructor(props) {
    super(props)
    this.state = {states: []};
    this.handleNameChange = this.handleNameChange.bind(this);
  }

  // handleNameChange, componentDidMount, and render ...
}
```

"What is **that**?" your teammate asks after finishing.

Lina says, "It's a hack."

Your teammate turns to her. "I'm listening."

You say, "Me, too."

"In JavaScript, you know about the this keyword, right?"

"Yes," both you and your teammate answer.

"Well, here's the deal. In JavaScript, if you have an object
and you refer to one of its methods like a property,
JavaScript forgets what object it came from."

You and your teammate look at her a little dumbfounded. You
say, "I'm not sure I understand. There's nothing like that
in Python."

"Right!" Lina says excitedly. "In Python, the self parameter
is always handled correctly by Python, passing in the value
of the object that it was bound to. JavaScript doesn't do
that. You can call any function with whatever value for the
'this' keyword you want!"

You and your teammate look at each other, then back at Lina.
"That seems like chaos," you say.

"It can be," admits Lina. "But, it can also be really
powerful. But, the key here is, if you want to use a method
in the class as an event handler, you have to do that 'bind'
thing in the constructor."

"Okay," says your teammate.

You nod. _JavaScript can be so weird_, you think.

"JavaScript can be pretty weird!" Lina says, happily.

Your teammate turns back to the screen and types in the
"Name" field. Lina asks to see the state, again, in the
React Components tab. All of you watch as letters are typed
into the "Name" field and the state is reflected to have
that value.

![updates in form and state](../../images/react-form-field-and-state-update.gif)

You all say some version of "That's pretty cool."

## Finish this step

For the three other form fields, room count, city, and
state, add change handlers in the same way you just did for
the `input` for the "Name".

You can see in the screenshot below that the values in all
four of the form inputs are now in the state of the form.

![all fields handled](../../images/react-update-form-fields.png)

Do the same steps for each of the three remaining fields.

1. Add an on `onChange` handler in the JSX for a method that
   will update the component state
1. Add a method that updates the component state in the same
   way that `handleNameChange` does
1. Do the `bind` thing in the constructor

<details>
<summary>For the room count</summary>

Here's how you could do it for the room count input. It'll
be **very** similar for the other two fields.

1. Add an on `onChange` handler in the JSX for a method that
   will update the component state

    ```jsx
      <input onChange={this.handleRoomCountChange} placeholder="Room count"
            required type="number" name="room_count" id="room_count"
            className="form-control" />
      ```

1. Add a method that updates the component state in the same
   way that `handleNameChange` does

    ```javascript
    handleRoomCountChange(event) {
      const value = event.target.value;
      this.setState({roomCount: value})
    }
    ```

1. Do the `bind` thing in the constructor

    ```javascript
    this.handleRoomCountChange = this.handleRoomCountChange.bind(this);
    ```

</details>
