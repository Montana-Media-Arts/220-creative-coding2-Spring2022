---
title: Create an Image
module: 14
jotted: true
---

# Create an Image

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'createcolor')">writeColor</button>
  <button class="tablinks" onclick="openTab(event, 'drawshapes')">drawShapes</button>
  <button class="tablinks" onclick="openTab(event, 'callcreatecolor')">Call writeColor</button>
  <button class="tablinks" onclick="openTab(event, 'borders')">Borders</button>
  <button class="tablinks" onclick="openTab(event, 'calldrawshapes')">Call drawShapes</button>
  <button class="tablinks" onclick="openTab(event, 'update')">Update</button>
  <button class="tablinks" onclick="openTab(event, 'todo')">To Do</button>
</div>

<div id="Overview" class="tabcontent" style="display:block">
<div class="tabhtml" markdown="1">

Using p5, we can create an NFT using the p5.Image and createImage function.

Here is a short example based on the one in the p5 js reference


```js
function setup() {
  let img = createImage(800, 600); // same as new p5.Image(800, 600);
  img.loadPixels();
  createCanvas(800, 600);
  background(0);

  // helper for writing color to array
  function writeColor(image, x, y, red, green, blue, alpha) 
  {
    let index = (x + y * width) * 4;
    image.pixels[index] = red;
    image.pixels[index + 1] = green;
    image.pixels[index + 2] = blue;
    image.pixels[index + 3] = alpha;
  }

  // this function draws random squares within squares on the canvas
  function drawShapes(number1, number2) {
    let startX = floor(random(number1-10)) + 10;
    let startY = floor(random(number2-20)) + 20;
    console.log(startX);
    // draw shapes
    for (x = startX; x < startX + 70; x++) {
      for (y = startY; y < startY + 70; y++) {
        if (x > startX + 10 && x < startX + 25 && y > startY + 10 && y < startY + 25) {
          writeColor(img, x, y, 50, 100, 50, floor(random(255)));
        } else {
          writeColor(img, x, y, 55, 20, 125, floor(random(255)));
        }
      }
    }
  }

  let x, y;
  // fill with random colors
  for (y = 0; y < img.height; y++) {
    for (x = 0; x < img.width; x++) {
      let red = random(255);
      let green = random(255);
      let blue = random(255);
      let alpha = 255;
      writeColor(img, x, y, red, green, blue, alpha);
    }
  }

  // draw upper border line
  for(y = 0; y < 5; y++)
  {
    for (x = 0; x < img.width; x++) 
    {
      writeColor(img, x, y, 255, 0, 0, 255);
    }
  }

  // draw a bottom border line
  y = img.height - 1;
  for(let i = 0; i < 5; i++)
  {
    for (x = 0; x < img.width; x++) 
    {
      writeColor(img, x, y, 255, 0, 0, 255);
    }
    y--;
  }

  // draw shapes
  for (var i = 0; i < 50; i++) {
    drawShapes(floor(random(width)), floor(random(height)));
  }

  img.updatePixels();
  image(img, 0, 0);
}
```

There's a lot to unpack here.  How does it work?

</div>
</div>
<div id="createcolor" class="tabcontent">
<div class="tabhtml" markdown="1">


First, we use the **writeColor** function to create a functional image that we can add the colors and the alpha value to each individual pixel.

```js
// helper for writing color to array
  function writeColor(image, x, y, red, green, blue, alpha) {
    let index = (x + y * width) * 4;
    image.pixels[index] = red;
    image.pixels[index + 1] = green;
    image.pixels[index + 2] = blue;
    image.pixels[index + 3] = alpha;
  }
```

</div>
</div>
<div id="drawshapes" class="tabcontent">
<div class="tabhtml" markdown="1">

Then, the **drawShapes** function displays various shapes randomly throughout the image.

```js
// this function draws random squares within squares on the canvas
  function drawShapes(number1, number2) {
    let startX = floor(random(number1-10)) + 10;
    let startY = floor(random(number2-20)) + 20;
    console.log(startX);
    // draw shapes
    for (x = startX; x < startX + 70; x++) {
      for (y = startY; y < startY + 70; y++) {
        if (x > startX + 10 && x < startX + 25 && y > startY + 10 && y < startY + 25) {
          writeColor(img, x, y, 50, 100, 50, floor(random(255)));
        } else {
          writeColor(img, x, y, 55, 20, 125, floor(random(255)));
        }
      }
    }
  }
```

</div>
</div>
<div id="callcreatecolor" class="tabcontent">
<div class="tabhtml" markdown="1">

In this section, randomly colored pixels are generated and sent to the writeColor function. Keep in mind the **writeColor** function is called and the location, the color, and alpha value of each pixel is sent in.

```js
let x, y;
  // fill with random colors
  for (y = 0; y < img.height; y++) {
    for (x = 0; x < img.width; x++) {
      let red = random(255);
      let green = random(255);
      let blue = random(255);
      let alpha = 255;
      writeColor(img, x, y, red, green, blue, alpha);
    }
  }
```

</div>
</div>
<div id="borders" class="tabcontent">
<div class="tabhtml" markdown="1">

Here we draw the upper and lower borders.  Examine this closely as it creates another double for loop to make the lines thicker.

```js
 // draw upper border line
  for(y = 0; y < 5; y++)
  {
    for (x = 0; x < img.width; x++) 
    {
      writeColor(img, x, y, 255, 0, 0, 255);
    }
  }

  // draw a bottom border line
  y = img.height - 1;
  for(let i = 0; i < 5; i++)
  {
    for (x = 0; x < img.width; x++) 
    {
      writeColor(img, x, y, 255, 0, 0, 255);
    }
    y--;
  }
```

</div>
</div>
<div id="calldrawshapes" class="tabcontent">
<div class="tabhtml" markdown="1">

Then, we called the **drawShapes** function to create the random shapes on the screen.

```js
  // draw shapes
  for (var i = 0; i < 50; i++) {
    drawShapes(floor(random(width)), floor(random(height)));
  }
```

</div>
</div>
<div id="update" class="tabcontent">
<div class="tabhtml" markdown="1">

Finally, in this last section, the pixels are updates in the image so that it can be displayed on the canvas.

```js
  img.updatePixels();
  image(img, 0, 0);
```

</div>
</div>
<div id="todo" class="tabcontent">
<div class="tabhtml" markdown="1">

Now, feel free to alter the example from above.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>

</div>
</div>
