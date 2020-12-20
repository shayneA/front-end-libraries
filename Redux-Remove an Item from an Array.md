## Redux: Remove an Item from an Array

Time to practice removing items from an array. The spread operator can be used here as well. Other useful JavaScript methods include `slice()` and `concat()`.

------

The reducer and action creator were modified to remove an item from an array based on the index of the item. Finish writing the reducer so a new state array is returned with the item at the specific index removed.





#### Solution 

I finished off the switch statement in the`immutableReducer` for case "REMOVE_ITEM" I return an array with 1 number deleted. I do this with the stead operator and `.slice()`. 

This was bit confusing. The goal is to get rid of the number at the index and return the rest of the array.  For example if the state was `[0,1,2,3,4,5]`and the index is 4 then 4 should be removed at the returned array should be `[ 0, 1, 2, 3, 5 ]` This is shown below in `consol.log `'s.  

`````react
const immutableReducer = (state = [0,1,2,3,4,5], action) => {
  switch(action.type) {
    case 'REMOVE_ITEM':
      // Don't mutate state here or the tests will fail
      return [...state.slice(0, action.index), ...state.slice(action.index + 1)]
    default:
      return state;
  }
};

const removeItem = (index) => {
  return {
    type: 'REMOVE_ITEM',
    index
  }
}

const store = Redux.createStore(immutableReducer);

console.log(store.getState())
store.dispatch(removeItem(4))
console.log(store.getState())
store.dispatch(removeItem(0))
console.log(store.getState())
/* ¬ Console.log's ¬
[ 0, 1, 2, 3, 4, 5 ]
[ 0, 1, 2, 3, 5 ]
[ 1, 2, 3, 5 ]
^^ Console.log's ^^  */ 
`````

