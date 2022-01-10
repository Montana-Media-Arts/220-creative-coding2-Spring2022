---
title: p5.js Basic Shapes
module: 1
jotted: false
---

## Review p5.js Basic Shapes

Remember, drawing simple shapes is the first thing that p5.js allows us to do quickly. You can do this using the p5.js editor or you an create a page a sketch file. If you need a refresher, please feel free to go back to <a href="https://montana-media-arts.github.io/120_CreativeCoding1-Fall2020/modules/week-9/overview/" target="_new">MART 120 Week 9</a>.   Here are examples in the following tabs.

<div class="tab">
    <button class="tablinks active" onclick="openTab(event, 'Circle')">Circle</button>
    <button class="tablinks" onclick="openTab(event, 'Square')">Square</button>
    <button class="tablinks" onclick="openTab(event, 'Ellipse')">Ellipse</button>
    <button class="tablinks" onclick="openTab(event, 'Rect')">Rect</button>
    <button class="tablinks" onclick="openTab(event, 'Triangle')">Triangle</button>
    <button class="tablinks" onclick="openTab(event, 'Point')">Point</button>
    <button class="tablinks" onclick="openTab(event, 'Line')">Line</button>
    <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
    
</div>
<!-- Tab content -->
<div id="Circle" class="tabcontent" style="display:block">

<div class="tabhtml" markdown="1">

To draw a circle, it might look like this.

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  circle(30,40,50);
}
```

How does this work?

1. circle is the name of the function
2. 30 is the x-coordinate on the page
3. 40 is the y-coordinate on the page
4. 50 is the diameter of the circle

One thing in which to mindful, the x and y origin is in the upper left-hand corner.  Any guesses why? It's because we don't like negative numbers. It's easier to move to the right positively and down positively.  Then, as we subtract, we move left and up, respectively.

</div>
</div>

<!-- Tab content -->
<div id="Square" class="tabcontent">

<div class="tabhtml" markdown="1">

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  square(30,40,50);
}
```

This time square is the name of the function.  30 is still the x, 40 is the y-coordinate, and the 50 represents the width and height since they are the same.

Give it a try!
</div>
</div>
<div id="Ellipse" class="tabcontent">

<div class="tabhtml" markdown="1">

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  ellipse(30,40,50,60);
}
```

Notice the difference with the ellipse as it allows us to create a different width and height. If the height and width were the same, it would be a circle.
</div>
</div>
<div id="Rect" class="tabcontent">

<div class="tabhtml" markdown="1">

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  rect(30,40,50,60);
}
```

Same for the rect function.  If the last two parameters are the same, we will get a square, but we will get a rectangle if they are different.
</div>
</div>

<div id="Triangle" class="tabcontent">

<div class="tabhtml" markdown="1">

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  triangle(30, 75, 58, 20, 86, 75);
}
```
The first two parameters represent the first point, which is the **bottom-left** point; in this case, then the second two parameters are the second point, which is the **top point**, and then the last two parameters represent the third point or the **bottom-right** point in this triangle.  

There are several other simple shapes, such as point, line, and quad.
</div>
</div>
<div id="Point" class="tabcontent">
<div class="tabhtml" markdown="1">

What if we want to place a point?  This is follows the same methodology as the other simple shapes.

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  point(30, 75);
}
````

This places a point at the x-coordinate of 30 and the y-coordinate of 75.

</div>
</div>

<div id="Line" class="tabcontent">
<div class="tabhtml" markdown="1">

Finally, to create a line, we need two points and then p5.js creates a line between the two points.

```js
function setup() {
  createCanvas(400,400);
}

function draw() {
  background(220);
  line(30, 20, 85, 75);
}
````

This example places the first point on the line at x-coordinate 30 and y-coordinate 20.  The second point is placed at x-coordinate 85 and y-coordinate 75.  And that's it!

</div>
</div>
<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">

Add different shapes to the draw method.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>