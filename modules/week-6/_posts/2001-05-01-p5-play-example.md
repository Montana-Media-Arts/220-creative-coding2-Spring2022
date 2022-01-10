---
title: Example
module: 6
jotted: false
---

# Example

So, what might an example look like and how do we break it down.

One simple example might be like this.

```js
//Creating animations

//animations like p5 images should be stored in variables
//in order to be displayed during the draw cycle
var ghost, asterisk;

//it's advisable (but not necessary) to load the images in the preload function
//of your sketch otherwise they may appear with a little delay
function preload() {

  //create an animation from a sequence of numbered images
  //pass the first and the last file name and it will try to find the ones in between
  ghost = loadAnimation('assets/ghost_standing0001.png', 'assets/ghost_standing0007.png');

  //create an animation listing all the images files
  asterisk = loadAnimation('assets/asterisk.png', 'assets/triangle.png', 'assets/square.png', 'assets/cloud.png', 'assets/star.png', 'assets/mess.png', 'assets/monster.png');
}

function setup() {
  createCanvas(800, 300);
}

function draw() {
  background(255, 255, 255);

  //specify the animation instance and its x,y position
  //animation() will update the animation frame as well
  animation(ghost, 300, 150);
  animation(asterisk, 500, 150);
}

```

So, what happened here.

First, two variables are created to hold the animations.

```js
var ghost, asterisk;
```

Then, they load the animations by using a built-in function called `loadAnimation` in the preload function just like we did before when we loaded images.

```js

ghost = loadAnimation('assets/ghost_standing0001.png', 'assets/ghost_standing0007.png');

asterisk = loadAnimation('assets/asterisk.png', 'assets/triangle.png', 'assets/square.png', 'assets/cloud.png', 'assets/star.png', 'assets/mess.png', 'assets/monster.png');

```

The setup function remains the same and then the draw function contains two more functions that displays the animations.

```js
  animation(ghost, 300, 150);
  animation(asterisk, 500, 150);
```

The animation is displayed in a specific x and y location.

How can we apply this to our example?
