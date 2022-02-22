---
title: Additional 3D Concepts
module: 8
jotted: false
---

# Additional 3D Concepts

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'custom')">Custom</button>
  <button class="tablinks" onclick="openTab(event, 'textures')">Textures</button>
  <button class="tablinks" onclick="openTab(event, 'text')">Text</button> 
  <button class="tablinks" onclick="openTab(event, 'webgltext')">WebGL text</button>
  <button class="tablinks" onclick="openTab(event, 'lights')">Lights</button> 
  <button class="tablinks" onclick="openTab(event, 'materials')">Materials</button>  
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

### 3D Primitives Shapes

There are 7 different 3D geometry primitives in p5.js.

* box()
* plane()
* sphere()
* ellipsoid()
* cone()
* cylinder()
* torus() 

Each of these primitives take only size parameters, not position. For example:

```js
box(10,20,30); //draws a box of width: 10, height: 20, and depth: 30
cone(40, 100, 100);//draws a cone with radius: 40, height: 100, and a detail of 100
```

You may be saying, “Hey now, what’s this detail you speak of?!” In webgl mode, the user can specify how smooth the curves and lines should be drawn. Larger detail numbers create smoother curves, however at the expense of the graphics renderer. Generally, leaving the default detail is sufficient when drawing primitives:

```js
cone(40,100);//draws a cone with radius: 40, height: 100, and a default detail: 24
```

One important difference between drawing primitives in 3d and drawing primitives in 2d is that 3d primitives take size parameters, but not position. To reposition 3D primitives, simply call **translate(x,y,z);** as per the Translation section from before.

</div>
</div>
<div id="custom" class="tabcontent">
<div class="tabhtml" markdown="1">

### Custom shapes & 2D drawing in WEBGL

In the introduction, we mentioned that WEBGL mode supports both 2D and 3D drawing. While WEBGL is optimized for 3D, you don’t necessarily have to always draw in 3D. For 2D drawing, there are the point(), line(), triangle() and quad() functions. For example,

```js
for(let i = 0; i < 500; i+=100){
  push();
  fill(i * 0.1, 100, 100);

  //line
  translate(0, 100, 0);
  line(-100, 0, i, 100, 0, i);

  //triangles
  translate(0, 100, 0);
  triangle(
    0, sin( i + frameCount * 0.1) * 10, i, 
    60, 60, i, 
    -60, 60, i);

  //quad
  translate(0, 200, 0);
  quad(
    -100, i, 0,
    100, i, 0,
    -100, 100, i,
    100, 100, i
    );
  pop();
}
```

If we look more closely at the quad() function, you’ll notice there are 12 parameters- 4 groups of 3 (x,y,z). Even though we are drawing a 2-dimensional shape, we still need to use the z-coordinate for each vertex.

Another way of drawing custom shapes in WEBGL mode is to use beginShape() and endShape(). This works exactly the same in 2d mode as it does in WEBGL, except in WEBGL, vertices receive x, y, and z as location coordinates.

```js
beginShape();
vertex(100,23,-100);
vertex(200,23,-50);
vertex(150, 45,-100);
endShape();
```

</div>
</div>
<div id="textures" class="tabcontent">
<div class="tabhtml" markdown="1">

### Textures

At the time of this writing, p5.js supports video, image, and offscreen 2d renderers as textures in WEBGL mode. A texture is like a “skin” that wraps around a 3D geometry. For example, if you want a static image to “texture” a box, you would write something like this:

```js
let img;
function preload(){
  img = loadImage(“path/to/img.jpg”);
}
function setup(){
  createCanvas(500,500,WEBGL);
}
function draw(){
  background(255);
  texture(img);
  box(45);
}
```

Loading images for texturing inside the preload() method is generally a best practice, but it is especially helpful when working with video since video files are generally larger than static images and can take therefore extra time to load.

To texture a beginShape() graphic you will need to pass in u,v coordinates. These coordinates map to the texture being applied. With textureMode(NORMAL) we tell p5 to normalize these values between 0 and 1. See the textureMode() reference for more info.

Below is an example:

```js

let img;
function setup() {
  createCanvas(windowWidth, windowHeight, WEBGL);
  img = loadImage("path/to/img.jpg");
  textureMode(NORMAL);
}

function draw() {
  background(200);
  texture(img)

  // Assuming img has 100 pixels width and height
  beginShape();
  vertex(0, 0, 0, 0, 0);
  vertex(100, 0, 0, 1, 0);
  vertex(100, 100, 0, 1, 1);
  vertex(0, 100, 0, 0, 1);
  endShape(CLOSE);
}
```
</div>
</div>
<div id="text" class="tabcontent">
<div class="tabhtml" markdown="1">

