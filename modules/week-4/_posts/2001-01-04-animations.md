---
title: Animations
module: 4
jotted: true
---

# Animations

Now that we know about Classes, Objects and Arrays, we can create animations.  For full disclosure, there is a library that does this for you (you just added  it at the top like you would with the p5 library), but we are going to do our own animations.

1. First, go to <a href="https://www.gameart2d.com/freebies.html" target="_new">Game Art 2D</a>

2. Then, find a set of animations that you like. You can go to another place if you have a favorite. I just know that they have some here.

3. Next, let's unpack them and put them into our assets folder.

4. Next, create a class that will import our image, take in an x and y and then have a function that draws it to the screen.

5. In the main sketch create an array of all the objects (should be one object for each frame).

6. Then, print out the objects in the draw.  Do you see the animation?  

7. It should look like this.

<!-- example here -->

Keep in mind, this first example, doesn't use a class.  See how we use the preload to load the images and then display them. 

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2022-Samples/blob/main/Week%204%20Animation%20Example%201.zip" target="_new">Animation Example 1</a>

Is there a way to slow down the animation?  Think about what you did last week.

In this example, we take the original example and use the setInterval to slow things down.

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2022-Samples/blob/main/Week%204%20Animation%20Example%202.zip" target="_new">Animation Example 2</a>

But we need to know how to use a class.  So, let's go back to original example and implement a class.

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2022-Samples/blob/main/Week%204%20Animation%20Example%203.zip" target="_new">Animation Example 3</a>

Finally, we will take our class example and add the setInterval into it.

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2022-Samples/blob/main/Week%204%20Animation%20Example%204.zip" target="_new">Animation Example 4</a>