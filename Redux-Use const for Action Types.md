## Redux: Use const for Action Types

A common practice when working with Redux is to assign action types as read-only constants, then reference these constants wherever they are used. You can refactor the code you're working with to write the action types as `const` declarations.

------

Declare `LOGIN` and `LOGOUT` as `const` values and assign them to the strings `'LOGIN'` and `'LOGOUT'`, respectively. Then, edit the `authReducer()` and the action creators to reference these constants instead of string values.

**Note:** It's generally a convention to write constants in all uppercase, and this is standard practice in Redux as well.





#### Solution 

I created 2 const's LOGIN & LOGOUT then I set them to their corresponding string's. 

Then I changed the `authReducer` switch statement by changing the case from a string to its corresponding const.  I then done the same thing for the action functions loginUser and logoutUser. 

Extra information on this below explain why using a const is better than a string:

`````react
// Change code below this line
const LOGIN = "LOGIN";
const LOGOUT = "LOGOUT";
// Change code above this line

const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {

  switch (action.type) {

    case LOGIN:
      return {
        authenticated: true
      }

    case LOGOUT:
      return {
        authenticated: false
      }

    default:
      return state;

  }

};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: LOGIN
  }
};

const logoutUser = () => {
  return {
    type: LOGOUT
  }
};
`````





##### Problem Explanation

Using a const for Action Types has a big advantage over using strings.

**Accidental mispellings of strings can lead to errors.**

You may spell `type: 'LOGIN'` correctly in your action creator but mispell `type: 'LOGN'` in your reducer as shown below.

```javascript
const loginUser = () => {
  return {
    type: "LOGIN"
  };
};

const authReducer = (state = defaultState, action) => {
  switch (action.type) {
    case "LOGN":
      return {
        authenticated: true
      };

    case "LOGOUT":
      return {
        authenticated: false
      };

    default:
      return state;
  }
};
```

By using a const for the Action Type, it won’t matter if your string is mispelled because both the reducer’s switch statement and the Action Type are referencing the same `const`. Using a `const` may also lead your code editor to suggesting the `const` as you are typing it, thus reducing the chance of mispelling the `const`.