---
title: Review and Destroy
module: 8
jotted: false
---

# Review
<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'destroy')">destroy</button>
  <button class="tablinks" onclick="openTab(event, 'remove')">remove</button>
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

At this point, your code displays an animation and randomized immovable objects. The character should be unable to move through the objects.

What does the code look like?

```js

var cowGirlObjects;
var result, runresult, runresultleft, attackresult;
var rock;
function preload() {
  result = loadStrings('assets/characteridle.txt');
  runresult = loadStrings('assets/characterrun.txt');
  runresultleft = loadStrings('assets/characterrunleft.txt');
  attackresult = loadStrings('assets/characterattack.txt');
  
}

function setup() {
    createCanvas(800,600);  
    cowGirlObjects = createSprite(300, 250);
    cowGirlObjects.addAnimation('idle', result[0], result[result.length-1]);
    cowGirlObjects.addAnimation('run', runresult[0], runresult[runresult.length-1]);
    cowGirlObjects.addAnimation('left', runresultleft[0], runresultleft[runresultleft.length-1]);
    cowGirlObjects.addAnimation('attack', attackresult[0], attackresult[attackresult.length-1]);

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
    else if(keyDown('a'))
    {
      cowGirlObjects.changeAnimation('left');
      cowGirlObjects.velocity.x -= .5;
      if(cowGirlObjects.collide(rock))
      {
        cowGirlObjects.changeAnimation('idle');
      }
    }
    else if(keyDown('x'))
    {
      cowGirlObjects.changeAnimation('attack');
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

At the moment, I can move the character to the left and right and attack. It also places an object on the screen. However, how do we destroy the object when it is attacked?  Eventually we are going to integrate the particle system, but for now, let's just remove it.

</div>
</div>

<div id="destroy" class="tabcontent">
<div class="tabhtml" markdown="1">

### Destroy

The code that is most important is the attack.

```js
    else if(keyDown('x'))
    {
      cowGirlObjects.changeAnimation('attack');
    }
```

With the p5 play library and the p5.js library, we can get all the information we need.

We are going to use the `dist` function to determine if we are close enough to destroy the object.

So, the code will look like this now.

```js
    else if(keyDown('x'))
    {
      cowGirlObjects.changeAnimation('attack');
      if(dist(cowGirlObjects.position.x,cowGirlObjects.position.y,rock.position.x,rock.position.y) < 250)
      {
        console.log("destroy");
      } 
    }
```

The `dist` function needs two points the first point (x,y) will be the location of the character.  The second point (x,y) will be the obstacle.  I am checking to see if it's less than 250 pixels away. If it is, then destroy it.  This may vary for you.

At the moment, I am just printing out **destroy**.  Not very intimating.  How do I remove it?

</div>
</div>

<div id="remove" class="tabcontent">
<div class="tabhtml" markdown="1">


#### remove

We are going to use the `remove` function in p5.js.  If you use the **remove** without any other parameters, the whole sketch will be removed. However, we can use the dot operator to remove just one item. In this case, the obstacle.

So, now our code will look like this.

```js
  else if(keyDown('x'))
    {
      cowGirlObjects.changeAnimation('attack');
      if(dist(cowGirlObjects.position.x,cowGirlObjects.position.y,rock.position.x,rock.position.y) < 250)
      {
        rock.remove();
        rock = null;
      } 
    }
```

Now, when the `x` key is pressed, if the character is close enough to the rock, it will disappear and the reference to the rock is set to nothing so the character won't stop.  We will have to change a few other sections too though. We must check to make sure the rock is not null whenever we evaluate collision. The entire section will look like this now.

```js

function draw() 
{
    background(120);
   
    if(keyDown('d'))
    {
      cowGirlObjects.changeAnimation('run');
      cowGirlObjects.velocity.x += .5;
      if(rock != null)
      {
        if(cowGirlObjects.collide(rock))
        {
          cowGirlObjects.changeAnimation('idle');
        }
      }
      
    }
    else if(keyDown('a'))
    {
      cowGirlObjects.changeAnimation('left');
      cowGirlObjects.velocity.x -= .5;
      if(rock != null)
      {
        if(cowGirlObjects.collide(rock))
        {
          cowGirlObjects.changeAnimation('idle');
        }
      }
      
    }
    else if(keyDown('x'))
    {
      cowGirlObjects.changeAnimation('attack');
     
      if(rock != null)
      {
        if(dist(cowGirlObjects.position.x,cowGirlObjects.position.y,rock.position.x,rock.position.y) < 250)
        {
          
          rock.remove();
          rock = null;
        }
      }
    }
    else
    {
      cowGirlObjects.changeAnimation('idle');
      cowGirlObjects.velocity.x = 0;
    }

    cowGirlObjects.debug = mouseIsPressed;
    drawSprites();
}
```

Pretty cool right?  How do we integrate our particle system?

</div>
</div>

