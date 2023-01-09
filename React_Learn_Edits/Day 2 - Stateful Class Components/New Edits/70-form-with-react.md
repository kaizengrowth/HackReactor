---
Type: Lesson
UID: 6b6c52ee-2be6-4346-a847-ebcc59b12ad8
DefaultVisibility: hidden
---

# Finish the project

Now that you've been able to finish one form, all forms are
basically the same. Do the same thing that you just did for
the `Location` form, but now for the `Conference` model.

Start off by commenting out the `LocationForm` component.

```jsx
function App(props) {
  if (props.attendees === undefined) {
    return null;
  }
  return (
    <>
      <Nav />
      <div className="container">
        {/* <LocationForm /> */}
        {/* <AttendeesList attendees={props.attendees} /> */}
      </div>
    </>
  );
}
```

Then, complete the same steps that you just did, but for the
form in _new-conference.html_ and its associated JavaScript
in _new-conference.js_. You'll make a `ConferenceForm` class
component, move the HTML and associated JavaScript into its
`render` and `componentDidMount` methods, write change
handlers for each of the form fields using the `.bind` in
the constructor for each, and creating submit handler.

![conference form in React](../../images/conference-go-create-conference-in-react.png)

Be very careful with the data that you submit. Like Lina
showed us, make sure the property names are what the API
expects when you create the POST request. If you end up
getting an error on your submissions, go to the Network tab
in the Developer Tools, click the red entry that has an
error, then click the Preview tab. You can see the Yellow
Page of Sadness that is returned.

![yellow page of sadness](../../images/submission-errors.png)

Once you have that done, do the same for the attendee
sign-up form in _attend-conference.html_ and
_attend-conference.js_. A couple of things to note when you
do this form:

* Do not worry about getting the blue background. We'll fix
  that when we work on single-page applications.
* Copy the _logo.svg_ from the _ghi/images/logo.svg_ to
  _ghi/app/public_ and the `src` to be `src="/logo.svg"`.
* Think about how you can show and hide the loading icon and
  the conference list drop down. You can make this decision
  in the `render` method. What are the HTML classes for the
  two components if the list of conferences has no entries?
  What if the list has one or more entries? This is a hard
  challenge because we haven't come up against this, yet.
  There are hints at the bottom.

![sign-up form](../../images/react-attendee-sign-up-form.png)

* **Stretch goal**: Add a Boolean value in the component
  state to show the success message on a valid form
  submission. Do the same type of HTML class determination
  that you did for showing and hiding the loading icon and
  dropdown list.

![stretch goal](../../images/form-stretch-goal.png)

<details>
<summary>Deciding classes based on data</summary>

What if your `render` method started off like this?

First, set the classes to what they should be when the page
loads. Then, once the list of conferences loads, change the
classes to what they should be to show the dropdown and hide
the loading icon.

```jsx
let spinnerClasses = // what could go here?
let dropdownClasses = // what could go here?
if (this.state.conferences.length > 0) {
  spinnerClasses = // what should be here?
  dropdownClasses = // what should be here?
}

return (
  <div className="my-5">
    <div className="row">
  // ...
```

</details>
<details>
<summary>How to use the classes in the JSX</summary>

Assuming you used the names of the variables in the last
hint, you can use the `spinnerClasses` variable like this
to put the class names HTML for the loading icon.

```jsx
<div className={spinnerClasses} id="loading-conference-spinner">
```

</details>

<details>
<summary>More about deciding classes</summary>

If you look at the original HTML, the loading icon started
off with the classes `"d-flex justify-content-center mb-3"`.
The dropdown started off with the classes `"form-select
d-none"`.

Here's what that could look like.

```javascript
let spinnerClasses = 'd-flex justify-content-center mb-3';
let dropdownClasses = 'form-select d-none';
if (this.state.conferences.length > 0) {
  spinnerClasses = // what should be here?
  dropdownClasses = // what should be here?
}
```

</details>
<details>
<summary>Yep. Need a little more.</summary>

Here's what the full HTML class decision could look like.

```javascript
let spinnerClasses = 'd-flex justify-content-center mb-3';
let dropdownClasses = 'form-select d-none';
if (this.state.conferences.length > 0) {
  spinnerClasses = 'd-flex justify-content-center mb-3 d-none';
  dropdownClasses = 'form-select';
}
```

</details>
