## React and Redux: Manage State Locally First

Here you'll finish creating the `DisplayMessages` component.

------

First, in the `render()` method, have the component render an `input` element, `button` element, and `ul` element. When the `input` element changes, it should trigger a `handleChange()` method. Also, the `input` element should render the value of `input` that's in the component's state. The `button` element should trigger a `submitMessage()` method when it's clicked.

Second, write these two methods. The `handleChange()` method should update the `input` with what the user is typing. The `submitMessage()` method should concatenate the current message (stored in `input`) to the `messages` array in local state, and clear the value of the `input`.

Finally, use the `ul` to map over the array of `messages` and render it to the screen as a list of `li` elements.





#### Solution 

I created a input box with a submit button. Once the button is clicked the input box gets set to empty and then the message is pasted in a list. 

This was a bit challenging ill paste code then explain top to bottom. 

`````react
class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
		}	}
`````

This is the component I created last challenge. 

 `````react
  handleChange(event){
    this.setState({
      input: event.target.value,
      messages: this.state.messages
    })
  }
 `````

This is the `handleChange()` method it's role is to set the state property of input to be the same as the text being inputted in real time. For example, if a user types "test " the state input first me "t" then "te", "tes" and finally "test".

Also this places the text in the messages array but does not save it. 

`````react
  submitMessage(){
    this.setState({
      input: '',
      messages: [...this.state.messages, this.state.input]
    })
  }
`````

The `submitMessage()`method is to handle the submit button when the submit button is clicked the input is set to an empty string and the text the user types is saved in the messages array. It keeps stacking so the user can have serval messages saved in the messages array. 

`````react
        <input onChange={this.handleChange.bind(this)} value={this.state.input}/>
        <button onClick={this.submitMessage.bind(this)}>Submit</button>
`````

This is the input box and submit button. The `onChange={this.handleChange.bind(this)}` is what allows the user to type in the input box and also this updates the input state to be set to same string as inside input box. The `value={this.state.input}`is what allows the `submitMessage()`method to change the input box back to an empty string. 

The `onClick={this.submitMessage.bind(this)}` triggers the `submitMessage()` method. 

`````react
 <ul>
          {this.state.messages.map((x, i)=>{
            return <li key={i}>{x}</li>
          })}
        </ul>
`````

Lastly this is the unordered list, It's using the JS map method to automatically create a list element for me every time the user clicks the submit button. The key{i} gives each element a unique key that is the index in the list. The {x} is the message the user typed placed on screen so the user can see the message in a list. 

`````react
class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
  }
  // add handleChange() and submitMessage() methods here
  handleChange(event){
    this.setState({
      input: event.target.value,
      messages: this.state.messages
    })
  }

  submitMessage(){
    this.setState({
      input: '',
      messages: [...this.state.messages, this.state.input]
    })
  }

  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        { /* render an input, button, and ul here */ }
        <input onChange={this.handleChange.bind(this)} value={this.state.input}/>
        <button onClick={this.submitMessage.bind(this)}>Submit</button>
        <ul>
          {this.state.messages.map((x, i)=>{
            return <li key={i}>{x}</li>
          })}
        </ul>
        { /* change code above this line */ }
      </div>
    );
  }
};
`````