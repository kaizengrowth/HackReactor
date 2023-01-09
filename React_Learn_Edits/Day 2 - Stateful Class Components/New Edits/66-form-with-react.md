---
Type: Lesson
UID: e1361ebe-c033-4c33-aaf5-e0fb10d425ba
DefaultVisibility: hidden
---

# Showing A Form

Your teammate asks, "How do we start?"

"I have a Docker command that can create a new React
environment for us." You start digging through your notes to
find the command that Malik shared with you when you're
interrupted by Lina.

"Can't we just use the existing React environment and build
a spa?"

You look at Lina, not quite sure you heard her correctly.
"Build a what?"

"A spa," she answers.

"I don't know what that is."

"Oh, sorry. A SPA," she says it now with stress and you can
almost see the uppercase letters, "is a single-page
application. It's a term for how to build front-end
applications like we're doing now."

You let out a little chuckle at the acronym conversation you
had with Malik. "Thanks for explaining that. Can you help
me understand more about that? And while we're all learning
together, can we make sure we don't use abbreviations that
others may not know?"

Lina blushes a little. "Sorry."

"No, please don't be sorry, Lina. It's just a way for all of
us to make sure that we're on the same page. Abbreviations
and acronyms that we all don't know can cause confusion."

Lina nods and says, "Okay. I get that." She clears her
throat a little and sits up straighter. You can nearly
imagine her doing this in a classroom in response to an
instructor's prompt. "A single-page application, or SPA,
uses just a single HTML file to show all of the graphical
human interface based on what you're doing. It shows and
hides different pieces of HTML based on if you're entering a
form to create a new location, or trying to look at the list
of attendees." Her spine curves a little as she stops her
explanation. "I built one with some friends in a front-end
framework called Vue.js. But from what I understand, it
works in React, too."

"Okay," you reply. "Let's reuse what we have now? I'm not
sure how to turn things on and off..." You look at your
teammate who just shrugs. "How about if we just reuse the
same environment, and after we get one or more forms
working, we can figure out how to switch things on and off?"

"Great!" Lina gushes.

"All right, we have our direction. Let's get to work. Since
we're going to build a single-page application," you say and
Lina does a very little dance in her chair, "I think we
should change the names of some things so that they're
properly named."

### !callout-info

## Note to the reader

If you have docker-compose running, please stop your
services now.

### !end-callout

You ask your teammate to rename the _ghi/attendees_
directory to _app_ because "it's going to be a whole app and
not just the attendees stuff."

You ask your teammate to open the _docker-compose.yml_ file
and ask them to rename the service that runs the React
application. "Please just name it 'react'. Then, update the
path for the volumes to point to the renamed directory,
please." You look at the YAML after they're done typing:

```Dockerfile
react:
  image: node:latest
  command: npm start
  working_dir: /app
  volumes:
    - ./ghi/app:/app
  environment:
    - HOST=0.0.0.0
    - PORT=3001
  ports:
    - "3001:3001"
```

**Note to the Windows reader**: If you're on Windows, yours
will look slightly different. Update your section to have
the new service name and new volumes entry. Make sure you
leave your environment variables the same.

"I guess that looks correct? Let's try it out and see if we
have any bugs!" Your teammate deletes all of the containers,
builds the images, and brings up the services.

```sh
docker container prune -f
docker-compose build
docker-compose up
```

All of you watch the terminal output and the Docker Desktop
client to see if there are any errors in the start up. You
ask your teammate to show the logs for the service that
now contains "-react-" in it. You look at the logs and see
the service come up successfully. You ask your teammate to
open a browser tab to localhost:3001. You all see the list
of attendees appear. You can feel the mounting excitement in
the group.

Your teammate adds, commits, and pushes the changes. "Why did
you do that?" asks Lina.

Your teammate responds, "So that we have a point to go back
to in case something goes horribly awry."

You laugh at their dire words. "Let's see if we can make
something **not** go horribly awry. If it's okay with the
both of you, I'd like to just try to get a form to work
without having to mess with the SPA stuff, just yet." They
both nod in assent. "If that's the case, let's refactor the
list of attendees into its own function." You stop and
correct yourself. "Sorry, its own **component**. That's what
React would call it."

You guide your teammate through the steps:

1. Creating a new file in _ghi/app/src_ named
   _AttendeesList.js_
1. Creating a new `AttendeesList` function component in there
   and exporting it as the "default"
1. Moving the `table` JSX and its contents from _App.js_ to
   the new function
1. Importing the  `AttendeesList` from the
   _AttendeesList.js_ module
1. Using the new `AttendeesList` function component in the
   `App` function component

As the work is being done, all three of you keep your eyes
on the browser and the console to see if there are any
errors. When one appears, each of you carefully read it and
try to troubleshoot the issues. Eventually, the React
application is working, again, and the Web page looks
exactly like it did before.

## Finish this step

Follow the steps above to refactor the list of attendees
into its own React function component.

This work is similar to what you did when you created the
`Nav` function component and used it in your `App` function
component.

The major difference is that you'll have to pass the
attendees data from the `App` component to the new
`AttendeesList` component to get it to properly render. Look
in _App.js_ to remind you how to pass data to a component.

If you get stuck along the way, here are some things to help you:

<details>
<summary>Step 2</summary>

This is what the empty `AttendeesList` function component
could look like:

```jsx
function AttendeesList() {

}

export default AttendeesList;
```

</details>
<details>
<summary>Step 3: No more table</summary>

Removing the `table` from the `App` function component can
make it look pretty empty now.

```jsx
import Nav from './Nav';

function App(props) {
  if (props.attendees === undefined) {
    return null;
  }
  return (
    <>
      <Nav />
      <div className="container">

      </div>
    </>
  );
}

export default App;
```

</details>
<details>
<summary>Step 3: Paste the table</summary>

The `AttendeesList` function component now should have the
`table` JSX in it. Make sure to have a `props` parameter!

```jsx
function AttendeesList(props) {
  return (
    <table className="table table-striped">
      <thead>
        <tr>
          <th>Name</th>
          <th>Conference</th>
        </tr>
      </thead>
      <tbody>
        {props.attendees.map(attendee => {
          return (
            <tr key={attendee.href}>
              <td>{ attendee.name }</td>
              <td>{ attendee.conference }</td>
            </tr>
          );
        })}
      </tbody>
    </table>
  );
}

export default AttendeesList;
```

</details>
<details>
<summary>Step 4: Import the new component</summary>

Just a normal `import` statement for JavaScript.

```javascript
import AttendeesList from './AttendeesList';
```

</details>
<details>
<summary>Step 5: Use the new component</summary>

```jsx
import Nav from './Nav';
import AttendeesList from './AttendeesList';

function App(props) {
  if (props.attendees === undefined) {
    return null;
  }
  return (
    <>
      <Nav />
      <div className="container">
        <AttendeesList attendees={props.attendees} />
      </div>
    </>
  );
}

export default App;
```

</details>
