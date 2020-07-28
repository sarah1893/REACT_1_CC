# Call this.setState from Another Function

The most common way to call `this.setState()` is to call a custom function that wraps a `this.setState()` call. .`makeSomeFog()` is an example:

```
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = { weather: 'sunny' };
    this.makeSomeFog = this.makeSomeFog.bind(this);
  }

  makeSomeFog() {
    this.setState({
      weather: 'foggy'
    });
  }
}
```

Notice how the method `makeSomeFog()` contains a call to ``this.setState()``.

You may have noticed a weird line in there:

```
this.makeSomeFog = this.makeSomeFog.bind(this);
```

This line is necessary because ``makeSomeFog()``‘s body contains the word ``this``. We’ll talk about it more soon!

Let’s walk through how a function wrapping ``this.setState()`` might work in practice. In the code editor, read **Mood.js** all the way through.

Here is how a ``<Mood />``‘s state would be set:

    1. A user triggers an *event* (in this case a click event, triggered by clicking on a ``<button></button>``).

    2. The event from Step 1 is being listened for (in this case by the ``onClick`` attribute on line 20).

    3. When this listened-for event occurs, it calls an *event handler* function (in this case, ``this.toggleMood()``, called on line 20 and defined on lines 11-14).

    4. Inside of the body of the *event handler*, ``this.setState()`` is called (in this case on line 13).

    5. The component’s ``state`` is changed!

Due to the way that event handlers are bound in JavaScript, ``this.toggleMood()`` loses its this when it is used on line 20. Therefore, the expressions ``this.state.mood`` and ``this.setState`` on lines 7 and 8 won’t mean what they’re supposed to… *unless* you have already bound the correct ``this`` to ``this.toggleMood``.

That is why we must bind ``this.toggleMood`` to this on line 8.

For an in-depth explanation of this kind of binding trickery, begin with [the React docs](https://facebook.github.io/react/docs/handling-events.html). For the less curious, just know that in React, whenever you define an event handler that uses ``this``, you need to add ``this.methodName = this.methodName.bind(this)`` to your constructor function.

Look at the statement on line 12. What does that do?

Line 12 declares a ``const`` named ``newMood`` equal to the opposite of ``this.state.mood``. If ``this.state.mood`` is “good”, then ``newMood`` will be “bad,” and vice versa.

A ``<Mood />`` instance would display “I’m feeling good!” along with a button. Clicking on the button would change the display to “I’m feeling bad!” Clicking again would change back to “I’m feeling good!”, etc. Try to follow the step-by-step walkthrough in **Mood.js** and see how all of this works.

One final note: you can’t call ``this.setState()`` from inside of the render function! We’ll explain why in the next exercise.

# this.setState 

Automatically Calls render
There’s something odd about all of this.

Look again at Toggle.js.

When a user clicks on the ``<button></button>``, the ``.changeColor()`` method is called. Take a look at .``.changeColor()``‘s definition.

.``.changeColor()`` calls ``this.setState()``, which updates `this.state.color`. However, even if `this.state.color` is updated from green to yellow, that alone shouldn’t be enough to make the screen’s color change!

The screen’s color doesn’t change until Toggle renders.

Inside of the render function, it’s this line:

```
<div style={{background:this.state.color}}>
```
that changes a virtual DOM object’s color to the new ``this.state.color``, eventually causing a change in the screen.

If you call .``.changeColor()``, shouldn’t you then also have to call .render() again? .changeColor() only makes it so that, the next time that you render, the color will be different. Why can you see the new background right away, if you haven’t re-rendered the component?

Here’s why: Any time that you call ``this.setState()``, ``this.setState()`` AUTOMATICALLY calls ``.render()``. as soon as the state has changed.

Think of ``this.setState()`` as actually being two things: ``this.setState()``, immediately followed by ``.render()``.

That is why you can’t call ``this.setState() ``from inside of the ``.render()``. method! ``this.setState()`` automatically calls ``.render()``.. If ``.render()``. calls ``this.setState()``, then an infinite loop is created.