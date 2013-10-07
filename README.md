# OOSCSS

This is a specification for arranging SCSS files to make CSS more modular.

## Using @mixins as "classes""

In its simplest terms, it looks like this:

```sass
@mixin class-name(){
	.class-name {
	}
}
```

Anatomy of a class

```sass
@mixin rectangle(){

	// Properties
	$width:	 200px;
	$height: 200px;

	// Constructor
	.rectangle {
		width:  $width;
		height: $height;
	}

}
```
	
## main.scss

`main.scss` should be used only for importing and instantiating 

```sass
// main.scss
	
@import "base-class.scss";
	
@include base-class();
```	
Normal mixins should be denoted with an underscore

```sass
@mixin _gradient($col-a, $col-b) {
	// Code to go in here
}
```

## Inheritance

```sass

@mixin parent-box(){
	.parent-box {
	}
}
	
@mixin child-box(){
	.child-box {
		@extend .parent-box;
	}
}
```
	
## Responsive implemenation

To implement responsive elements:

### Media queries in style.main.scss

`box.class.scss`

```sass
@mixin box($width, $height){
	.box {
		width:  $width;
		height: $height;
		background: grey;
	}
}
```

`style.main.scss`

```sass
// style.main.scss

@import "box.class.scss";

@media screen and (min-width: 320px) {
	@include box(100px, 50px);
}
	
@media screen and (min-width: 960px) {
	@include box(200px, 300px);
}
```
