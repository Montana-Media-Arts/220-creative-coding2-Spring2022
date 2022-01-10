---
title: Particle Systems
module: 7
jotted: false
---

# Particle Systems

The term particle system, an incredibly common and useful technique in computer graphics, was coined in the creation of this particular effect.

<quote>“A particle system is a collection of many many minute particles that together represent a fuzzy object. Over a period of time, particles are generated into a system, move and change from within the system, and die from the system.” —William Reeves, "Particle Systems—A Technique for Modeling a Class of Fuzzy Objects," </quote>

ACM Transactions on Graphics 2:2 (April 1983), 92.
Since the early 1980s, particle systems have been used in countless video games, animations, digital art pieces, and installations to model various irregular types of natural phenomena, such as fire, smoke, waterfalls, fog, grass, bubbles, and so on.

This section will be dedicated to looking at implementation strategies for programming a particle system. How do we organize our code? Where do we store information related to individual particles versus information related to the system as a whole? The examples we’ll look at will focus on managing the data associated with a particle system. They’ll use simple shapes for the particles and apply only the most basic behaviors (such as gravity). However, by using this framework and building in more interesting ways to render the particles and compute behaviors, you can achieve a variety of effects.

As the quote described above, a particle system is a collection of simple objects. We've already dealt with programming collections of objects before - like arrays of Movers that simulate bouncing balls. But for particle systems, our collections are more complex. The collections will range in size: sometimes there will be zero particles, sometimes ten, sometimes ten thousand.  The collections themselves will have behavior and properties, not just the particles they're made up of.

<a href="https://www.khanacademy.org/computing/computer-programming/programming-natural-simulations/programming-particle-systems/a/intro-to-particle-systems" target="_new">Khan Academy</a> 

### Coding Train

<a href="https://www.youtube.com/embed/UcdigVaIYAk" data-lity>Simple Particle System Video - Coding Train</a>