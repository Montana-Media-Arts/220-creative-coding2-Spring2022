---
title: Custom Shapes
module: 11
jotted: false
---

# Custom Shapes

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'vertex')">Vertex</button>  
  <button class="tablinks" onclick="openTab(event, 'example')">Example</button>  
  <button class="tablinks" onclick="openTab(event, 'todo')">To Do</button>  
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

### Overview

```js
beginShape();
vertex(30, 20);
vertex(85, 20);
vertex(85, 75);
vertex(30, 75);
endShape(CLOSE);
```

#### Description

Using the beginShape() and endShape() functions allow creating more complex forms. beginShape() begins recording vertices for a shape and endShape() stops recording. The value of the kind parameter tells it which types of shapes to create from the provided vertices. With no mode specified, the shape can be any irregular polygon.

The parameters available for beginShape() are POINTS, LINES, TRIANGLES, TRIANGLE_FAN, TRIANGLE_STRIP, QUADS, QUAD_STRIP, and TESS (WebGL only). After calling the beginShape() function, a series of vertex() commands must follow. To stop drawing the shape, call endShape(). Each shape will be outlined with the current stroke color and filled with the fill color.

Transformations such as translate(), rotate(), and scale() do not work within beginShape(). It is also not possible to use other shapes, such as ellipse() or rect() within beginShape().

DetailX and detailY determines the number of subdivisions in the x-dimension and the y-dimension of a sphere. More subdivisions make the sphere seem smoother. The recommended maximum values are both 24. Using a value greater than 24 may cause a warning or slow down the browser.

#### Syntax

beginShape([kind])

#### Parameters

* kind Constant: either POINTS, LINES, TRIANGLES, TRIANGLE_FAN TRIANGLE_STRIP, QUADS, QUAD_STRIP or TESS (Optional)

</div>
</div>

<div id="vertex" class="tabcontent"  >
<div class="tabhtml" markdown="1">

#### Description

All shapes are constructed by connecting a series of vertices. vertex() is used to specify the vertex coordinates for points, lines, triangles, quads, and polygons. It is used exclusively within the beginShape() and endShape() functions.

#### Syntax

* vertex(x, y)
* vertex(x, y, z, [u], [v])

#### Parameters

* x Number: x-coordinate of the vertex
* y Number: y-coordinate of the vertex
* z Number: z-coordinate of the vertex
* u Number: horizontal coordinate for the texture mapping (Optional)
* v Number: vertical coordinate for the texture mapping (Optional)

</div>
</div>

<div id="example" class="tabcontent"  >
<div class="tabhtml" markdown="1">

### Example

```js

function preload()
{
   dog = loadImage("assets/dog.jpg");
}
// draw a sphere
// with radius 150
function setup() {
  createCanvas(800, 600, WEBGL);
   // need this to make the custom shape appear
  image(dog,0,0);
}

function draw() {
  background(200);
 
  
  rotateX(frameCount * 0.01);
  rotateY(frameCount * 0.01);
  
  translate(-100, -100);
  texture(dog);

  beginShape();
  vertex(0, 0, 100, 0, 0);
  vertex(200, 0, 50, 1, 0);
  vertex(200, 200, 100, 1, 1);
  vertex(0, 200, 50, 0, 1);
  endShape(CLOSE);
}
```

</div>
</div>

<div id="todo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tab to see the final result. Feel free to change values. 

<iframe src="https://editor.p5js.org/michaelcassens/sketches/XRIRdoPyM" width="100%" height="800px"></iframe>
</div>
</div>