### Text

To work with text in webgl mode, you have two options: use the 2d p5.js API to render to an offscreen image, or use the native webgl text() method. There are advantages & disadvantages to both which are discussed below:

#### Offscreen Renderer
You can draw your text to an offscreen renderer first, and then use it as a texture.

#### Advantages:

You can use the same fonts available to the 2d p5.js API, including the browser's built-in fonts (eg, 'mono', 'sans', etc...).
You can use stroke() to draw an outline around the glyphs.
The performance may be better, especially if you are able to render your text only once in setup() and reuse that texture in your draw() function.
Disadvantages:

The fidelity of the text may not be as high as with the text() method due to pixellation when zooming or inaccuracies in anti-aliasing when tilting the text image.
Here is an example of using an offscreen renderer to draw text:

```js
let pg;
function setup(){
  createCanvas(100, 100, WEBGL);
  pg = createGraphics(256,256);
}
function draw(){
  background(0);
  pg.background(255);
  pg.text('hello world!', 50, 50);
  //pass graphics as texture
  texture(pg);
  plane(100);
}
```

</div>
</div>
<div id="webgltext" class="tabcontent">
<div class="tabhtml" markdown="1">

### webgl text()

The webgl version of the text() method works very similarly to the 2d version. However there are a few differences:

**Disadvantages:**

You can only use use opentype/truetype fonts loaded in your preload() function using the loadFont() method. You must either place those font files in a location accessible from your sketch, or use a CORS-compatible webl URL.
stroke() is not currently supported.
Advantages:

The fidelity of the rendered text should be better, especially when zooming & tilting.
The performance may be better, especially if the text changes regularly and you are unable to cache the offscreen image used in the previous method.
Here is an example of loading an opentype font and using it to draw text with the webgl text() method:

```js
let myFont;
function preload() {
  myFont = loadFont('assets/AvenirNextLTPro-Demi.otf');
}

function setup() {
  fill('#ED225D');
  textFont(myFont);
  textSize(36);
  text('p5*js', 10, 50);
}
```

</div>
</div>
<div id="lights" class="tabcontent">
<div class="tabhtml" markdown="1">

### Lights

The last big inclusion in WEBGL mode is lights. Lighting is a simple but powerful way to provide depth and realism to p5.js sketches. At the time of this writing there are 3 types of light functions in p5.js:


* ambientLight();
* directionalLight();
*pointLight();

```js
ambientLight(255,0,0); //even red light across our objects
box(25);
```

**ambientLight()** is the simplest of the three functions, and it provides even (omnidirectional) ambient lighting to objects drawn afterward. It takes a p5.Color or r,g,b numerical values as parameters.

<br>

```js
directionalLight(r, g, b, x, y, z):
let dirY = (mouseY / height - 0.5) *2;
let dirX = (mouseX / width - 0.5) *2;
directionalLight(250, 250, 250, dirX, -dirY, 0.25);
ambientMaterial(250);
sphere(50, 64);
```

**directionalLight** rays shine in a given direction, but they do not have a specific point of origin, and therefore cannot be positioned closer or farther away from a geometry. The directionalLight vector can also be considered the angle in which light hits the geometry. Therefore, a negative y-value will light a given geometry from below.

**pointLight()**: On the other hand, pointLight takes a color and a location as parameters. The major difference between directionalLight and pointLight is pointLight shines from a specific point of origin, and therefore reflects differently when it is farther vs. nearer the object.

</div>
</div>
<div id="materials" class="tabcontent">
<div class="tabhtml" markdown="1">

### Materials

In the real world, light reflects off objects differently, depending on their angle of reflection as well as the object's’ material. At the time of this writing there are four types of materials in p5.js:

* normalMaterial()
* ambientMaterial()
* specularMaterial()

**normalMaterial()** does not take any parameters, it automatically maps a geometry’s normal vectors to RGB colors. For more information on geometry normals, we find this Wikipedia entry to be pretty helpful.

(At one time, there was also a basicMaterial() which fills the following geometry with a color, but is not affected by any of the light functions(). However, due to it being the same as fill(), it was removed and the function fill() can be used with WEBGL for the "basic material" functionality.)

**ambientMaterial()** is like fill(), however the total color is affected by light functions that precede it.

**specularMaterial()** is the most “realistic” of the four materials. Specular material is a technical way of describing a material that reflects light in a single direction. This effect is often perceived in the real world as being glassy, water-like, or perhaps in the above example, a billiards ball. For example:

```js
pointLight(255, 255, 255, mouseX, mouseY, 0);
specularMaterial(250, 0, 0);
sphere(50, 64);
```
</div>
</div>

