---
title: Working with Variables
module: 2
jotted: false
---

# Working with Variables
<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
  
</div>

<div id="Overview" class="tabcontent" style="display:block" >
<div class="tabhtml" markdown="1">
So, how do we work with variables?

```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var diameter = 25;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,200,29);
        circle(x,y,diameter);
   
    }

```

If we change the variable **redColor** then it will give us a different shade of red.


```js
    var redColor = 250;
    var x = 100;
    var y = 100;
    var diameter = 25;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,100,29);
        circle(x,y,diameter);
   
    }

```

However, we can also use the draw method to change the redColor variable for us by incrementing it.  
```js
    var redColor = 0;
    var x = 100;
    var y = 100;
    var diameter = 25;
    function setup()
    {
        createCanvas(800,600);
    }
    function draw()
    {
        background(0);
        fill(redColor,100,29);
        circle(x,y,diameter);
        redColor++;
   
    }

```

What happens?  Go to the next tab and try it out!

</div>
</div>

<div id="ToDo" class="tabcontent" markdown="1">
<div class="tabhtml" markdown="1">

Try the code in the earlier tabs to see the final result

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>
