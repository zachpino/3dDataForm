  ### Week 2 · Programmatic 2D SVG
  
[Scalable Vector Graphics](http://www.wikipedia.com/wiki/svg) are a powerful method for drawing interactive, animated, complex shapes in a web browser.

The language itself is remarkably simple, though expressive. This chunk of code creates an svg canvas (work area) 600px by 600px, with a circle positioned at 200px, 100px and a radius of 30px.

```svg
<svg width='600' height='600'>

  <circle cx="200" cy="100" r="30" />

</svg>
```

Copy that code into a text editor like [Sublime](http://www.sublimetext.org) and save the file as `circle.svg`. The resulting file can be opened and edited in Adobe Illustrator or Sketch, and can be viewed in most web browsers. This flexibility is what makes SVG so powerful.

Various other svg *elements* can be created with the same structure, though each maintains different *mandatory attributes* -- the settings like `cx` and `points` that describe their geometry.

```svg

<circle cx="100" cy="100" r="100"/>

<ellipse cx="60" cy="60" rx="50" ry="25"/>

<image xlink:href="http://www..." height="100" width="100"/>    

<line x1="20" y1="100" x2="100" y2="20"/>

<polygon points="60,20 100,40 100,80 60,100 20,80 20,40"/>

<polyline points="20,100 40,60 70,80 100,20"/>

<rect x="10" y="10" width="100" height="100"/>

```

Adobe Illustrator allows the export of SVG content, so making content there and evaluating its output is the best way to learn these elements. There are [many other svg elements](https://developer.mozilla.org/en-US/docs/Web/SVG/Element#Graphics_elements), though they are far more rarely encountered.

Editing these lines of code will allow the composition of various objects within the svg canvas. In order to change the visual appearance of these objects, [other attributes](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute) can be used. The order of attributes does not usually matter.

```svg
<circle cx="100" cy="100" r="100" fill="#f00" stroke="#ff0" stroke-width="5" stroke-opacity=".7" fill-opacity=".5" />
```

```svg
<svg width='600' height='600'>

  <circle cx="200" cy="400" r="50" fill="#f0f"/>
  <rect x="150" y="420" width="100" height="200" fill="#0ff"/>
  
</svg>
```

Note that the rectangle is drawn from its upper-left corner, and the circle from the center. Note, too, that the rectangle is drawn on top of the circle. In SVG, elements described later are drawn on top of elements described earlier.

The `<text>` element can be used to draw text to the canvas. Its formatting is slightly different, as it contains a child -- the text to display.

```svg
<svg width='600' height='600'>

  <text x="50" y="50" font-family="Courier" font-size="15" fill="#f00">
    Some writing on the screen
  </text>
  
</svg>  
```  

In the same way, elements can be arbitrarily grouped.

```svg
<svg width='600' height='600'>

  <g>
    <circle cx="200" cy="400" r="50" fill="#f0f"/>
    <rect x="150" y="420" width="100" height="200" fill="#0ff"/>
  </g>
  
  <g>
    <circle cx="500" cy="300" r="10" fill="#00f"/>
    <rect x="150" y="420" width="150" height="300" fill="#0f0"/>
  </g>
  
</svg>  
```

A very powerful attribute is `transform`, which allows the repositioning of elements using a special syntax.

```svg
<rect x="100" y="100" width="50" height="50" transform="translate(50 60) rotate(72 300 300) scale(2 1.5)"
```
This code draws a 50 pixel square at 100,100. The `transform` attribute moves (`translate`s) the object 50 pixels to the right and 60 pixels down, rotates the rectangle 72 degrees around the point at 300,300 and scales the rectangle 2x on its x-axis and 1.5 on its y-axis. There is [inherent complexity](https://css-tricks.com/transforms-on-svg-elements/) in this attribute, which requires experimentation.

The most powerful SVG element is `path` which draws arbitrary shapes based on one attribute, containing coordinates and a [special markup language](https://www.w3.org/TR/SVG/paths.html).

```svg
    <path d="M200,300 L400,50 L600,300 L800,550 L1000,300 Z" fill="none" stroke="#888888" stroke-width="2" />
```
The `d` attribute here moves (`M`) the imaginary pen to 200,300, draws a line (`L`) to 600,300, another to 800,550, and a final line to 200,300. The path is then closed (`Z`). `<path>` is worth the time to master, as any shape can be drawn in programmatic ways.
