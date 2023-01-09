---
Type: Lesson
UID: 3735c95c-79f3-4656-9912-5645ccc8c43e
DefaultVisibility: hidden
---

# A Long Weekend

You left work last week feeling a little behind the curve.
That evening, you texted your teammate about your
"adventures" in programming React with Malik. They texted
back that they'll see you Monday to pair with you some 
more. While you felt like you learned some stuff
while pairing with Malik, you also felt like you were missing
some pretty big things.

The feeling finally got to you Sunday afternoon. You spent
some time going through the React tutorial. There were lots
of things in there that felt new, like really new. But you
read as much as you could.

You walk into the office later than usual this morning.
Your time with the React tutorial left you feeling like
you'd just eaten a whole plate of spaghetti, carb overload.
When the alarm when off, you snoozed it more times than you
care to remember. But you're feeling a little more
prepared to work with Malik. For being a back-end
programmer, he sure did seem to get the whole front-end
thing.

It's just about time for the stand-up meeting. You put down
your laptop bag and head over to the Scrum board where the
team is starting to congregate. You see your teammate and
smile, wave. They walk around the group and stand near you.
"Hey, how're you feeling?" you ask.

"Better. So much better. It was not a fun couple of days."
They smile.

"I'm so sorry. I'm glad you're feeling better."

When stand-up begins, Evander asks questions about what
everyone did on Friday, what each person plans to do today,
and if there are any blockers. You notice Malik isn't in
the group and glance over toward his desk. He's sitting
there on the phone. _Missing stand-up_, you think. _That
must be an important phone call._

When it gets to you, you say, "Malik and I created the
attendees list last week with", you pause for emphasis,
"**React**." You emphasize on the word. Your team gives
you a brief round of good-natured applause. "We're exactly
one day ahead of schedule with the React implementation.
Today, I planned on refactoring one of the forms into
React. I don't have any blockers that I know about."

Evander nods and moves some sticky notes on the Scrum board.
They look at your teammate standing next to you and they
shrug. "I was sick," your teammate says. "Thank goodness, I
feel better now. I'm not sure who I'm pairing with today."

While the rest of the group gives their status, Malik
walks up and positions himself in the circle. When it gets
to him, he says, "I just got off the phone with the video
conference platform support team. We have a fix!" The team
makes some sounds of celebration. "Today, I'm going to work
on integrating their new, fixed API into our code." He
shoots you a slightly remorseful look. "I'm not going to be
able to pair with you today." You nod amidst mixed
emotions.

Evander looks at your teammate. "You ready to get back into
things and do some React?"

"Sure?" They look at you. You nod. "Yeah," they continue,
"I'm on it."

"Great!" Evander says.

The stand-up meeting concludes pretty quickly after that.
You ask your teammate, "This is a dumb question. Did you
read anything about React while you were sick?"

They laugh. "No. Sorry. I'm going to be the apprentice in
this relationship today."

You laugh. "Well, it'll be the clueless leading the
helpless then!" They laugh with you. "Okay, see you at your
desk in a couple of minutes?"

"Sure."

You head over to your desk, grab your notebook, make sure
all of the code is committed and pushed, and take a deep
breath. You examine your feelings: there's the nervousness
of the unknown, the happiness of having your teammate back,
the anxiety of the pressure of your development deadline,
and the urge to have a quick snack. Your stomach reminds you
that you haven't had any food today. _Well, I can fix one of
these things_, you think as you head to the café.

You grab a drink and a snack from the shelf. "Can I ask you
a question?"

You turn around and see Lina, the intern, with a hopeful
face standing a little too close to you. Lina always
seems to stand too close to people. You take a little step
back and say, "What's up, Lina?"

"Well, I was wondering if I could pair with you both today.
I guess that's a triple. I was wondering if I could triple
today, so that I could learn some React, too? I was hoping
to be able to learn it, and this is a good time since you're
doing it?"

