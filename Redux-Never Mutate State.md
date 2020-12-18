## Redux: Never Mutate State

These final challenges describe several methods of enforcing the key principle of state immutability in Redux. Immutable state means that you never modify state directly, instead, you return a new copy of state.

If you took a snapshot of the state of a Redux app over time, you would see something like `state 1`, `state 2`, `state 3`,`state 4`, `...` and so on where each state may be similar to the last, but each is a distinct piece of data. This immutability, in fact, is what provides such features as time-travel debugging that you may have heard about.

Redux does not actively enforce state immutability in its store or reducers, that responsibility falls on the programmer. Fortunately, JavaScript (especially ES6) provides several useful tools you can use to enforce the immutability of your state, whether it is a `string`, `number`, `array`, or `object`. Note that strings and numbers are primitive values and are immutable by nature. In other words, 3 is always 3. You cannot change the value of the number 3. An `array` or `object`, however, is mutable. In practice, your state will probably consist of an `array` or `object`, as these are useful data structures for representing many types of information.

------

There is a `store` and `reducer` in the code editor for managing to-do items. Finish writing the `ADD_TO_DO` case in the reducer to append a new to-do to the state. There are a few ways to accomplish this with standard JavaScript or ES6. See if you can find a way to return a new array with the item from `action.todo` appended to the end.





#### Solution 

Inside the `immutableReducer` I finished off the switch statement case `ADD_TO_DO` by making it return a new array with `action.todo` added to the end of it. There is multiple ways of completing this. extra information at under solution. 

`````react
const ADD_TO_DO = 'ADD_TO_DO';

// A list of strings representing tasks to do:
const todos = [
  'Go to the store',
  'Clean the house',
  'Cook dinner',
  'Learn to code',
];

const immutableReducer = (state = todos, action) => { 
  
  switch(action.type) {
    case ADD_TO_DO:
      // Don't mutate state here or the tests will fail
      return state.concat(action.todo)
    default:
      return state;
  }
};

const addToDo = (todo) => {
  return {
    type: ADD_TO_DO,
    todo
  }
}

const store = Redux.createStore(immutableReducer);
`````



##### Extra info 



const means: it cannot change through re-assignment, and it cannot be re-declared.
Since objects and arrays are mutable, you can add to it by index (array[3] = 3), by property (object.name=“sam”), by extending (with various array methods)

.push() and .splice() directly modify the array

.concat() doesn’t modify array but just returns a new array

.slice() doesn’t modify array but just returns a new array

spread operator […array] doesn’t modify array but just returns a new array