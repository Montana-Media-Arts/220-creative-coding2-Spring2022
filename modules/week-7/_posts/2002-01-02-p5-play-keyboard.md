---
title: p5.play keyboard 
module: 6
jotted: false
---

# Using the keyboard in p5.play

So, in order to make an animation change, we have to create two different animations and then move along the x or y axis just like before.  So, let's add onto what we started with.

```js

var cowGirlObjects
var result;
function preload() {
  result = loadStrings('assets/characteridle.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = loadAnimation(result[0], result[result.length-1]);
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
    animation(cowGirlObjects, 300, 250);
}

```

In order to add a run animation, we have to make a few modifications.  We are going to create a sprite with two different states.  Then, we can change states when the keys are pressed.  It looks like this now.

```js
var cowGirlObjects;
var result, runresult;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = createSprite(300, 250);
    cowGirlObjects.addAnimation('idle', result[0], result[result.length-1]);
    cowGirlObjects.addAnimation('run', runresult[0], runresult[runresult.length-1]);
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
   
    if(keyDown('d'))
    {
      cowGirlObjects.changeAnimation('run');
    }
    else
    {
      cowGirlObjects.changeAnimation('idle');
    }

    drawSprites();
}
```

Now, how do we make it move while we run?  We can just change the velocity of the x-coordinate.  However, what happens when we do that?

```js
var cowGirlObjects;
var result, runresult;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = createSprite(300, 250);
    cowGirlObjects.addAnimation('idle', result[0], result[result.length-1]);
    cowGirlObjects.addAnimation('run', runresult[0], runresult[runresult.length-1]);
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
   
    if(keyDown('d'))
    {
      cowGirlObjects.changeAnimation('run');
      cowGirlObjects.velocity.x += .5;
    }
    else
    {
      cowGirlObjects.changeAnimation('idle');
    }

    drawSprites();
}
```

In this scenario, the velocity just continues even when we release the key.  Wow, it can really fast. Just change the .5.  So, how can we make it stop?

```js

var cowGirlObjects;
var result, runresult;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = createSprite(300, 250);
    cowGirlObjects.addAnimation('idle', result[0], result[result.length-1]);
    cowGirlObjects.addAnimation('run', runresult[0], runresult[runresult.length-1]);
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
   
    if(keyDown('d'))
    {
      cowGirlObjects.changeAnimation('run');
      cowGirlObjects.velocity.x += .5;
    }
    else
    {
      cowGirlObjects.changeAnimation('idle');
      cowGirlObjects.velocity.x = 0;
    }

    drawSprites();
}

```

We set the velocity back to 0.  Whew. that's better!  What about collisions?

