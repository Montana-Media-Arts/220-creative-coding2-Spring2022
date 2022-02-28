---
title: p5.play collisions 
module: 7
jotted: false
---

# Collisions in p5.play

So, how do we deal with collisions?  In  p5.play, they have a built-in collision function.

First, let's add a new image.

```js

var cowGirlObjects;
var result, runresult;
var rock;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = createSprite(300, 250);
    cowGirlObjects.addAnimation('idle', result[0], result[result.length-1]);
    cowGirlObjects.addAnimation('run', runresult[0], runresult[runresult.length-1]);

    rock = createSprite(700, 300);
    //compact way to add an image
    rock.addImage(loadImage('assets/rock.png'));
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

However, if we move, we will walk right through the rock. That won't work!

So, what will we do?  We can use the `collide` function and that will check to see if two objects have collided.

```js
var cowGirlObjects;
var result, runresult;
var rock;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = createSprite(300, 250);
    cowGirlObjects.addAnimation('idle', result[0], result[result.length-1]);
    cowGirlObjects.addAnimation('run', runresult[0], runresult[runresult.length-1]);

    rock = createSprite(700, 300);
    //compact way to add an image
    rock.addImage(loadImage('assets/rock.png'));
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
   
    if(keyDown('d'))
    {
      cowGirlObjects.changeAnimation('run');
      cowGirlObjects.velocity.x += .5;
      if(cowGirlObjects.collide(rock))
      {
        cowGirlObjects.changeAnimation('idle');
      }
    }
    else
    {
      cowGirlObjects.changeAnimation('idle');
      cowGirlObjects.velocity.x = 0;
    }

    cowGirlObjects.debug = mouseIsPressed;
    rock.debug = mouseIsPressed;
    drawSprites();
}
```

**Note** We also added the debug at the bottom so we can see the bounding boxes on the sprites.  This will tell us where they are colliding.  Now, I am going to let you know work with the play library.