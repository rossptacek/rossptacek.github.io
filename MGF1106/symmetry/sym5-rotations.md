---
layout: page
title: "SYM5: Rotations"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Rotations

The final type of rigid motion that we'll consider is a **rotation**.
The basic idea around a rotation is straightforward.
The object will be spun around, as though it were sitting on a turntable.
In this section, we will study how rotations are defined mathematically.
We will see how to apply a rotation to a figure, and we will work backwards
All that we have to decide is where to put the center of the turntable and how far to turn it.

The point around which everything spins is called the **center** or **rotocenter** of the rotation.
We choose it just by picking any point on our space.
The amount by which we'll spin is called the **magnitude** of the rotation.
We will specify it by an angle, typically taken to be in the counter-clockwise direction.

<figure class="center">
<img src="{{imgdir}}/reflection-different-rotocenters.svg" alt="Two rotations with different centers." class="center">
<figcaption>Two $90^\circ$ counterclockwise rotations with different centers.  In both images, the center is denoted with $C$.
</figcaption>
</figure>

The figure above depicts in more detail how a rotation is implemented.
You can imagine the circle whose center is the rotocenter passing through a point.
In the figure above these are gray dashed circles.
The point is moved by traveling along this circle in a counter-clockwise direction by the given angle.

## Defining Rotations

As in the introduction, we see that we need two bits of information to define a rotation.

1. We need to specify a point that the rotation will be based around, called the **center** or **rotocenter** of the rotation.
2. We need to specify an angle through which the object will rotate.
  When specifying an angle, we also need to specify the direction of the rotation as well.
  The two options are **clockwise (CW)** and **counter-clockwise (CCW)**.
  <img src="{{imgdir}}/rotation-cw-ccw.svg" alt="A rotation moves a point off a grid." class="center">
  By default, we assume angles are counter-clockwise.
  
### Equivalent Angles

