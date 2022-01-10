---
title: Review Classes and Objects
module: 5
jotted: false
---

# Review Classes and Objects

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'Separate')">Separate Files</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

If we recall from last, week, we talked about classes and objects.  Recall, a class is a blueprint or template for an object and contain **properties** and **functions**.  

Whereas, the formal definition of an object is the following. An object is a specific instance of a class.

We had a couple of examples, specically around a dog.

```js

class Dog {
  constructor(name, breed, weight, eyeColor, hairColor ) {
    this.name = name;
    this.breed = breed;
    this.weight = weight;
    this.eyeColor = eyeColor;
    this.hairColor = hairColor;
  }

  eat()
  {
    text(this.name + "is eating...", 100, 100);
  }

  sleep()
  {
    text(this.name + " is sleeping...", 200, 200);
  }
}

var leonberger = new Dog("Alice", "Leonberger", 70, "brown", "brown");

var lab = new Dog ("Lucy", "Lab", 35, "black", "black");

function setup()
{
  createCanvas(800,600);
}

function draw()
{
  background(0);
  fill(255);
  leonberger.eat();
  lab.sleep();
}

```

</div>
</div>

<div id="Separate" class="tabcontent">
<div class="tabhtml" markdown="1">

Recall from last week, we also separated our classes from our main sketch.  The primary reason for doing this is to make sure our code is cleaner and that we can more easily share and reuse classes in other projects.

So, it might look something like this:

#### dog.js

```js

class Dog {
  constructor(name, breed, weight, eyeColor, hairColor ) {
    this.name = name;
    this.breed = breed;
    this.weight = weight;
    this.eyeColor = eyeColor;
    this.hairColor = hairColor;
  }

  eat()
  {
    text(this.name + "is eating...", 100, 100);
  }

  sleep()
  {
    text(this.name + " is sleeping...", 200, 200);
  }
}
```

#### sketch.js

```js
var leonberger = new Dog("Alice", "Leonberger", 70, "brown", "brown");

var lab = new Dog ("Lucy", "Lab", 35, "black", "black");

function setup()
{
  createCanvas(800,600);
}

function draw()
{
  background(0);
  fill(255);
  leonberger.eat();
  lab.sleep();
}
```

#### index.html

```html

<html>
    <head>
        <script src="p5.min.js"></script>
        <script src="dog.js"></script>
        <script src="sketch.js"></script>
    </head>
    <body>
    </body>
</html>

```

Something to note however.  The `dog.js` class must be referenced before the `sketch.js` so that it can be used and found in the `sketch.js` file.


</div>
</div>

<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tabs to see the final result. Feel free to change values.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>
