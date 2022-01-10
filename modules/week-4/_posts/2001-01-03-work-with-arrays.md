---
title: Working with Arrays
module: 4
jotted: true
---

# Work with Arrays

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'Step1')">Step 1</button>
  <button class="tablinks" onclick="openTab(event, 'Step2')">Step 2</button>
  <button class="tablinks" onclick="openTab(event, 'Step3')">Step 3</button>
  <button class="tablinks" onclick="openTab(event, 'Step4')">Step 4</button>
  <button class="tablinks" onclick="openTab(event, 'Step5')">Step 5</button>
  <button class="tablinks" onclick="openTab(event, 'Step6')">Step 6</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">
So, how are we going to work with them.  Let's start with a simple example of displaying shapes and then we will work with our dogs.

</div>
</div>

<div id="Step1" class="tabcontent" >
<div class="tabhtml" markdown="1">

So, let's create a simple shape class.

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
</div>
</div>

<div id="Step2" class="tabcontent" >
<div class="tabhtml" markdown="1">
Let's test this out and see if it works.

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
var circle1 = new myCircle(100,100,25, 120, 34,100);

function setup()
{
    createCanvas(800,600);
}

function draw()
{
    background(0);
    circle1.draw();
}
```

Did it work?  Great!

</div>
</div>

<div id="Step3" class="tabcontent" >
<div class="tabhtml" markdown="1">

Now, let's create a couple of circles and make sure it works.

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
var circle1 = new myCircle(100,100,25, 120, 34,100);
var circle2 = new myCircle(200,200,125, 220, 134,10);
function setup()
{
    createCanvas(800,600);
}

function draw()
{
    background(0);
    circle1.draw();
    circle2.draw();
}
```

So, I just copy and pasted and another circle appeared!

I could continue doing this, but what if I wanted to use an array?

</div>
</div>

<div id="Step4" class="tabcontent" >
<div class="tabhtml" markdown="1">

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
var myCircles = []; // declare a circle array
myCircles[0] = circle1 = new myCircle(100,100,25, 120, 34,100); // add a circle to index 0
myCircles[1] = circle2 = new myCircle(200,200,125, 220, 134,10); // add a circle to index 1
function setup()
{
    createCanvas(800,600);
}

function draw()
{
    background(0);
    myCircles[0].draw();
    myCircles[1].draw();
}

```

Now, this is all fine, but where does the power of arrays come in?  It almost seems like the same as before.

</div>
</div>

<div id="Step5" class="tabcontent" >
<div class="tabhtml" markdown="1">
Let's try this:

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
var myCircles = []; // declare a circle array
myCircles[0] = circle1 = new myCircle(100,100,25, 120, 34,100); // add a circle to index 0
myCircles[1] = circle2 = new myCircle(200,200,125, 220, 134,10); // add a circle to index 1
function setup()
{
    createCanvas(800,600);
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

Okay, what did I do? I added a for loop in the draw and then printed out all the circles in the array using **i** as my index instead of putting the actual numbers in there.

</div>
</div>

<div id="Step6" class="tabcontent" >
<div class="tabhtml" markdown="1">
Can we do more?  Of course we can.


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
var myCircles = []; // declare a circle array

function setup()
{
    createCanvas(800,600);
    for(var i = 0; i < 5; i++)
    {
        myCircles[i] = new myCircle(random(10,100),random(10,200),random(5,25), random(255), random(255),random(255)); //
    }
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

Now, what did I do?  I created 5 random circles of random colors and put them in random places. I used two for loops to create and then display the circles.

In the next section change the 5 to some other number.  What happens?
</div>
</div>

<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tabs to see the final result. Feel free to change values.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>

