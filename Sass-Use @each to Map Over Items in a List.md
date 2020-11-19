## Sass: Use @each to Map Over Items in a List

The last challenge showed how the `@for` directive uses a starting and ending value to loop a certain number of times. Sass also offers the `@each` directive which loops over each item in a list or map. On each iteration, the variable gets assigned to the current value from the list or map.

```scss
@each $color in blue, red, green {
  .#{$color}-text {color: $color;}
}
```

A map has slightly different syntax. Here's an example:

```scss
$colors: (color1: blue, color2: red, color3: green);

@each $key, $color in $colors {
  .#{$color}-text {color: $color;}
}
```

Note that the `$key` variable is needed to reference the keys in the map. Otherwise, the compiled CSS would have `color1`, `color2`... in it. Both of the above code examples are converted into the following CSS:

```scss
.blue-text {
  color: blue;
}

.red-text {
  color: red;
}

.green-text {
  color: green;
}
```

------

Write an `@each` directive that goes through a list: `blue, black, red` and assigns each variable to a `.color-bg` class, where the "color" part changes for each item. Each class should set the `background-color` the respective color.



In this challenge, I am using the @each directive/loop to change the background colour of 3 div's. 



#### Solution-1

`````scss
  $colors: (blue-bg: blue, black-bg: black, red-bg: red);

  @each $class, $color in $colors {
    .#{$class} {background-color: $color;}
  }
`````

In the first solution I create a variable called `$colors`. I give it 3 values; blue-bg: blue, black-bg: black and red-bg: red. The first part is the name of the class for the first div and second is the respective colour. For example blue-bg is class name and its colour is blue. Next I call the @each directive and give it 2 parameters $class and $color, then I type in colors. next I call the first parameter which is the first class in the colours variable, then I use the css background-color: with the 2nd parameter which is the respective colour in the colors variable.



#### Solution-2

`````scss
  @each $color in blue, black, red {
    .#{$color}-bg {background-color: $color;}
  }
`````

The 2nd solution is much cleaner. I first call the @each directive then I give it the parameter $color to be used later.  The $color will be blue in the first iteration then black and red. I then use a period followed by a hashtag and semi colon and place the $color parameter in there.  followed by hyphen bg. Then I use the css command background-color: with the $color parameter as its input. Once this runs the $color parameter changes to the respective colors in order. 



Both these examples would look like this in normal CSS.

``````scss
.blue-bg {
  color: blue;
}

.black-bg {
  color: black;
}

.red-bg {
  color: red;
}
``````