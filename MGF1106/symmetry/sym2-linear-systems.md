---
layout: page
title: "SYM2: Linear Systems"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Linear Systems

When studying rigid motions, we'll find that everything can everything relies on being able to draw lines in particular directions and being able to find the intersection between lines.
These tasks can be accomplished with algebra, but we will do it purely geometrically by drawing the lines on grid paper.
To define a line, one needs two pieces of information.
1. A point from which the line will begin, and
2. A direction in which the line will extend (both forwards and backwards).

Picking an initial point is as simple as putting your pencil down on the paper, so most of this section will be devoted to how direction is handled.

## Vectors
If we only want to describe a direction, we could just use an angle.
Indeed, we could accomplish our goals with just angles, but translating angles to points on our grid paper would require introducing trigonometry.
Instead, we'll handle direction using **vectors**.
A **vector** is a mathematical object which records both a direction and a magnitude.
Vectors will prove useful when we're talking about translations.
Geometrically, vectors are represented by arrows.

<figure class="center">
<img src="{{imgdir}}/vectorexample.svg" alt="Vectors represented by arrows" class="center">
<figcaption> The black arrow is a vector.  The gray arrows are the same vector.
</figcaption>
</figure>

The direction of the vector is the direction in which the arrow points, and the magnitude of the vector is its length.
Note that position is not a part of what we call a vector.
In the above image, the black arrow and the grayed out arrows all represent the same vector because they have the same directions and magnitudes.

<figure class="center">
<img src="{{imgdir}}/vectorexample-rtheta.svg" alt="Vectors in polar and component forms" class="center">
<figcaption> Left: A vector represented directly by its direction (angle) and magnitude (length).  Right: A vector represented by its horizontal and vertical components.
</figcaption>
</figure>

The image above indicates two possible ways to represent a vector.
On the left we see a vector represented directly using it's angle and length, sometimes called polar form.
We can immediately see some issues with polar form.
Namely, it is difficult to compute the angle.
While we are able to use the Pythagorean theorem to find the length of the arrow, the angle is hard to compute.
On the right, we see our preferred way to represent a vector, **component form**.
In component form, a vector is represented by it's horizontal and vertical components.
Since the vector extends 4 units right and 3 units up, its component form is $(4, 3)$.
If the vector extends to the left or down, then the components may be negative numbers.

### Computing Magnitude

As we alluded to previously, we can compute the magnitude of a vector in component form using the Pythagorean theorem.

<div class="theorem">
The magnitude of the vector $(a, b)$ is $\sqrt{a^2+b^2}$.
</div>

### Scaling Vectors

A vector $\vec{v}=(a,b)$ can be **scaled** by multiplying each of its components by the same number, $k$.  We'll denote this by $k\vec{v}=(ka, kb)$.

* If $k>0$ the vector will point in the same direction but its distance will be multiplied by $k$.
* If $k<0$ the vector will point in the opposite direction, and its distance will be multiplied by $\|k\|$.
* If $k=0$ the vector will become the zero vector.

In particular, $-\vec{v}$ has the same length as $\vec{v}$ but points in the opposite direction.


### Perpendicular Vectors

<div class="definition" text="Perpendicular">
Two (nonzero) vectors are called <strong>perpendicular</strong> if their directions differ by $90^\circ$.
</div>

There is an easy test to see if two vectors are perpendicular.
<div class="theorem">
Vectors $(a, b)$ and $(c, d)$ are perpendicular if and only if $ac+bd=0$.
Given a vector $(a,b)$, the vectors $(-b, a)$ and $(-a, b)$ are perpendicular to it.
</div>
If $\vec{v}$ is a vector, then $\vec{v}\_\perp$ may be used to represent a vector that is perpendicular to $\vec{v}$.
<div class="warning">
There are many vectors perpendicular to a given vector, so $\vec{v}_\perp$ is not a unique object.
</div>

### Vector Between Points

To find a vector from one point to another, just find the signed horizontal and vertical distance between the points.
<div class="warning"> Be careful of signs!  The positive directions are up and right.  If you have to travel left or down to get from one point to another, use a negative number!
</div>

<div class="example" text="Vector Between Points" markdown="1">
Below, the points $P$ and $Q$ are given.
We will find a vector from $P$ to $Q$.
<img src="{{imgdir}}/vectorbetweenpoints.svg" alt="Finding a vector from one point to another." class="center">

We go $-2$ units in the horizontal direction and $5$ units in the vertical direction to go from $P$ to $Q$, so the vector is represented by $(-2, 5)$.
Observe that if we flipped the order and wanted a vector from $Q$ to $P$ then we would get the direction with the opposite direction, $(2, -5)$.
</div>

## Lines

To define a line, we need a point and a vector.
The line consists of all points reachable by travelling forwards and backwards along the vector from the point.

<figure class="center">
<img src="{{imgdir}}/lineexample.svg" alt="A line defined by a point and a vector." class="center">
<figcaption> The line (blue) is defined by a point $P$ and a vector $\vec{v}$.
</figcaption>
</figure>

In the picture above, we can see that the blue line is constructed with the following procedure.
1. Draw a copy of $\vec{v}$ extending from $P$.
2. Draw additional copies of $\vec{v}$, each extending from the tip of the previous copy.
3. Perform the above two steps with $-\vec{v}$ as well.

### Finding Vectors of Lines

We can always work backwards to find the vector of a line.
Just take any two points and find a vector from one to the other.

<div class="example" text="Vector of a Line" markdown="1">
In the image below, we take any two points on a line and find the vector between them.
<img src="{{imgdir}}/linevector.svg" alt="Finding a vector in the direction of a line." class="center">
It is fine to take any two points in any order when performing this task.
Remember that there is not a unique vector required to define a line.
</div>

<div class="definition" text="Perpendicular Bisector">
Given points $P$ and $Q$, the <strong>perpendicular bisector</strong> of the points is the unique line which passes through the midpoint of $P$ and $Q$ and is perpendicular to the vector from $P$ to $Q$.
</div>

<div class="procedure" text="Finding a Perpendicular Bisector" markdown="1" >
Given two points, $P$ and $Q$ we can determine the perpendicular bisector of $P$ and $Q$ as follows.

1. Find the vector between $P$ and $Q$ and call it $\vec{v}$.
2. Follow half of $\vec{v}$ from $P$ to find the midpoint, $M$, between $P$ and $Q$.
3. Find a vector $v_\perp$ which is perpendicular to $\vec{v}$.
4. The perpendicular bisector is the line defined by the point $M$ and the vector $v_\perp$.
</div>



