## React: Use Default Props

React also has an option to set default props. You can assign default props to a component as a property on the component itself and React assigns the default prop if necessary. This allows you to specify what a prop value should be if no value is explicitly provided. For example, if you declare `MyComponent.defaultProps = { location: 'San Francisco' }`, you have defined a location prop that's set to the string `San Francisco`, unless you specify otherwise. React assigns default props if props are undefined, but if you pass `null` as the value for a prop, it will remain `null`.

------

The code editor shows a `ShoppingCart` component. Define default props on this component which specify a prop `items` with a value of `0`.



#### Solution 

This was a simple challenge I created a prop for the Shopping cart component. I done this by first starting the name of the component followed by period and `defaultProps` an equal sign followed by curly braces and name of prop and value. e.g. `nameOfComponent.defaultProps = {exampleName: "enter value"} `. This can then be accessed by the shopping cart component. 

`````react
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};
// Change code below this line
ShoppingCart.defaultProps = {items: 0} 
`````