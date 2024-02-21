---
layout: page
title: "SYM2: Translations"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Translations

Translations are probably the simplest rigid motion.
A translation occurs when an object is slid without any type of spin.
The figure below shows a gray hand and some possible images of the hand under a translation.

<figure class="center">
<img src="{{imgdir}}/translationexample.svg" alt="A hand under various translations" class="center">
<figcaption> The blue hands show some possible translations of the gray hand.  The important feature is that the hand is moved but its orientation is not changed.
</figcaption>
</figure>

While translations may be simple, describing them mathematically still takes some work.
In this section we'll introduce the proper mathematical object for describing a translation, a vector.
Then we'll use vectors to work with translations and compositions of translations.

## Vectors

A **vector** is a mathematical object which records both a direction and a magnitude.
This is exactly what we need to describe a translation.
We need to know which way to push the object, and we also need to know how far in that direction to poush.
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
In component form, a vector is represented by how far it extends in the horizontal and vertical directions.
Since the vector extends 4 units right and 3 units up, its component form is $(4, 3)$.
If the vector extends to the left or down, then the components may be negative numbers.

## Applying Translations

Translations are applied by moving points from the tail of a vector to the vector's tip.

<div class="procedure" text="Applying Translations" markdown=1>
Given a point $P$ and a vector $\vec{v}$, we translate $P$ by $\vec{v}$ with
the following steps.

1. Place a copy of $\vec{v}$ so that its tail is located at $P$.
2. The image, $P'$ under the translation is the location of the tip of the copy of $\vec{v}$
</div>

This procedure is illustrated in the image below.
<figure class="center">
<img src="{{imgdir}}/translationvector.svg" alt="Applying a translation vector" class="center">
<figcaption> The point $P$ is translated to $P'$ by the vector $\vec{v}$.
</figcaption>
</figure>

Applying translations is fairly straightforward.
Geometrically, the arrow shows exactly where the point should move.
Algebraically, the components of the vector indicate how much to change the point's coordinates in both the horizontal and vertical directions.

## Determining a Translation

Given a point $P$ and its image $P'$ under a translation, we can recover the translation vector which sends $P$ to $P'$.
We just need to record how much the translation alters the horizontal and vertical position of $P$.

<div class="warning"> Be careful of signs!  The positive directions are up and right.  If you have to travel left or down to get from one point to another, use a negative number!
</div>

<div class="example" text="Vector Between Points" markdown="1">
Below, the points $P$ and $Q$ are given.
We will find a vector from $P$ to $Q$.
<img src="{{imgdir}}/vectorbetweenpoints.svg" alt="Finding a vector from one point to another." class="center">

We go $-2$ units in the horizontal direction and $5$ units in the vertical direction to go from $P$ to $Q$, so the vector is represented by $(-2, 5)$.
Observe that if we flipped the order and wanted a vector from $Q$ to $P$ then we would get the direction with the opposite direction, $(2, -5)$.
</div>

On occassion, the notation $\overrightarrow{PQ}$ will be used to denote the vector from $P$ to $Q$.
<div class="warning">
When using this notation, be careful because $\overrightarrow{PQ}$ and $\overrightarrow{QP}$ are <strong>not</strong> the same.  They go in opposite directions.
</div>

<div class="procedure" text="Determining Translations" markdown=1>
Given a point $P$ and its image $P'$ under a translation, the translation vector is $\overrightarrow{PP'}$.
</div>

## Composing Translations

Recall that composing two rigid motions means to perform one rigid motion and then immediately perform the other.  When we perform two translations in a row, we see that the result is just another translation.

<figure class="center">
<img src="{{imgdir}}/translationcompose.svg" alt="Applying a translation vector" class="center">
<figcaption> Translating by $\vec{v}$ and then $\vec{u}$ is the same as just translating by the gray vector.  We can denote the result as $\vec{v}+\vec{u}$.
</figcaption>
</figure>

Geometrically, we place one arrow at the tip of the other.
Algebraically, we can think of this as "adding" the two vectors, and in component form it even looks like addition!
If $\vec{v}=(a, b)$ and $\vec{u}=(c,d)$, then $\vec{u}+\vec{v} = (a+c, b+d)$.
We can add vectors by just adding their components.

<details class="example" markdown="1">
<summary>Component Addition</summary>
Let's look at the previous example with components included.
<img src="{{imgdir}}/translationcompose-components.svg" alt="Applying a translation vector" class="center">
We can see that the "tip-to-tail" geometric addition agrees with the algebraic addition because:
<div>
$$\begin{align}
\vec{u}+\vec{v} &= (-3, -3) + (-1, -3) \\
 &= (-3-1, -3-3) \\
 &= (-4, -6)
\end{align}$$
</div>
</details>

### Scaling Vectors

Aside from adding vectors, another natural operation is **scaling** vectors.
If $\vec{v}=(a, b)$, then $\vec{v}+\vec{v} = (2a, 2b)$.
The resulting vector points in the same direction as $\vec{v}$ but is twice as long.
We can do this with any multiplier, not just 2.
A vector $\vec{v}=(a,b)$ can be **scaled** by multiplying each of its components by the same number, $k$.  We'll denote this by $k\vec{v}=(ka, kb)$.

* If $k>0$ the vector will point in the same direction but its distance will be multiplied by $k$.
* If $k<0$ the vector will point in the opposite direction, and its distance will be multiplied by $\|k\|$.
* If $k=0$ the vector will become the zero vector.

There are a few important applications of scaling.
1. The vector $-\vec{v}$ has the same length as $\vec{v}$ but points in the opposite direction.
2. The vector $\frac12\vec{v}$ is the **midpoint** between the tip and the tail of $\vec{v}$.  


## Objectives Covered
1. Specify translations with vectors.
2. Apply translations to figures.
3. Determine a vector between two points.
4. Perform vector arithmetic (addition and scaling)





