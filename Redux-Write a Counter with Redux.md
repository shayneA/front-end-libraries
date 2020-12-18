## Redux: Write a Counter with Redux

Now you've learned all the core principles of Redux! You've seen how to create actions and action creators, create a Redux store, dispatch your actions against the store, and design state updates with pure reducers. You've even seen how to manage complex state with reducer composition and handle asynchronous actions. These examples are simplistic, but these concepts are the core principles of Redux. If you understand them well, you're ready to start building your own Redux app. The next challenges cover some of the details regarding `state` immutability, but first, here's a review of everything you've learned so far.

------

In this lesson, you'll implement a simple counter with Redux from scratch. The basics are provided in the code editor, but you'll have to fill in the details! Use the names that are provided and define `incAction` and `decAction` action creators, the `counterReducer()`, `INCREMENT` and `DECREMENT` action types, and finally the Redux `store`. Once you're finished you should be able to dispatch `INCREMENT` or `DECREMENT` actions to increment or decrement the state held in the `store`. Good luck building your first Redux app!





#### Solution 

I created a simple counter with redux. First I set up the action types`INCREMENT`and`DECREMENT` setting them to strings with the same name as constants. 

Next I created the reducer for the counter, `counterReducer` has a state set to 0 and an action as parameters. Next I gave it a switch statement that has 2 cases one for increment and the other for decrement, when they are called they return the state incremented or decremented else the state is returned unchanged. 

Then I set up the action creators for the increment and decrement, `incAction` returns a object with a type and value of "INCREMENT", `decAction`is the same thing but for the type value is "DECREMENT".

Lastly, I set up the redux store by setting the const store to `Redux.createStore(counterReducer)`.

`````react
const INCREMENT = "INCREMENT"; // Define a constant for increment action types
const DECREMENT = "DECREMENT"; // Define a constant for decrement action types

const counterReducer = (state = 0, action) => {

    switch(action.type) {
        case INCREMENT:
            return state + 1;

        case DECREMENT:
            return state - 1;

        default:
            return state
    }
    
}; // Define the counter reducer which will increment or decrement the state based on the action it receives

const incAction = () => { return {type: INCREMENT} }; // Define an action creator for incrementing

const decAction = () => { return {type: DECREMENT} }; // Define an action creator for decrementing

const store = Redux.createStore(counterReducer); // Define the Redux store here, passing in your reducers
`````