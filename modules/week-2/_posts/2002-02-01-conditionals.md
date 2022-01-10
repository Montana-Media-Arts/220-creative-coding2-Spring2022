---
title: Conditionals
module: 2
jotted: false
---

# Conditionals

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'if')">If</button>
  <button class="tablinks" onclick="openTab(event, 'ifelse')">If/Else</button>
  <button class="tablinks" onclick="openTab(event, 'elseif')">Else-If</button>
  <button class="tablinks" onclick="openTab(event, 'switch')">Switch</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
  
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">
Let's start with the original example from last time.

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,100,29);
        rect(x,y,side);
   
    }

```
</div>
</div>
<div id="if" class="tabcontent" >
<div class="tabhtml" markdown="1">


In the last section, we changed the **redColor** variable.  We can do that again, but we will use control statements to help us with it.

The first one is the **if** statement.  We can always say things like "If you are hungry, eat a sandwich" or something like that.


```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,100,29);
        rect(x,y,side);
        redColor++;
        // reset the red section of the rgb
        if(redColor > 255)
        {
            redColor = 0;
        }
   
    }

```
</div>
</div>

<div id="ifelse" class="tabcontent" >
<div class="tabhtml" markdown="1">

In the first section, we looked at the if statement by changing the **redColor** variable.  Now, we can look at the other side, the **else** statement.  It cannot be used alone. However, it can be used with an if statement.  

Using our first analogy, we can say, if I am hungry, I will eat a sandwhich else, I will wait until later.

How does this look in code?

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,100,29);
        rect(x,y,side);
        // reset the red section of the rgb
        if(redColor > 255)
        {
            redColor = 0;
        }
        else
        {
            redColor++;
        }
   
    }

```
</div>
</div>

<div id="elseif" class="tabcontent" >
<div class="tabhtml" markdown="1">

In this section, we will look at the **else-if** control structure.  This work like an if/else, but it makes our code more concise. 

You can think of it like this, if it's rainy out, wear a rain jacket, else if it's snowing out, then wear a heavy jacket, else if it's sunny out, leave the jacket at home!

What does this look like in code? In order to see it, let's create variables for green and blue too.

```js
    var redColor = 0;
    var greenColor = 0;
    var blueColor = 0;
    var x = 100;
    var y = 100;
    var side = 50;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,greenColor,blueColor);
        rect(x,y,side);
        // reset the red section of the rgb
        if(redColor > 255)
        {
            redColor = 0;
        }
        else if(greenColor > 255)
        {
            greenColor = 0;
        }
        else if(blueColor > 255)
        {
            blueColor = 0;
        }
            // notice I am incrementing red by 1
            redColor++;
            // I can increment green by 2 like this
            greenColor = greenColor + 2;
            // I can also increment blue by three like this
            blueColor += 3;
        
   
    }

```

</div>
</div>
<div id="switch" class="tabcontent" >
<div class="tabhtml" markdown="1">

In the previous section, we looked at else-if and now we will change to looking at another control structure that functions in a similar fashion, the **switch**.  This is handy when it comes to menu type items and numbers.

Let's look at another analogy.  Switch statements work like if statements, in 
How does this look in code?

```js
   var redColor = 0;
    var greenColor = 100;
    var blueColor = 100;
    var x = 100;
    var y = 100;
    var side = 50;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,greenColor,blueColor);
        rect(x,y,side);
        // update the red section of the rgb
        switch(redColor)
        {
            case 10:
                redColor = 200;
                break;
            case 100:
                redColor = 10;
                break;
            case 200:
                redColor = 100;
                break;
          default:
                redColor = 10;
        }
    }
```

There are a couple things to note.  All the items you want to compare must start with a **case** keyword and you have to have a **break** statement after each case or it will continue looking until it gets to the default.


</div>
</div>


<div id="ToDo" class="tabcontent" markdown="1">
<div class="tabhtml" markdown="1">

Try the code in the earlier tabs to see the final result. Feel free to change numbers.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>

