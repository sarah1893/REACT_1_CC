# Create a Component Instance

`MyComponentClass` is now a working component class! It’s ready to follow its instructions and make some React components.

So, let’s make a React component! It only takes one more line:

```
<MyComponentClass />
```

To make a React component, you write a *JSX element*. Instead of naming your JSX element something like `h1` or `div` like you’ve done before, give it the same name as a component class. Voilà, there’s your *component instance*!

JSX elements can be either HTML-like, or component instances. JSX uses capitalization to distinguish between the two! That is the React-specific reason why component class names must begin with capital letters. In a JSX element, that capitalized first letter says, “I will be a component instance and not an HTML tag.”

# Render A Component

You have learned that a component class needs a set of instructions, which tell the component class how to build components. When you make a new component class, these instructions are the body of your class declaration:

```
class MyComponentClass extends React.Component
{ // everything in between these curly-braces is instructions for how to build components

  render() {
    return <h1>Hello world</h1>;
  }
}
```

This class declaration results in a new component class, in this case named `MyComponentClass`. `MyComponentClass` has one method, named `render`. This all happens via standard JavaScript class syntax.

You *haven’t* learned how these instructions actually work to make components! When you make a component by using the expression `<MyComponentClass />`, what do these instructions do?

Whenever you make a component, that component inherits all of the methods of its component class. `MyComponentClass` has one method: `MyComponentClass.render()`. Therefore, `<MyComponentClass />` also has a method named `render`.

You could make a million different `<MyComponentClass />` instances, and each one would inherit this same exact `render` method.

This lesson’s final exercise is to render your component. In order to *render* a component, that component needs to have a method named `render`. Your component has this! It *inherited* a method named `render` from `MyComponentClass`.

Since your component has a render method, all that’s left to do is call it. This happens in a slightly unusual way.

To call a component’s `render` method, you pass that component to `ReactDOM.render()`. Notice your component, being passed as `ReactDOM.render()`‘s first argument:

```
ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
);
```

`ReactDOM.render()` will tell `<MyComponentClass />` to call its render method.

`<MyComponentClass />` will call its render method, which will return the JSX element `<h1>Hello world</h1>`. `ReactDOM.render()` will then take that resulting JSX element, and add it to the virtual DOM. This will make “Hello world” appear on the screen.