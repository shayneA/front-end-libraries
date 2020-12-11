## React: Use && for a More Concise Conditional

The if/else statements worked in the last challenge, but there's a more concise way to achieve the same result. Imagine that you are tracking several conditions in a component and you want different elements to render depending on each of these conditions. If you write a lot of `else if` statements to return slightly different UIs, you may repeat code which leaves room for error. Instead, you can use the `&&` logical operator to perform conditional logic in a more concise way. This is possible because you want to check if a condition is `true`, and if it is, return some markup. Here's an example:

```
{condition && <p>markup</p>}
```

If the `condition` is `true`, the markup will be returned. If the condition is `false`, the operation will immediately return `false` after evaluating the `condition` and return nothing. You can include these statements directly in your JSX and string multiple conditions together by writing `&&` after each one. This allows you to handle more complex conditional logic in your `render()` method without repeating a lot of code.

------

Solve the previous example again, so the `h1` only renders if `display` is `true`, but use the `&&` logical operator instead of an `if/else` statement.





#### Solution 

I used the `&&` logical operator to check if `this.state.display` is true. If it's true `<h1>Displayed!</h1>` is shown if its false then it is not shown.  This is a very useful way to test conditions and render JSX, the same can be done with if/else statements, however, it would be more verbose. 

`````react
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState(state => ({
      display: !state.display
    }));
  }
  render() {
    // Change code below this line
    return (
       <div>
         <button onClick={this.toggleDisplay}>Toggle Display</button>
        {this.state.display && <h1>Displayed!</h1>}
       </div>
    );
  }
};
`````