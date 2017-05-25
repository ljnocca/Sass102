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
  	