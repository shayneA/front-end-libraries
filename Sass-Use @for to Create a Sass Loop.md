## Sass: Use @for to Create a Sass Loop

The `@for` directive adds styles in a loop, very similar to a `for` loop in JavaScript.

`@for` is used in two ways: "start through end" or "start to end". The main difference is that the "start **to** end" *excludes* the end number as part of the count, and "start **through** end" *includes* the end number as part of the count.

Here's a start **through** end example:

```scss
@for $i from 1 through 12 {
  .col-#{$i} { width: 100%/12 * $i; }
}
```

The `#{$i}` part is the syntax to combine a variable (`i`) with text to make a string. When the Sass file is converted to CSS, it looks like this:

```scss
.col-1 {
  width: 8.33333%;
}

.col-2 {
  width: 16.66667%;
}

...

.col-12 {
  width: 100%;
}
```

This is a powerful way to create a grid layout. Now you have twelve options for column widths available as CSS classes.

------

Write a `@for` directive that takes a variable `$j` that goes from 1 **to** 6.

It should create 5 classes called `.text-1` to `.text-5` where each has a `font-size` set to 15px multiplied by the index.



#### Solution

I created a for loop using SASS. Iterates though the p elements with the class text-1 to text-5. The for loop is using #j as the parameter. First the class is called with a period( . ) next the class name in this case "text-" lastly the number going form 1 to 5. The default font size is set to 15px for 1st p element. depending on the number the loop multiplies the font size by the number represented by #J. So it go's 15, 30, etc until it reach's 5. 

`````scss
<style type='text/scss'>

    @for $j from 1 through 5 {
        .text-#{$j} {font-size: 15px * $j; } 
    }

</style>

<p class="text-1">Hello</p>
<p class="text-2">Hello</p>
<p class="text-3">Hello</p>
<p class="text-4">Hello</p>
<p class="text-5">Hello</p>
`````