# Import React

Wooo! Your first React component!

Take a look at the code on line 1:

```
import React from 'react';
```

This line of code creates a new variable. That variable’s name is `React`, and its value is a particular, imported JavaScript object:

```
// create a variable named React:
import React from 'react';
// evaluate this variable and get a particular, imported JavaScript object:
React // { imported object properties here... }
```

This imported object contains methods that you need in order to use React. The object is called the React *library*.

Later, we’ll go over where the React library is imported from, and how the importing process works. For now, just know that you get the React library via `import React from 'react';`.

You’ve already seen one of the methods contained in the React library: `React.createElement()`. Recall that when a JSX element is *compiled*, it transforms into a `React.createElement()` call.

For this reason, you *have* to import the React library, and save it in a variable named `React`, before you can use any JSX at all. `React.createElement()` must be available in order for JSX to work.

# Import ReactDOM

Now take a look at the code on line 2:

```
import ReactDOM from 'react-dom';
```

This line of code is very similar to line 1.

Lines 1 and 2 both import JavaScript objects. In both lines, the imported object contains React-related methods.

However, there is a difference!

The methods imported from `'react-dom'` are meant for interacting with the DOM. You are already familiar with one of them: ``ReactDOM.render()`.

The methods imported from `'react'` don’t deal with the DOM at all. They don’t engage directly with anything that isn’t part of *React*.

To clarify: the DOM is used in React applications, but it isn’t *part* of React. After all, the DOM is also used in countless non-React applications. Methods imported from `'react'` are only for pure React purposes, such as creating components or writing JSX elements.

# Create a Component Class

You’ve learned that a *React component* is a small, reusable chunk of code that is responsible for one job, which often involves rendering HTML.

Here’s another fact about components: we can use a JavaScript class to define a new React component. We can also define components with JavaScript functions, but we’ll focus on class components first.

All class components will have some methods and properties in common (more on this later). Rather than rewriting those same properties over and over again every time, we extend the `Component` class from the React library. This way, we can use code that we import from the React library, without having to write it over and over again ourselves.

After we *define* our class component, we can use it to render as many instances of that component as we want.

What is `React.Component`, and how do you use it to make a component class?

`React.Component` is a JavaScript class. To create your own component class, you must subclass React.Component. You can do this by using the syntax `class YourComponentNameGoesHere extends React.Component {}`


# Name a Component Class

Good! Subclassing `React.Component` is the way to declare a new *component* class.

When you declare a new component class, you need to give that component class a name. On line 4, notice that our component class’s name is `MyComponentClass`.

Component class variable names must begin with capital letters!

This adheres to JavaScript’s class syntax. It also adheres to a broader programming convention in which class names are written in UpperCamelCase.

In addition, there is a React-specific reason why component class names must always be capitalized. We’ll get to that soon!