In your mind, you think about the deadlines that you're on.
You weigh that with not really fully comprehending React as
it is. Adding that you're now the "lead" on React, having
someone else along could prevent you from making the
end-of-week code check-in. "You don't know any React?"

"No," she says. "But I do know JavaScript. Pretty well,
actually."

_Why didn't they get Lina to do this, then?_ you grumpily
think to yourself. _Because she's an intern, that's why._
You chide yourself for your irritable reaction. "Go check
with Evander and see if it's okay with them."

"I already asked them."

You take a moment to reflect on your feelings. You come to
the conclusion that having a third person along for this
ride probably won't be too bad. And Lina says she knows
JavaScript. "Yeah, okay, come on."

Lina follows you over to your teammate's desk. "Lina's going
to join us. She knows JavaScript."

"That's great! Thanks for helping out, Lina!"

"I'm really happy to be working on some code with the two of
you."

You and your teammate smile at Lina's enthusiasm. "Pull up
a chair," you say as you take a seat next to your teammate. Lina
wanders off to find a chair. "I hope this is okay with you."

"No worries," your teammate replies. "Lina and I did some
work together last month. It was fun. She made the project
more enjoyable."

You nod as Lina rolls a chair to the other side of your
teammate's desk and plops down. "This is great! Thank you
both, again."

Your teammate has already pulled the latest changes from the
repository and brought up the code. You go through the code
explaining what you and Malik previously did. You explain
the JSX code as best as you can. You show them Malik's
drawing of how attributes on what looks like a tag become
properties on the `props` object passed to the function.

"From what I've read on the React Web site over the weekend,
Malik and I built what's called a 'stateless' component
because it's just a function. There's another kind of
component called a 'stateful' component that you use
JavaScript classes for. They have 'state', just like a
Python class does. From the examples I saw, I think
that we need to use a 'stateful' component to create a
form."

Both your teammate and Lina ask nearly at the same time,
"Why?"

"That's a great question. Here's what I think I figured
out." You ask your teammate to open the JavaScript file
_new-location.js_. "You see, inside here, we're using the
`FormData` object to read the data from the form." They both
nod. "When we do the React version of this, we won't be
able to select the form by its id. That's just not the way
React works."

They both sit there in silence for a moment, letting that
statement sink in. Lina's the first to break the silence.
"Then how does React work?"

"Let's go over here to the whiteboard," you say. You grab a
couple of different colored markers. "This is what we do
when we write our own HTML and JavaScript." You draw a
diagram on the whiteboard:

![vanilla js and html](../../images/vanilla-js-get-form-data.png)

"We're in complete control of the HTML and JavaScript with
separate files for each. The HTML shows up in the browser,
someone types some stuff into the form, then submits it. Our
JavaScript gets the form by its id, listens for the submit
event, uses the form object to make a FormData object, then
we use that in our HTTP request."

You draw another diagram on the board:

![react data cycle](../../images/react-data-lifecycle.png)

"From as far as I can tell, React is totally in charge of
the HTML. It creates the HTML based on the data that we give
it, or some default data. For React stateless components,
that's something that we feed to it. In the case of the
stateful components," here you point to the word "state" in
the diagram, "it's based on whatever is stored in the
component itself."

You point to the green arrow. "React takes that state and
renders it to HTML. React is totally in charge now. We
know the HTML that it will produce, because we specified it
in the render method with that weird JSX stuff. But, React
is in charge of it. It can do whatever it wants with that
HTML. We're not supposed to do 'getElementById'."

You point to the red arrow and the first label. "Instead, we
can listen for when a person types into the input boxes.
That's a change in the data. We use that change to update
the state of the component, which causes it to call the
'render' method, again, which updates the HTML."

Your teammate and Lina look at you with confused looks on
their faces. "Yeah, I know," you admit with a touch of
confusion in your own voice. "Maybe if we just try typing
it out, we can all get a better understanding of it."

Lina takes out her phone and snaps a picture of your
diagrams. Then, you three head back over to your teammate's
desk to work through this new concept.
