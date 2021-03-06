# this.props.children

Every component’s ``props`` object has a property named ``children``.

``this.props.children`` will return everything in between a component’s opening and closing JSX tags.

So far, all of the components that you’ve seen have been *self-closing tags*, such as ``<MyComponentClass />``. They don’t have to be! You could write ``<MyComponentClass></MyComponentClass>``, and it would still work.

``this.props.children`` would return everything in between ``<MyComponentClass />`` and ``<MyComponentClass />``.

Look at **BigButton.js**. In Example 1, ``<BigButton>``‘s ``this.props.children`` would equal the text, “I am a child of BigButton.”

In Example 2, ``<BigButton>``‘s ``this.props.children`` would equal a ``<LilButton />`` component.

In Example 3, ``<BigButton>``‘s ``this.props.children`` would equal ``undefined``.

If a component has more than one child between its JSX tags, then ``this.props.children`` will return those children in an array. However, if a component has only one child, then ``this.props.children`` will return the single child, not wrapped in an array.s