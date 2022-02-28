---
title: Applying p5.play
module: 7
jotted: false
---

# Applying p5.play

So, let's look at what we did.

```js
var cowGirlObjects = [];
var animation = [];
var result;
var i = 0;
function preload() {
  result = loadStrings('assets/characteridle.txt');
}

function setup() {
  createCanvas(800,600);
  for(var i = 0; i < result.length; i++)
  {
    cowGirlObjects.push(new imageclass('assets/' + result[i], 0, 0));
    animation[i] = cowGirlObjects[i].getImage();
  }
  setInterval(incrementIndex, 50);

}

// display all the frames using the draw function as a loop
function draw() 
{

    background(120);
    image(animation[i], cowGirlObjects[i].getX(), cowGirlObjects[i].getY());
}


function incrementIndex()
{
     // increment the index
     i += 1;

     // if we reach the end of the array, start over
     if (i >= cowGirlObjects.length) {
         i = 0;
     }
}

```

This hopefully didn't seem like too big a deal at the time right?

What would it look like in p5.play?

```js

var cowGirlObjects
var result;
function preload() {
  result = loadStrings('assets/characteridle.txt');
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = loadAnimation('assets/' + result[0], 'assets/' + result[1], 'assets/' + result[2], 'assets/' + result[3], 'assets/' + result[4], 'assets/' + result[5], 'assets/' + result[6],'assets/' + result[7],'assets/' + result[8],'assets/' + result[9]);
}

// display all the frames using the draw function as a loop
function draw() 
{
    background(120);
    animation(cowGirlObjects, 300, 250);
}

```

Okay so maybe that is a little cleaner.  Can we make it even more automated?

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
What just happened?  That was pretty cool right?  We didn't have to list out all the assets one by one.  First though, I had to change the file names because they had spaces in them and I had to make a change to the text file.  It looks like this now.  I also added the path to the file.  Cleaner right?

```js

assets/Idle1.png
assets/Idle2.png
assets/Idle3.png
assets/Idle4.png
assets/Idle5.png
assets/Idle6.png
assets/Idle7.png
assets/Idle8.png
assets/Idle9.png
assets/Idle10.png

```

Then, in the loadAnimation, we can call the first frame which in this case is Idle1.png and the last frame Idle10.png and the loadAnimation will find fill in the other frames automatically.  That's cool!

