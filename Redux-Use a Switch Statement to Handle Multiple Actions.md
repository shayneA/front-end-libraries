## Redux: Use a Switch Statement to Handle Multiple Actions

You can tell the Redux store how to handle multiple action types. Say you are managing user authentication in your Redux store. You want to have a state representation for when users are logged in and when they are logged out. You represent this with a single state object with the property `authenticated`. You also need action creators that create actions corresponding to user login and user logout, along with the action objects themselves.

------

The code editor has a store, actions, and action creators set up for you. Fill in the `reducer` function to handle multiple authentication actions. Use a JavaScript `switch` statement in the `reducer` to respond to different action events. This is a standard pattern in writing Redux reducers. The switch statement should switch over `action.type` and return the appropriate authentication state.

**Note:** At this point, don't worry about state immutability, since it is small and simple in this example. For each action, you can return a new object — for example, `{authenticated: true}`. Also, don't forget to write a `default` case in your switch statement that returns the current `state`. This is important because once your app has multiple reducers, they are all run any time an action dispatch is made, even when the action isn't related to that reducer. In such a case, you want to make sure that you return the current `state`.





#### Solution 

I used a JavaScript switch statement to handle different `action.type` cases. In the case where `action.type`is equal to `"LOGIN"` the switch statements returns an anonymous JS object of `{authenticated: true}`. I also made one for the case `"LOGOUT"` which returns `authenticated: false`, lastly I set up a default case that returns state. 

extra info below solution. 

`````react
const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  // Change code below this line

  switch(action.type){

  case 'LOGIN': 
  return {
    authenticated: true
    }  

  case 'LOGOUT': 
  return {
    authenticated: false
    } 

  default: 
  return state
  }

  // Change code above this line
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: 'LOGIN'
  }
};

const logoutUser = () => {
  return {
    type: 'LOGOUT'
  }
};
`````



##### Extra info

Tip: Make sure you don’t use “break” commands after return statements within the switch cases.

Specific actions will be passed into the reducer function. Look at the action creator functions (e.g. loginUser) to see what values you will need to check for in your switch case statements.

Each case condition should return an updated authenticated property object.

Do not forget to include a default case in your statement which returns the defaultState.

