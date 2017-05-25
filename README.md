# Sass102

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
	* make groups of CSS declarations that you want to reuse throughout your site:
		* declare the following at the top of the SCSS file:
		```
		@mixin backface-visibility {
  			backface-visibility: hidden;
  		}

  		* use `@include backface_visibility;` wherever you want to include that mixin