# Access a Component's state

To *read* a component’s ``state``, use the expression ``this.state.name-of-property``:

```
class TodayImFeeling extends React.Component {
  constructor(props) {
    super(props);
    this.state = { mood: 'decent' };
  }

  render() {
    return (
      <h1>
        I'm feeling {this.state.mood}!
      </h1>
    );
  }
}
```

The above component class reads a property in its ``state`` from inside of its ``render`` function.

Just like ``this.props``, you can use ``this.state`` from any property defined inside of a component class’s body.