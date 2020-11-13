## Sass: Store Data with Sass Variables

One feature of Sass that's different than CSS is it uses variables. They are declared and set to store data, similar to JavaScript.

In JavaScript, variables are defined using the `let` and `const` keywords. In Sass, variables start with a `$` followed by the variable name.

Here are a couple examples:



```scss
$main-fonts: Arial, sans-serif;
$headings-color: green;

//To use variables:
h1 {
  font-family: $main-fonts;
  color: $headings-color;
}
```



One example where variables are useful is when a number of elements need to be the same color. If that color is changed, the only place to edit the code is the variable value.

------

Create a variable `$text-color` and set it to red. Then change the value of the `color` property for the `.blog-post` and `h2` to the `$text-color` variable.



#### Solution 

I created a variable in sass called `text-color` and I set it to red. Using this variable I changed the colour of the blog post classes and h2 header to red. *Note: The syntax is vary important the variable starts with a dollar sign, after the name is finished there is a colon at the end and lastly there needs to be a semi colon at the end after css is stated for example. To create a variable that holds the colour red the syntax is: `$variable-name: red;`.

``````scss
<style type='text/scss'>

  $text-color: red;
 
  .header{
    text-align: center;
  }
  .blog-post, h2 {
    color: $text-color; 
  }
</style>

<h1 class="header">Learn Sass</h1>
<div class="blog-post">
  <h2>Some random title</h2>
  <p>This is a paragraph with some random text in it</p>
</div>
<div class="blog-post">
  <h2>Header #2</h2>
  <p>Here is some more random text.</p>
</div>
<div class="blog-post">
  <h2>Here is another header</h2>
  <p>Even more random text within a paragraph</p>
</div>
``````