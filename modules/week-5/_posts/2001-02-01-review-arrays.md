---
title: Review Arrays
module: 5
jotted: false
---


# Arrays
<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'push')">push</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">
Now, I hope you are convinced that arrays are incredibly powerful and helpful especially when we are talking about keeping track of a large number of variables.  It's so much better!

So, what did we do prior?

Last week did something like this.

#### mycircle.js

```js
class myCircle
{
    constructor(x,y, diameter, redColor, greenColor, blueColor)
    {
        this.x = x;
        this.y = y;
        this.diameter = diameter;
        this.redColor = redColor;
        this.greenColor = greenColor;
        this.blueColor = blueColor;
    }

    draw()
    {
        fill(this.redColor, this.greenColor, this.blueColor);
        circle(this.x,this.y,this.diameter);
    }
}

```

And then we used the class by doing this.

#### sketch.js

```js
var myCircles = []; // declare a circle array
myCircles[0] = new myCircle(100,100,25, 120, 34,100); // add a circle to index 0
var circle2 = new myCircle(200,200,125, 220, 134,10); // add a circle to index 1

myCircles[1] = circle2;

function setup()
{
    createCanvas(800,600);
}

function draw()
{
    background(0);
    for(var i = 0; i < myCircles.length; i++)
    myCircles[i].draw();
}
```

</div>
</div>
<div id="push" class="tabcontent">
<div class="tabhtml" markdown="1">

In the previous example, we added each object to a specific index in the array. That defnitely works, but we can also use the function `push` and that will add the object to the array as well. 

```js

var myCircles = []; // declare a circle array

function setup()
{
    createCanvas(800,600);
    var circle1 = new myCircle(100,100,25, 120, 34,100); // add a circle to index 0
    myCircles.push(circle1);

    myCircles.push(new myCircle(200,200,125, 220, 134,10)); // add a circle to index 1

}

function draw()
{
    background(0);
    for(var i = 0; i < myCircles.length; i++)
    {
        myCircles[i].draw();
    }
    
}

```

There are a couple of things to notice.  In the setup, I create a circle object, assigned it to a variable, and then pushed it onto the array.  In the next line, I didn't create a variable, I just pushed the object directly into the array. Both are valid and you are welcome to do either.

Then, in the draw, the objects are drawn.  The opposite function to `push` is `pop`, but if you pop the objects off the array, they are no longer in the array so that is why I used the for loop to display the objects.

We will revisit this in a just a bit.

</div>
</div>
<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tabs to see the final result. Feel free to change values.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>