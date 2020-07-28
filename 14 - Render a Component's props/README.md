# Render a Component's props

You just *passed* information to a component’s `props` object!

You will often want a component to *display* the information that you pass.

Here’s how to make a component display passed-in information:
    1. Find the *component* class that is going to receive that information.
    2. Include `this.props.name-of-information` in that component class’s *render* method’s `return` statement.