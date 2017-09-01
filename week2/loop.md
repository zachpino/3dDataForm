### Looping

Commonly, designers seek to produce patterns, and Raphael is ideal for explorations into repeating geometries.

Again, it is necessary to have an HTML page structure in place.

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

Within the Raphael code area, a loop can be implemented to draw a row of circles with the `for` control structure.

```js
	var width = 600;
	var height = 600;
	var canvas = Raphael(0,0,width,height);

	for(i=0; i<10; i++){
		var circles = canvas.circle( i*40, 100, 30);
		circles.attr("fill","#f00");
	}
```

The `i` variable counts up from 0, where it begins, until it hits 10 and the loop stops. A circle is placed at each multiple of 40 as `i` increases.

A 2-dimensional grid can also be constructed by nesting a loop within a loop. `i` and `j` are commonly used variable names for such purposes, though any name can be used for either. The `j` variable is now used to set y-values.

```js
	for(i = 0; i < count; i++){
		for(j = 0; j < count; j++){
			var circles = canvas.circle( i*40, j*40, 30);
			circles.attr("fill","#f00");
		}
	}
```


It is possible to do other interesting pattern manipulations as well, harnessing Raphael's ability to construct SVG transformations.

```js
var polarCount = 20;

for(i=0;i<20;i++){
	var rect = canvas.rect(50,50,100,100);
	rect.attr("fill","#f00");
	rect.rotate((360/polarCount)*i, width/2, height/2);
}
```
A rectangle is drawn in red, and given a desired count of 20 rectangles, each rectangle is rotated 18 degrees (360 degrees divided by the desired 20 items) around the center of the canvas (`width` and `height` divided by 2).
