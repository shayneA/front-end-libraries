## React: Use a Ternary Expression for Conditional Rendering

Before moving on to dynamic rendering techniques, there's one last way to use built-in JavaScript conditionals to render what you want: the ternary operator. The ternary operator is often utilized as a shortcut for `if/else` statements in JavaScript. They're not quite as robust as traditional `if/else` statements, but they are very popular among React developers. One reason for this is because of how JSX is compiled, `if/else` statements can't be inserted directly into JSX code. You might have noticed this a couple challenges ago — when an `if/else` statement was required, it was always *outside* the `return` statement. Ternary expressions can be an excellent alternative if you want to implement conditional logic within your JSX. Recall that a ternary operator has three parts, but you can combine several ternary expressions together. Here's the basic syntax:



```jsx
condition ? expressionIfTrue : expressionIfFalse;
```



------

The code editor has three constants defined within the `CheckUserAge` component's `render()` method. They are called `buttonOne`, `buttonTwo`, and `buttonThree`. Each of these is assigned a simple JSX expression representing a button element. First, initialize the state of `CheckUserAge` with `input` and `userAge` both set to values of an empty string.

Once the component is rendering information to the page, users should have a way to interact with it. Within the component's `return` statement, set up a ternary expression that implements the following logic: when the page first loads, render the submit button, `buttonOne`, to the page. Then, when a user enters their age and clicks the button, render a different button based on the age. If a user enters a number less than `18`, render `buttonThree`. If a user enters a number greater than or equal to `18`, render `buttonTwo`.



#### Solution 

First, I initialize the state for the CheckUserAge component and gave it a input and userAge props set to empty stings. 

Next, I used the ternary expression to display different buttons depending on the input and when they click submit. The first button was the submit button, this should be shown when `this.state.userAge` is still an empty string. Next was buttonTwo this is shown when the user enters an age over 18. Lastly buttonThree shows when the user enters a age under 18. 

<u>example of ternary expression under solution</u> 

`````react
const inputStyle = {
  width: 235,
  margin: 5
};

class CheckUserAge extends React.Component {
  constructor(props) {
    super(props);
    // Change code below this line
    this.state = {
      input: "",
      userAge: ""
    }
    // Change code above this line
    this.submit = this.submit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(e) {
    this.setState({
      input: e.target.value,
      userAge: ''
    });
  }
  submit() {
    this.setState(state => ({
      userAge: state.input
    }));
  }
  render() {
    const buttonOne = <button onClick={this.submit}>Submit</button>;
    const buttonTwo = <button>You May Enter</button>;
    const buttonThree = <button>You Shall Not Pass</button>;
    return (
      <div>
        <h3>Enter Your Age to Continue</h3>
        <input
          style={inputStyle}
          type='number'
          value={this.state.input}
          onChange={this.handleChange}
        />
        <br />
        {/* Change code below this line */}
        {this.state.userAge == ""
         ? buttonOne 
         : this.state.userAge >= 18 
         ? buttonTwo
         : this.state.userAge <= 18
         ? buttonThree 
         : null 
        } 
       
        {/* Change code above this line */}
      </div>
    );
  }
} 
`````



##### ternary expression examples 

`{this.state.userAge == "" `is the first statement on line 1 when the condition is true the second line is returned.  

`? buttonOne` After the condition is given. The true response needs to have a question mark before the code u want returned also there needs to be colon with a return statement for the ternary expression to end. If the false response is not given an error will happen. 

`         : this.state.userAge >= 18 `in this example, I chained ternary expressions together to test more condition. This line checks that the userAge is greater than or equal to 18 and if it is button 2 is shown. ` ? buttonTwo`

`: this.state.userAge <= 18` I then checked if the userAge is less than 18 and if it is button 3 will be shown ` ? buttonThree `. 

`  : null } ` lastly if none of the previous statements were true null is returned and nothing happens. I needed to add this as without a responsive for the false condition an error would happen. 

`````react
		{this.state.userAge == ""
         ? buttonOne 
         : this.state.userAge >= 18 
         ? buttonTwo
         : this.state.userAge <= 18
         ? buttonThree 
         : null 
        } 
`````