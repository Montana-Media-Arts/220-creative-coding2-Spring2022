---
title: ellipsoid
module: 9
jotted: false
---

# ellipsoid

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'example')">Example</button>  
  <button class="tablinks" onclick="openTab(event, 'todo')">To Do</button>  
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

### Overview

```js
// draw an ellipsoid
// with size 30, 40 and 40.
function setup() {
  createCanvas(100, 100, WEBGL);
}

function draw() {
  background(205, 105, 94);
  ellipsoid(30, 40, 40);
}
```

#### Description

Draw an ellipsoid with given radius

DetailX and detailY determine the number of subdivisions in the x-dimension and the y-dimension of a cone. More subdivisions make the ellipsoid appear to be smoother. Avoid detail number above 150, it may crash the browser.

#### Syntax

ellipsoid([radiusx], [radiusy], [radiusz], [detailX], [detailY])

#### Parameters

* radiusx Number: x-radius of ellipsoid (Optional)
* radiusy Number: y-radius of ellipsoid (Optional)
* radiusz Number: z-radius of ellipsoid (Optional)
* detailX Integer: number of segments, the more segments the smoother geometry default is 24. Avoid detail number above 150, it may crash the browser. (Optional)
* detailY Integer: number of segments, the more segments the smoother geometry default is 16. Avoid detail number above 150, it may crash the browser. (Optional)

</div>
</div>

<div id="example" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

### Example

```js

// draw a ellipsoid
// with size 50, 150 and 74.
function setup() {
  createCanvas(600, 800, WEBGL);
}

function draw() {
    background(200);
    normalMaterial();
    translate(-100,-100);
    rotateX(frameCount * 0.01);
    rotateY(frameCount * 0.01);
    ellipsoid(50, 150,75, 24, 24);
}
```

</div>
</div>

<div id="todo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tab to see the final result. Feel free to change values. 

<iframe src="https://editor.p5js.org/michaelcassens/sketches/HG2y4qVvB" width="100%" height="800px"></iframe>
</div>
</div>