---
title: Animation Decisions
module: 5
jotted: false
---

# Changing Animations

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'step1')">Step 1</button>
  <button class="tablinks" onclick="openTab(event, 'step2')">Step 2</button>
  <button class="tablinks" onclick="openTab(event, 'step3')">Step 3</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 
</div>
<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

Remember in the last section, we were able to make the idle appear, but what do we need to do to make a different animation appear.  If you recall from last week, we had to create a second array to hold the run animation.

We can do the same thing, but read in a different file and then populate the run array.  What might this look like?

We will still use the `imageclass.js` and we will create a new file for running.

</div>
</div>

<div id="step1" class="tabcontent">
<div class="tabhtml" markdown="1">

```js
Run (1).png
Run (2).png
Run (3).png
Run (4).png
Run (5).png
Run (6).png
Run (7).png
Run (8).png

```

This time, we will call this file, **characterrun.txt**

</div>
</div>
<div id="step2" class="tabcontent">
<div class="tabhtml" markdown="1">

We will read this file in just like we did with the idle file.

```js
var cowGirlObjects = [];
var cowGirlRunObjects = [];
var currentObjects = [];
var result;
var runresult;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
  for(var i = 0; i < result.length; i++)
  {
    cowGirlObjects.push(new imageclass(result[i], 0, 0));
  }
  for(var i = 0; i < runresult.length; i++)
  {
    cowGirlRunObjects.push(new imageclass(runresult[i], 0, 0));
  }
}

function setup() {
  background(200);
  setInterval(incrementIndex, 50);

}

// display all the frames using the draw function as a loop
function draw() 
{

    background(120);
    
    if(keyIsPressed)
    {
        if(key == "d")
        {
            currentObjects = cowGirlRunObjects;
        }
    }
    else
    {
        currentObjects = cowGirlObjects;
    }
    image(currentObjects[i].getImage(), currentObjects[i].getX(), currentObjects[i].getY());
}


function incrementIndex()
{
     // increment the index
     i += 1;

     // if we reach the end of the array, start over
     if (i >= animation.length) {
         i = 0;
     }
}

```

</div>
</div>
<div id="step3" class="tabcontent">
<div class="tabhtml" markdown="1">

What happens if we press the `a` key and go the other way.  We want the character to flip. How are we going to do that?

The nice thing about p5.js is that we can use two lines of code that will help us

#### translate

The first one is translate.  This will move the character or image to a different part of the screen.  However, keep in mind that it will require you to keep track of where you are on the screen at all times.  This is a simple example below.

```js
translate(width,0); // move to far corner
```

In this case, it moves it to the far corner of the canvas and leaves the y-coordinate the same as it was before.

#### scale

The second line is the scale.  It is typically used to make an image larger or smaller, but we can also flip horizontally or vertically if we want.  We just change the sign of the x or y coordinate.

```js
scale(-1.0,1.0);    // flip x-axis backwards
```

In this case, we are keeping the image the same size, but flipping the direction of the x coordinate so that it is opposite of what it was originally.

So, how does this look in a simple example?

```js
var myImage;
var x = 100;
var y = 100;
function preload() 
{
    // assume we have an Idle (1).png in our assets folder
    myImage = loadImage("./assets/Idle (1).png");
}

function setup() 
{
  createCanvas(800,600);
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
    if(keyIsPressed)
    {
        if(key == "a")
        {
            // move the character to the width of the character so that it can flip
            translate(myImage.width,0); 
            scale(-1.0,1.0);    // flip x-axis backwards
            image(myImage,x,y);
        }
    }
    else
    {
        // go back to the original orientation
        image(myImage,x,y);
    }    
}

```

So, we can see in this example that we can flip a single image by just moving it over to the right by its width and then translating it.

However, for our assignment, you can just flip your images and create another animation that moves the opposite way.  

</div>
</div>
<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tabs to see the final result. Feel free to change values.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>