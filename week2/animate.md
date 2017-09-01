### Interactivity and Animation

Raphael also enables the identification of user behaviors, such as hovering and clicking, and animation.

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
    
    	var width = 600;
	var height = 600;
	
	var polarCount = 12;
	
	var canvas = Raphael(0,0,width,height);
	
	//loop 12 times
    	for(i=0;i<12;i++){
		//make a rectangle
		var myRect = canvas.rect(100,100,50,50);
		
		//set the fill so that each rectangle is more red than the preceding
		myRect.attr("fill", "rgb("+ (255/polarCount)*i + ",0,0)");
		
		//rotate each rectangle around the center of the svg canvas
		myRect.rotate((360/polarCount)*i, width/2, height/2);

		//when the mouse enters the element...
		myRect.mouseover(function(){
			//...animate over one second (1000 milliseconds) the stroke color and width
			this.animate({stroke: '#f0f', 'stroke-width':20}, 1000);
		});

		//when the mouse exits...
		myRect.mouseout(function(){
			//...reset the stroke over .5 seconds
			this.animate({stroke: '#000', 'stroke-width':0}, 500);
		});
	}

</script>
    
</body>
</html>
```

The `animate()` syntax is identical to `.attr` but with an added argument for duration. 

Try out `.click(function(){...})`,`.dblclick(function(){...})`, and `.drag(function(){...})`. There are also `touch` events for tablets and mobile devices detailed in the [Raphael reference](http://dmitrybaranovskiy.github.io/raphael/reference.html#Element.transform).
