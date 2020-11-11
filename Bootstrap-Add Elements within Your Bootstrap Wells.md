## Bootstrap: Add Elements within Your Bootstrap Wells

Now we're several `div` elements deep on each column of our row. This is as deep as we'll need to go. Now we can add our `button` elements.

Nest three `button` elements within each of your `well` `div` elements.



#### Solution 

I added 3 buttons inside of the div's with the class well.

`````html
<div class="container-fluid">
  <h3 class="text-primary text-center">jQuery Playground</h3>
  <div class="row">
    <div class="col-xs-6">
      <div class="well">

        <button> </button>
        <button> </button>
        <button> </button>
        
      </div>
    </div>
    <div class="col-xs-6">
      <div class="well">
        
        <button> </button>
        <button> </button>
        <button> </button>

      </div>
    </div>
  </div>
</div>
`````


