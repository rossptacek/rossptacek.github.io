---
layout: page
title: "SYM3: Reflections"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Reflections

Intuitively, we understand mirror symmetry.
In the image below, we see that the gray and blue hands are mirror images.
The line $\ell$ represents the "mirror" in the sense that the two hands are identically positioned with respect to the mirror.
They just are on opposite sides of it.

<figure class="center">
<img src="{{imgdir}}/reflection-example.svg" alt="Left hand reflected to right hand." class="center">
<figcaption> A hand is reflected across the axis of reflection $\ell$.  A particular point $P$ and its image $P'$ are also shown.
</figcaption>
</figure>

To define a reflection, we just have to specify where to put the mirror.
The line upon which we place the mirror is called the **axis of reflection**.
So in order to appropriately define reflections, we will spend some time using our knowledge of vectors to describe lines.
We will also observe that reflections move points perpendicularly to the axis of reflection, so we'll spend some time discussing perpendicular vectors and lines.
Finally, we will describe how to apply reflections and how to find reflections with a given point and image.

## Lines

To define a line, we need a point and a vector.
The line consists of all points reachable by travelling forwards and backwards along the vector from the point.

<figure class="center">
<img src="{{imgdir}}/lineexample.svg" alt="A line defined by a point and a vector." class="center">
<figcaption> The line (blue) is defined by a point $P$ and a vector $\vec{v}$.
</figcaption>
</figure>


In the picture above, we can see that the blue line is constructed with the following procedure.
The procedure might seem complicated, but it's just a precise way to say "Draw a straight line along the direction of the vector.

<div class="procedure" text="Drawing a line" markdown="1">
In order to draw a line pointing in a direction given by a vector $\vec{v}$, we do the following:
1. Draw a copy of $\vec{v}$ extending from $P$.
2. Draw additional copies of $\vec{v}$, each extending from the tip of the previous copy.
3. Perform the above two steps with $-\vec{v}$ as well.
</div>


### Finding Vectors of Lines

We can always work backwards to find the vector of a line.
Just take any two points and find a vector from one to the other.

<div class="example" text="Vector of a Line" markdown="1">
In the image below, we take any two points on a line and find the vector between them.
<img src="{{imgdir}}/linevector.svg" alt="Finding a vector in the direction of a line." class="center">
It is fine to take any two points in any order when performing this task.
Remember that there is not a unique vector required to define a line.
</div>

### Perpendicular Lines

Lines (and vectors) are perpendicular if they differ by a right ($90^\circ$) angle.
We'll see shortly that reflections move points perpendicular to the axis of reflection, so we'll spend a little time now seeing how to represent perpendicular lines.

<div class="definition" text="Perpendicular">
Two (nonzero) vectors are called <strong>perpendicular</strong> if their directions differ by $90^\circ$.  Two lines are perpendicular if their vectors are perpendicular.
</div>

There is an easy test to see if two vectors are perpendicular.
<div class="theorem">
Vectors $(a, b)$ and $(c, d)$ are perpendicular if and only if $ac+bd=0$.
Given a vector $(a,b)$, the vectors $(-b, a)$ and $(-a, b)$ are perpendicular to it.
</div>
If $\vec{v}$ is a vector, then $\vec{v}\_\perp$ may be used to represent a vector that is perpendicular to $\vec{v}$.
<div class="warning">
There are many vectors perpendicular to a given vector, so $\vec{v}_\perp$ is not a unique object
</div>

<div class="definition" text="Perpendicular Bisector">
Given points $P$ and $Q$, the <strong>perpendicular bisector</strong> of the points is the unique line which passes through the midpoint of $P$ and $Q$ and is perpendicular to the vector from $P$ to $Q$.
</div>

<div class="procedure" text="Finding a Perpendicular Bisector" markdown="1" >
Given two points, $P$ and $Q$ we can determine the perpendicular bisector of $P$ and $Q$ as follows.

1. Find the vector between $P$ and $Q$ and call it $\vec{v}$.
2. Follow $\frac12\vec{v}$ from $P$ to find the midpoint, $M$, between $P$ and $Q$.
3. Find a vector $v_\perp$ which is perpendicular to $\vec{v}$.
4. The perpendicular bisector is the line defined by the point $M$ and the vector $v_\perp$.
</div>

## Defining a Reflection

The line upon which the mirror is placed is called the **axis of reflection**.

<figure class="center">
<img src="{{imgdir}}/reflection-example.svg" alt="Left hand reflected to right hand." class="center">
<figcaption> A hand is reflected across the axis of reflection $\ell$.  A particular point $P$ and its image $P'$ are also shown.
</figcaption>
</figure>


Every point on one side of the axis of reflection will be moved the other side of the axis.
In the figure above we can see a gray hand which is moved to its mirror image in blue.
The axis of reflection is the vertical line marked $\ell$.
We see that the not only are points on the left of $\ell$ moved to the right, but also the distance from points to the axis of reflection are preserved.
For the marked point $P$, we see that the distance from $P$ to $\ell$ is the same as the distance from $P'$ to $\ell$.

It's intutive in the example above, but when we talk about the distance from a point to a line we are talking about the *perpendicular* distance.
The vector from a point to its image should be perpendicular to the axis of reflection, as illustrated in the figure below.

