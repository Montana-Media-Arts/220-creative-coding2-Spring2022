---
title: Built-in Functions
module: 2
jotted: true
---

# Built-in Functions
<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'random')">random</button>
  <button class="tablinks" onclick="openTab(event, 'abs')">abs</button>
  <button class="tablinks" onclick="openTab(event, 'round')">round</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
  
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">
In p5.js there are a number of different built-in functions that can help us perform actions and make our programs more sophisticated.
</div>
</div>
<div id="random" class="tabcontent" >
<div class="tabhtml" markdown="1">


The first one we will look at is the **random** function.

In the reference material, it is defined like this:

* Return a random floating-point number.
* Takes either 0, 1 or 2 arguments.
* If no argument is given, returns a random number from 0 up to (but not including) 1.
* If one argument is given and it is a number, returns a random number from 0 up to (but not including) the number.
* If one argument is given and it is an array, returns a random element from that array.
* If two arguments are given, returns a random number from the first argument up to (but not including) the second argument.

An example is might look like this

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    function setup()
    {
        createCanvas(800,600);
        fill(redColor,100,29);
        for(var i = 0; i < 5; i++)
        {
            rect(x,y,side);
            x+=random(50);
            y+=random(50);
        }
        
    }
    function draw()
    {
    }

```

</div>
</div>
<div id="abs" class="tabcontent" >
<div class="tabhtml" markdown="1">

Calculates the absolute value (magnitude) of a number. Maps to Math.abs(). The absolute value of a number is always positive.

This function is most useful when we want to determine the distance between two points and with inequalities.

Let's look at an example:

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    var previousX = x;
    var textY = 400;
    function setup()
    {
        createCanvas(800,600);
        fill(redColor,100,29);
        for(var i = 0; i < 5; i++)
        {
            rect(x,y,side);
            x+=random(50);
            y+=random(50);
            text("distance between X: " + abs(previousX-x), 200,textY)
            textY += 20;
            previousX = x;
        }
         
    }
    function draw()
    {
    }

```


</div>
</div>
<div id="round" class="tabcontent" >
<div class="tabhtml" markdown="1">

The last one is the round function which rounds a decimal number to a whole number or to a specific decimal place depending on the parameters that are sent into the function.

Here is simple example that returns a whole number:

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    var previousX = x;
    var textY = 400;
    function setup()
    {
        createCanvas(800,600);
        fill(redColor,100,29);
        for(var i = 0; i < 5; i++)
        {
            rect(x,y,side);
            x+=random(50);
            y+=random(50);
            text("distance between X: " + round(abs(previousX-x)), 200,textY)
            textY += 20;
            previousX = x;
        }
         
    }
    function draw()
    {
    }

```

In this example, this returns numbers with 3 decimal points.

Here is simple example that returns a whole number:

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    var previousX = x;
    var textY = 400;
    function setup()
    {
        createCanvas(800,600);
        fill(redColor,100,29);
        for(var i = 0; i < 5; i++)
        {
            rect(x,y,side);
            x+=random(50);
            y+=random(50);
            text("distance between X: " + round(abs(previousX-x),3), 200,textY)
            textY += 20;
            previousX = x;
        }
         
    }
    function draw()
    {
    }

```

There are just a few built-in functions. There many more and if you are interested, please visit: <a href="https://p5js.org/reference/" target="_new">p5.js Reference</a>

</div>
</div>

<div id="ToDo" class="tabcontent" markdown="1">
<div class="tabhtml" markdown="1">

Try the code in the earlier tabs to see the final result. Feel free to change numbers.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>
