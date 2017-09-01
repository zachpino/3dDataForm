### Programmatic SVG with Rapahel 

Creating and editing SVG is nice, but it would be better if we could leverage computational logic to create imagery without as much human sweat and concentration. Enter [Raphaël](http://dmitrybaranovskiy.github.io/raphael/), a powerful Javascript library for creating SVG in clientside Javascript.

In order to use Raphael, it is necessary to have a functional HTML page (note that these types of files are no longer openable by Adobe Illustrator or Sketch). 

```html
<!DOCTYPE html>
<html>
<head>
	<title>SVG Experiments</title>
</head>
<body>
  	<script src="https://raw.githubusercontent.com/DmitryBaranovskiy/raphael/master/raphael.min.js"></script>
    
    <script type="text/javascript">
      
      //Javascript code using the Raphael library can be entered here.
    
    </script>
    
</body>
</html>

```

Two script tags are placed. The first imports the functions of the Raphael library. The second script tag is where code should be entered.

First, it is necessary to create an SVG container, just like what is done with the `<svg>` tag when hand-writing SVG or creating an artboard in Illustrator.

```js
    //Create two variables for the storage of useful numbers
		var width = 600;
		var height = 600;
    
    //create an svg container through Raphael
		var canvas = Raphael(0,0,width,height);
```

It is now possible to create objects on that canvas using Raphael's familiar syntax

For example, the following code creates a 20px x 60px rectangle at 100,100 and a 50px radius circle at 200,200.

```js
		var rectangle = canvas.rect(100,100,20,60);
    		var circle = canvas.circle(200,200,50);
```
Position is always defined before size. Check out the [Raphael reference](http://dmitrybaranovskiy.github.io/raphael/reference.html#Paper) for more examples and SVG creation and editing tools.

It is also possible to introduce programmatic [pseudo-randomness](https://en.wikipedia.org/wiki/Pseudorandomness). 

```js
		var randomRadius = Math.random()*20+10;
    		var circle = canvas.circle(200,200,randomRadius);
```

`Math.random()` produces a pseudo-random number between 0 and 1. Multiplying that number by 20 yield a maximum random value of 20, and adding 10 sets a minmum size of 10. Reloading the page will generate newly scaled circles.

SVG attributes can be set using Raphael as well.

```js
		var myRect = canvas.rect(100,100,200,200);
		myRect.attr("fill", "#fff");	
```
It is also possible to set multiple attributes at once using js object syntax.

```js
		var myRect = canvas.rect(100,100,200,200);
		myRect.attr({
			"fill": "#fff", 
			"stroke": "#f0f",
			"stroke-width": 8
		);	
```
