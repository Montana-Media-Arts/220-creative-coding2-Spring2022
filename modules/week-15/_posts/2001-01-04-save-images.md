---
title: Create Movie
module: 14
jotted: true
---

# Create a Movie

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'framerate')">frameRate</button>
  <button class="tablinks" onclick="openTab(event, 'draw')">draw</button>
  <button class="tablinks" onclick="openTab(event, 'mod')">mod operator %</button>
  <button class="tablinks" onclick="openTab(event, 'saveframes')">saveFrames</button>
  <button class="tablinks" onclick="openTab(event, 'noloop')">noloop</button>
  <button class="tablinks" onclick="openTab(event, 'todo')">To Do</button>
</div>

<div id="Overview" class="tabcontent" style="display:block">
<div class="tabhtml" markdown="1">

Using p5, we can also create movies by autogenerating several frames and then stitching them together.

Here is an example of auto-generating circles of different colors.  There is a lot here again, but we are using the **saveFrames** function to save each frame as it's drawn to the screen.  Keep in mind that since it runs in the browser, a popup save file window will appear for each frame.

```js
var mainColor = 255;

function setup() {
    createCanvas(640, 480);
    background(0);
    frameRate(25);
    noStroke();
    rectMode(CENTER);
}
function draw() {
    fill(random(mainColor),random(mainColor),random(mainColor), random(100));

    var size= random(200);

    circle(random(width), random(height), size);

    if (frameCount % 2 == 0) {
        mainColor = 255 - mainColor; // 255 0 255 0 255 0 ..
    }
    saveFrames("myMovie",".png",1,25);

    if (frameCount > 25) { // 1 second * 25 fps = 25
        noLoop();
    }
}
```

There's a lot here as well.  How does it work?  

</div>
</div>
<div id="framerate" class="tabcontent">
<div class="tabhtml" markdown="1">

In the first section, the **frameRate** is set so that each frame creates a new images to save.  The **rectMode** also starts the shapes in the middle of the screen.

```js
  createCanvas(640, 480);
  background(120);
  frameRate(25);
  noStroke();
  rectMode(CENTER);
```

</div>
</div>
<div id="draw" class="tabcontent">
<div class="tabhtml" markdown="1">

In this section, random colors are generated and then the circle is drawn onto the canvas.

```js
    fill(random(mainColor),random(mainColor),random(mainColor), random(100));

    var size= random(200);

    circle(random(width), random(height), size);

    if (frameCount % 2 == 0) {
        mainColor = 255 - mainColor; // 255 0 255 0 255 0 ..
    }
    saveFrames("myMovie",".png",1,25);

    if (frameCount > 25) { // 1 second * 25 fps = 25
        noLoop();
    }
```

</div>
</div>
<div id="mod" class="tabcontent">
<div class="tabhtml" markdown="1">


This section switches between colors and no color for a differet effect.  We use the **%** which is modulus operator.  It checks to see if the number is divisible by 2 (i.e. there is no remainder).  If it doesn't have a remainder, then it sets the color to zero and if there is a remainder, then the color is 255.

```js
    if (frameCount % 2 == 0) 
    {
        mainColor = 255 - mainColor; // 255 0 255 0 255 0 ..
    }
```

</div>
</div>
<div id="saveframes" class="tabcontent">
<div class="tabhtml" markdown="1">


This is the main section where each frame is saved so that we can create a movie based on the sketch.

```js
  saveFrames("myMovie",".png",1,25);
```

</div>
</div>
<div id="noloop" class="tabcontent">
<div class="tabhtml" markdown="1">

This last section just checks to see how many frames were produced and stops the draw function from continuing.  This produces 1 second of video creating 25 frames.

```js
  if (frameCount > 25) { // 1 second * 25 fps = 25
      noLoop();
  }
```

</div>
</div>
<div id="todo" class="tabcontent">
<div class="tabhtml" markdown="1">

Now, alter the example from above.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>

</div>
</div>

