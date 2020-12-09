## React: Use the Lifecycle Method componentWillMount

React components have several special methods that provide opportunities to perform actions at specific points in the lifecycle of a component. These are called lifecycle methods, or lifecycle hooks, and allow you to catch components at certain points in time. This can be before they are rendered, before they update, before they receive props, before they unmount, and so on. Here is a list of some of the main lifecycle methods: `componentWillMount()` `componentDidMount()` `shouldComponentUpdate()` `componentDidUpdate()` `componentWillUnmount()` The next several lessons will cover some of the basic use cases for these lifecycle methods.

**Note:** The `componentWillMount` Lifecycle method will be deprecated in a future version of 16.X and removed in version 17. [(Source)](https://reactjs.org/blog/2018/03/27/update-on-async-rendering.html)

------

The `componentWillMount()` method is called before the `render()` method when a component is being mounted to the DOM. Log something to the console within `componentWillMount()` - you may want to have your browser console open to see the output.



#### Solution 

I Simply added `console.log("test")` inside the `compoentWillMount()` method. 

`````react
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  componentWillMount() {
    // Change code below this line
    console.log("test")
    // Change code above this line
  }
  render() {
    return <div />
  }
};
`````



## Gradual Migration Path

[React follows semantic versioning](https://reactjs.org/blog/2016/02/19/new-versioning-scheme.html), so this change will be gradual. Our current plan is:

- **16.3**: Introduce aliases for the unsafe lifecycles, `UNSAFE_componentWillMount`, `UNSAFE_componentWillReceiveProps`, and `UNSAFE_componentWillUpdate`. (Both the old lifecycle names and the new aliases will work in this release.)
- **A future 16.x release**: Enable deprecation warning for `componentWillMount`, `componentWillReceiveProps`, and `componentWillUpdate`. (Both the old lifecycle names and the new aliases will work in this release, but the old names will log a DEV-mode warning.)
- **17.0**: Remove `componentWillMount`, `componentWillReceiveProps`, and `componentWillUpdate` . (Only the new “UNSAFE_” lifecycle names will work from this point forward.)

More information at [(Source)](https://reactjs.org/blog/2018/03/27/update-on-async-rendering.html)