Technically, any real number can be the magnitude of an angle.
However, many choices of angle are redundant.
For example, the $360^\circ$ rotation is one full rotation.
After a $360^\circ$ rotation, a point is right back to where it started.
The $360^\circ$ rotation is no different from a $0^\circ$ rotation.
In general, adding or subtracting $360^\circ$ from an angle does not change the rotation that it specifies.
Typically, we want to specify an angle as being between 0 and 360 degrees (but not including 360 because it's the same as 0).

<details class="example" markdown="1">
<summary>Equivalent Rotation Angles</summary>
We'll work a few examples of normalizing angles to be between 0 and 360 degrees.
1. Convert a $540^\circ$ rotation to a rotation with an angle between 0 and 360 degrees.
  We see that 540 is too large, so we'll need to subtract 360 to normalize it.
  \\[ 540^\circ - 360^\circ = 180^\circ.\\]
  So a $540^\circ$ rotation is the same as a $180^\circ$ rotation.
  This result is between 0 and 360, so we're done.
2. Convert a $-50^\circ$ rotation to a rotation with an angle between 0 and 360 degrees.
  First, this is a good time to note that there's no problem with having a negative angle.
  It just means to turn in the opposite direction as a positive angle.
  This time, $-50^\circ$ is too small, so we need to add 360 degrees.
  \\[ -50^\circ + 360^\circ = 310^\circ.\\]
3. Convert a $1000^\circ$ rotation to a rotation with an angle between 0 and 360 degrees.
  This example is just like the first except that we need to subtract multiple 360s, two in this case.
  \begin{align}
  1000^\circ - 360^\circ &= 640^\circ \\\
  640^\circ - 360^\circ &= 280^\circ \\\
  \end{align}
  So the $1000^\circ$ rotation is equivalent to a $280^\circ$ rotation.
</details>

<details class="example" markdown="1">
<summary>Converting Large Angles</summary>
If we wanted to convert a 10000 degree angle to one between 0 and 360, we'd be at our calculators for a long time subtracting 360s.
It is more efficient to compute exactly how many 360s will be required.
To do so, divide the angle by 360.
\\[10000\div 360 \approx 27.778 \\]
This means that 10000 is a bit more ethan 27 360s.
So we can subtract all 27 out at the same time.
\\[10000^\circ - 27\cdot360^\circ = 280^\circ\\]
So the $10000^\circ$ angle is the same as a $280^\circ$ angle.
</details>

It is important to keep in mind that we are **not** saying that an angle is unchanged by adding or subtracting $360^\circ$ from it.
We are only saying that the result of rotating through that angle is the same.
For example, figure skaters use angles to represent how much they spin when they jump.
It is certainly not the case that a $0^\circ$ jump is the same as a $720^\circ$ jump!

<div class="note">
This equivalence of angle is only meant to apply to rotations for rigid motions.
There are many contexts where adding or subtracting $360^\circ$ completely changes the meaning.
</div>


### Converting Between CW and CCW

In the previous section, we did not distinguish between clockwise and counter-clockwise angles because it applies regardless of whether we're dealing with clockwise or counter-clockwise angles.
Sometimes, we will need to convert between clockwise and counter-clockwise angles.
The conversion is not too difficult!
Just multiply the angle by -1 to convert between the two!

<details class="example" markdown="1">
<summary>Converting between CW and CCW</summary>
1. Convert a $1050^\circ$ CW rotation to a rotation with a CCW angle between 0 and 360.
  First, we'll convert the $1050^\circ$ CW rotation to a CCW rotation of $-1050^\circ$.
  Then, we just need to convert this to an angle between 0 and 360.
  While this number is small enough to just add 360 a few times, we'll practice the division once more.
  \\[-1050\div 360 \approx -2.9167\\]
  This means that the angle is -2 full rotations, almost -3 full rotations.
  So in order to make this positive, we'll need to add 3 full rotations (360s).
  \\[-1050^\circ + 3\cdot360^\circ = 30^\circ\\].
  So the $1050^\circ$ CW rotation is equivalent to a $30^\circ$ CCW rotation.
</details>

## Applying Rotations

In general, we'll have a hard time applying rotations on a grid because the rotation will not typically be on a grid point.
The image below shows a $30^\circ$ counter-clockwise rotation.

<figure class="center">
<img src="{{imgdir}}/rotation-bad-angle.svg" alt="A rotation moves a point off a grid." class="center">
<figcaption>Most rotations will move points off of the grid.
</figcaption>
</figure>

In general, to apply a rotation, one would need a protractor or similar tool to measure an angle.
Since much of what we do involves being able to measure points on the grid, we'll usually stick to rotations that are a multiple of $90^\circ$.
As long as the original points are on the grid, then their images under these rotations will be too.

### Applying 90 and 270 Degree Rotations

When applying a 90 or 270 degree rotation, we can use our knowledge of perpendicular vectors.
the vector from the point to the rotation's center should be perpendicular to the vector from the image to the center, but the two vectors should have the same length.
Recall that given a vector $(a, b)$, the vectors $(-a, b)$ and $(-b, a)$ are vectors which are perpendicular to $(a, b)$ but have the same length.
One of these will lead us the $90^\circ$ rotation and the other to the $270^\circ$ rotation, and it will be visually clear which is which.

<details class="example" markdown="1">
<summary> Finding Perpendicular Rotations</summary>
When we want to apply a rotation of 90 or 270 degrees, we find the vector from the point to the center and then find the perpendicular vectors with the same length.

<img src="{{imgdir}}/rotation-perpendicular.svg" alt="Perpendicular vectors." class="center">

In the image above, we want to rotation $P$ by a 90 or 270 degree rotation.
We find the vector $\vec{v}=(3,2)$ from the center to $P$.
The two candidate perpendicular vectors are $(-2, 3)$ and $(-3, 2)$.
Visually, we can see that $A$ (following $(-2, 3)$) would be the result of a $90^\circ$ CCW rotatation while $B$ would be the result of a $270^\circ$ CCW rotation.

</details>

### Applying 180 Degree Rotations

Applying 180 degree rotations is very similar, easier even.
Instead of needing to find a perpendicular vector, we can just negate the vector.

<img src="{{imgdir}}/rotation-opposite.svg" alt="Opposite vectors." class="center">

In the image above, $A$ would be the image of $P$ under a 180 degree rotation.



## Determining Rotations

As we've done with other rigid motions, we want to be able to work backwards.
Given some points and their images under a rotation, we'd like to figure out what kind of rotation moved the points.
The most difficult part of this is finding the center of the rotation.
As with glide reflections, it will take two points and their images to determine the rotation's center.
A single point and image leaves some ambiguity, as shown in the figure below.

<figure class="center">
<img src="{{imgdir}}/rotation-ambiguous.svg" alt="Two rotations which move a poitn identically." class="center">
<figcaption>The two rotations above are different rotations, but they have the same effect on the point $P$, moving it to $P'$.
</figcaption>
</figure>

One observation that helps us pin down the rotation's center is that it must be that the point and its image are the same distance from the center.
It turns out that any such point *must* be on the perpendicular bisector between the point and its image.

<figure class="center">
<img src="{{imgdir}}/perp-bisector-distance.svg" alt="Distance to the perpendicualr bisector." class="center">
<figcaption>The point $A$ has the same distance to both $P$ and $P'$.
The same is true for any point on the perpendicular bisector.
</figcaption>
</figure>

So the *usual* procedure for finding the rotation's center is to draw the perpendicular bisectors between the points and their images.
In most cases, these two lines will intersect at a single point which must be the rotation's center.

<details class="example" markdown="1">
<summary>Finding a Rotation's Center (Usual)</summary>
This example will show what happens when the perpendicular bisectors do not coincide.
In the image below we are given two points, $P$ and $Q$, and their images, $P'$ and $Q'$ under a rotation.

<img src="{{imgdir}}/rotations-find-rotocenter-usual.svg" alt="Intersecting perpendicular bisectors to find the rotocenter." class="center">

1. The perpindicular bisector between $P$ and $P'$ is constructed as the blue dashed line.
  * First we found the midpoint $M_P$ between $P$ and $P'$.
  * The vector between $P$ and $P'$ is $(5, -3)$, so we use a perpendicular vector of $(3, 5)$ for the perpendicular bisector.
    Since the midpoint is in the middle of a box, it might be easier to take half that vector, $(1.5, 2.5)$ as the perpendicular vector.
2. The perpendicular bisector between $Q$ and $Q'$ is constructed as the red dashed line.
  * Find the midpoint $M_Q$ between $Q$ and $Q'$.
  * The vector between $Q$ and $Q'$ is $(3, 3)$, so we can use $(-3, 3)$ as a perpendicular vector.
3. The perpendicular bisectors meet at the point $C$, which must be the rotation's center.

Visually, we can see that the rotation is a clockwise $90^\circ$ rotation centered at $C$.

</details>

This procedure works unless the points $P$ and $Q$ happen to be on the same line as the rotation's center.
So in this case, we can fix things by intersecting the perpendicular bisector with the line containing $P$ and $Q$.

<details class="example" markdown="1">
<summary>Finding a Rotation's Center (Unusual)</summary>
This example will show what happens when the perpendicular bisectors do coincide.
In the image below we are given two points, $P$ and $Q$, and their images, $P'$ and $Q'$ under a rotation.

<img src="{{imgdir}}/rotations-find-rotocenter-unusual.svg" alt="Intersecting perpendicular bisectors to find the rotocenter." class="center">

1. The perpindicular bisector between $P$ and $P'$ is constructed as the blue dashed line.
2. The perpendicular bisector between $Q$ and $Q'$ is constructed as the red dashed line.  This time we see that the bisectors are the same line!
  So instead we take the line joining $P$ and $Q$.
3. The center, $C$ is the intersection of the perpenedicular bisector(s) and the line between $P$ and $Q$.

Visually, we can see that the rotation is a clockwise $90^\circ$ rotation centered at $C$.

</details>

Combining these two possibilities we arrive at the general procedure.
<div class="procedure" text="Finding a Rotation's Center" markdown="1">
Given two points $P$ and $Q$ and their images $P'$ and $Q'$ under an unknown rotation, we can find that rotation's center with the following procedure:
1. Find the perpendicular bisector between $P$ and $P'$.
2. Find the perpendicular bisector between $Q$ and $Q'$.
  If this would coincide with the perpendicular bisector found in step 1, instead find the line which joins $P$ and $Q$.
3. The rotation's center is the intersection of the lines found in steps 1 and 2.
</div>

If we need to exactly measure the angle of the rotation, we would need a tool such as a protractor.
Typically, we can assess the angle visually because in this class we'll usually have an angle that is a multiple of $90^\circ$.

## Objectives Covered
1. Graphically find images of objects under a rotation.
2. Determine the center of a rotation given two point-image pairs.
3. Find equivalent angles of rotation.
4. Convert between clockwise and counterclockwise angles of rotation.
