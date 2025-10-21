# Procedural Jellyfish

## Project Overview
In this project, I createed a procedural jellyfish using Houdini.

Here is the breakdown of the different jellyfish parts I was putting together:

<img height="500" alt="Jellyfish Parts" src="/assets/JellyfishParts.png">

This is the reference image I was working with:

<img height="500" alt="Jellyfish Reference" src="/jellyRef.jpg">

## Bell
Starting from a bended line, revolving it around a y-axis, I have the basic hull of my jellyfish bell. Then polyextrude gives it an inner layer as shown in the reference image. Finally a null-node was introduced to take references of multiple parameters of the bell and is used to set key frames on the timeline, serving as a stand-alone moving and pulsing animation controller for the jellyfish.

<img height="500" alt="Jellyfish Bell" src="/jellyBell.png">

## Arms 
A rectangular XY-plain grid was crumple, folded, and reshaped in a series of Attribute Wrangle nodes, then copied in four positions all facing the middle. Using the bell's centroid, one at first frame and one animated, the arms were able to match the animation with the bell. Next, Vellum Cloth gave the arms some physical simulation, pinned by a group of nodes at the very top of the arms. In the end, a polyextrude node provides thickness to the arms.

<img height="500" alt="Jellyfish Arms" src="/jellyArms.png">

## Veins
Beginning with two Group Expression nodes with different Y value selection, followed by a scatter node respectively, two group start_seeds and end_seeds points are randomly selected. Passing them into the Finds Shortest Path node on the bell surface, veins are drawn "from any start to each end" points in the input groups. Similar to arms, they gained ability to move with bell's animation. Then a Ray node made sure it also stick on the bell surface while pulsing, finishing with some thickness obtained from sweep node.

<img height="500" alt="Jellyfish Veins" src="/jellyVeins.png">

## Organs
Very much a combination of what was done for arms and veins: a line bended on both ends was copied in four positions facing the middle, then pointdeformed to follow bell's animation, casted onto bell's inner layer by Ray, finished with a sweep for thickness.

<img height="500" alt="Jellyfish Organs" src="/jellyOrgans.png">


## Tentacles
The most bottom ring of points were selected as roots to grow tentacles, each with a randomized length. While pinned to their roots, pointdeform provides animation with the bell and vellumhair adds physical simulation to them. Pop Force was also added onto vellumsolver here to make the tentacles sway left and right, finished by a sweep for a little bit of thickness.

<img height="500" alt="Jellyfish Tentacles" src="/jellyTenta.png">

## Final Result
<img alt="Jellyfish" src="/jellyfish.gif">