<figure class="center">
<img src="{{imgdir}}/reflection-example-2.svg" alt="Left hand reflected to right hand." class="center">
<figcaption> A hand is reflected across diagonal axis of reflection $\ell$.
The vector from the point $P$ to its image $P'$ is perpendicular to $\ell$.
</figcaption>
</figure>

From this, we can find the following procedure to find the images of points
under a reflection.

<div class="procedure" text="Image Under Reflection" markdown="1">
Suppose that we are given the following:

* An axis of reflection, $\ell$ and
* A point $P$.

We can find the image of $P$ under the reflection with the following steps.

1. Draw the line $\ell_\perp$ which passes through $P$ and is perpendicular to $\ell$.
2. Find the intersection of $\ell$ and $\ell_\perp$ and call it $X$
3. Find the vector $\vec{x}$ from $P$ to $X$.
4. $P'$ is found by following $\vec{x}$ starting from $X$
</div>

<div class="example" markdown="1">
Suppose we are given the following point and axis of reflection.
<img src="{{imgdir}}/reflection-example-3-1.svg" alt="A point and axis of reflection." class="center">

Let's find the image of $P$.  We'll do the first two steps simultaneously.
1. Draw the line $\ell_\perp$ which passes through $P$ and is perpendicular to $\ell$.
2. Find the intersection of $\ell$ and $\ell\_\perp$ and call it $X$
  <img src="{{imgdir}}/reflection-example-3-2.svg" alt="Intersection of line and perpendicular." class="center">
  In the image above, we took two points on $\ell$ to find a vector $\vec{v}$ in the direction of $\ell$.
  Then, we found a perpendicular vector $\vec{v}\_\perp$ and used it to draw a line from $P$.
  This line is denoted $\ell\_\perp$.
  Finally, we marked $X$ as the intersection of $\ell$ and $\ell\_\perp$.
  We'll also do the next two steps simultaneously.
3. Find the vector $\vec{x}$ from $P$ to $X$.
4. $P'$ is found by following $\vec{x}$ starting from $X$
    <img src="{{imgdir}}/reflection-example-3-3.svg" alt="Intersection of line and perpendicular." class="center">

<div class="note">
In this case the vector from $P$ to $\ell$ ($\vec{x}$) just so happened to be the same as the perpendicular vector ($\vec{v}_\perp$) we found.  It will not always be so.  Remember that we had a variety of choices for choosing the vector along the line.
</div>
</div>

## Determining a Reflection

Given a point and its image under a reflection, we can determine the rotation which moved the point by working backwards.
First, we know that the line should be equidistant from the point and its image, and second, we know that the line should be perpendicular to the vector from the point to its image.
In other words, the axis of reflection is just the perpendicular bisector between $P$ and $Q$.


<div class="example" text="Determining Axis of Reflection" markdown="1">
Suppose that a reflection moves point $P$ to point $P'$ in the image below.
<img src="{{imgdir}}/find-reflection.svg" alt="A point and its image under an unknown reflection." class="center">

The axis of reflection is just the perpendicular bisector between $P$ and $P'$.
Remember that the perpendicular bisector is the line which is
1. Perpendicular to the vector between $P$ and $P'$ and,
2. Passes through the midpoint of $P$ and $P'$.

<img src="{{imgdir}}/find-reflection-solved.svg" alt="Finding the axis of reflection between $P$ and $P'$." class="center">

Above, we find the midpoint ($M$) between $P$ and $P'$ by finding half the vector between the points.
<div class="note">
The midpoint does not fit exactly on a grid line since half the vector from $P$ to $P'$ is $(-2.5, -1.5)$.  In general, we'll stick to grid points, but on occassion, we will use centers of boxes as in this example.  We will not use any other non-grid points.
</div>
Then, we find the direction of the line by finding a vector perpendicular to the vector between the points.
One way of doing so is reversing the coordinates and making one of them negative.
</div>

## Properties of Reflections

Here are a few useful properties of reflections.
1. Points on the axis of reflection are not moved by the reflection.
  Such points are called **fixed points**.
2. Applying a reflection twice in a row brings any point back to where it started.
3. Reflections reverses the orientation of objects.

In the image below we see visually what is meant by reversing orientation.

<figure class="center">
<img src="{{imgdir}}/reflection-orientation.svg" alt="Reflections reverse orientation." class="center">
<figcaption> Left: A reflection changes the direction in which a spiral winds.  Right: The counterclockwise order $P$, $Q$, $R$ is reversed in the image to $P'$, $R'$, $Q'$.
</figcaption>
</figure>

The other type of rigid motion we've studied, translations, preserve order.
So this is one way that we can easily differentiate between type of rigid motions.

<div class="note"> You need at least three points and their images to test whether a rigid motion is orientation preserving or orientation reversing.
</div>

## Objectives Covered
1. Graphically find perpendicular lines and perpendicular bisectors.
2. Determine the images of points under a reflection.
3. Given a point and its image under a reflection, determine the axis of reflection of the reflection.
4. Identify whether a rigid motion is orientation preserving or orientaion reversing.

