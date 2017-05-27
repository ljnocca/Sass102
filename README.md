# Sass102

## Compiling
* In the terminal, compile the SCSS to CSS by typing the following command:
`sass --watch style.scss:style.css `

## Lesons Learned
* Pseudo-elements (ie: `::before`, `::after`, and `:hover`)
	* in SCSSS:
	```
	.notecard{ 
  		&:hover{
      		@include transform (rotatey(-180deg));  
    	}
  	}
  	```

* mixins
	* In general, here are 5 important facts about arguments and mixins:
	1. Mixins can take multiple arguments.
	2. Sass allows you to explicitly define each argument in your @include statement.
	3. When values are explicitly specified you can send them out of order.
	4. If a mixin definition has a combination of arguments with and without a default value, you should define the ones with no default value first.
	5. Mixins can be nested.

	```
	@mixin dashed-border($width, $color: #FFF) {
	  	border: {
		     color: $color;
		     width: $width;
		     style: dashed;
	  	}
	}

	span { //only passes non-default argument
	    @include dashed-border(3px);
	}

	p { //passes both arguments
	    @include dashed-border(3px, green);
	}

	div { //passes out of order but explicitly defined
	   @include dashed-border(color: purple, width: 5px); 
	}
	```
	* In the example above, the color of the border of span elements would be white, the border of paragraph elements would be green, while the div elements would have a thicker purple border.

	* make groups of CSS declarations that you want to reuse throughout your site:
		* declare the following at the top of the SCSS file (takes in an argument for visibility):
		```
		@mixin backface-visibility($visibility) {
  			backface-visibility: $visibility;
  		}
  		```
  		* use `@include backface_visibility(hidden);` wherever you want to include that mixin. Here the visibility assigned is "hidden"
  		* OR You can assign a default value in the mixin definition. If no value is passed in to the argument, the default is used:
  		```
		@mixin backface-visibility($visibility: hidden) {
  			backface-visibility: $visibility;
  		}
  		```
 * List Arguments
 	* Sass allows you to pass in multiple arguments in a list or a map format.
 	* it makes sense to create a map with these properties in case we ever want to update or reference them.
 	```
	$college-ruled-style: ( 
	    direction: to bottom,
	    width-percent: 15%,
	    stripe-color: blue,
	    stripe-background: white
	);
	```
	* When we include our mixin, we can then pass in these arguments in a map with the following `...` notation:
	```
	.definition {
      width: 100%;
      height: 100%;
      @include stripes($college-ruled-style...);
 	}
 	```
 * string interpolation
 	* interpolation is handy when you want to make use of variables in selectors or file names. The notation is as follows:
 	```
	@mixin photo-content($file) {
	  content: url(#{$file}.jpg); //string interpolation
	  object-fit: cover;
	}


	.photo { 
	  @include photo-content('titanosaur');
	  width: 60%;
	  margin: 0px auto; 
	  }
	```
	* String interpolation would enable the following CSS:
	```
	.photo { 
	  content: url(titanosaur.jpg);
	  width: 60%;
	  margin: 0px auto; 
	}
	```
* & selector with mixins
	``
	 .word { //SCSS: 
	    display: block; 
	    text-align: center;
	    position: relative;
	    top: 40%;
	    @include text-hover(red);
  	}
  	``

# Main Lessons
1. Mixins are a powerful tool that allow you to keep your code DRY. Their ability to take in arguments, assign default values to those arguments, and accept said arguments in whatever format is most readable and convenient for you makes the mixin Sass's most popular directive.
2. The & selector* is a Sass construct that allows for expressive flexibility by referencing the parent selector when working with CSS psuedo elements and classes.
3. String interpolation is the glue that allows you to insert a string in the middle of another when it is in a variable format. Its applications vary, but the ability to interpolate is especially useful for passing in file names.

