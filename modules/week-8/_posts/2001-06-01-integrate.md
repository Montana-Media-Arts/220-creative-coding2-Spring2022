---
title: Integration
module: 7
jotted: false
---

# Integrate Particle System

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'change')">change</button>
  <button class="tablinks" onclick="openTab(event, 'call')">call</button>
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

First, we need change the Particle class so that it accepts parameters so that the particles appear wherever the attack happens.

The Particle class will look like this now.

```js
// Daniel Shiffman
// http://codingtra.in

// Simple Particle System
// https://youtu.be/UcdigVaIYAk

class Particle {

  constructor(x,y) {
    this.x = x;
    this.y = y;
    this.vx = random(-1, 1);
    this.vy = random(-5, -1);
    this.alpha = 255;
  }

  finished() {
    return this.alpha < 0;
  }

  update() {
    this.x += this.vx;
    this.y += this.vy;
    this.alpha -= 5;
  }

  show() {
    noStroke();
    //stroke(255);
    fill(255, this.alpha);
    ellipse(this.x, this.y, 16);
  }

}

```

We only had to make a small change to the Particle class.

</div>
</div>

<div id="change" class="tabcontent">
<div class="tabhtml" markdown="1">

Next, we want to move all the code from the draw into a function that also accepts an x and a y that will be passed into the Particles class. Now, we can just call the method whenever there is a collision.

```js
function createParticles(x,y)
{
for (let i = 0; i < 5; i++) {
    let p = new Particle(x,y);
    particles.push(p);
  }
  for (let i = particles.length - 1; i >= 0; i--) {
    particles[i].update();
    particles[i].show();
    if (particles[i].finished()) {
      // remove this particle
      particles.splice(i, 1);
    }
  }
}

```

</div>
</div>

<div id="call" class="tabcontent">
<div class="tabhtml" markdown="1">

Finally, we can call this function in our collision section.

```js
else if(keyDown('x'))
    {
      cowGirlObjects.changeAnimation('attack');
     
      if(rock != null)
      {
        if(dist(cowGirlObjects.position.x,cowGirlObjects.position.y,rock.position.x,rock.position.y) < 250)
        {
          createParticles(rock.position.x, rock.position.y);
          rock.remove();
          rock = null;
        }
      }
    }
```

Did it work?  No? Dang!  What do we need to change?

</div>
</div>

