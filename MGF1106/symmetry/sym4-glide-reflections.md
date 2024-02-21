---
layout: page
title: "SYM4: Glide Reflections"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Glide Reflections

A **glide reflection** is the composition of a reflection followed by a translation along the axis of reflection.
A common example of a glide reflection is a pair of footprints as a person walks.
The footprints are mirror images, but because the person is walking, the footprints are separated.

<figure class="center">
<img src="{{imgdir}}/glide-footprints.svg" alt="A glide reflection applied to a footprint." class="center">
<figcaption>To get from one footprint ($F$) to the next ($F'$), the foot is reflected (light gray) and then translated (blue).
</figcaption>
</figure>

In the figure above the footprints $F$ and $F'$ could be consecutive steps as a person is walking in the vertical direction (along $\vec{v}$).
The two footprints are sort of mirror images, but they are not simply reflections.
The reflection of $F$ is the light gray footprint, but the next footprint is shifted up a bit.

## Specifying a Glide Reflection

So in order to specify a glide reflection we need to specify both a reflection and a translation.
The one restriction is that the vector must be a vector which is along the line.
In order to specify just a line, we must give a point and a vector, so to simplify things, we will just say that the vector provided is also the translation vector of the glide reflection.

<div class="procedure" text="Applying Glide Reflections" markdown="1">
We can apply a glide reflection specified by a point $P$ and vector $\vec{v}$ by

1. Reflecting across the line specified by $P$ and $\vec{v}$, and
2. Translting by $\vec{v}$.
</div>

In general, we need to be very careful about the order in which we apply rigid motions, but we see that in the *very particular* case of glide reflections the order of operations does not matter.

<figure class="center">
<img src="{{imgdir}}/glide-footprints-commute.svg" alt="The order of translation and reflection does not matter" class="center">
<figcaption> Left: The reflection is applied and then the translation.  Right: The translation is applied and then the reflection.  The results are the same.
</figcaption>
</figure>

## Determining a Glide Reflection

If we are given a glide reflection and need to work backwards to find the axis of reflection and translation vector of the reflection, it is not enough to have a single point and that point's image.
This was enough for a reflection or a translation, but it is not enough information to pin down a glide reflection, as shown in the figure below.

<figure class="center">
<img src="{{imgdir}}/glide-same-image.svg" alt="Two different glide reflections with the same effect on a point." class="center">
<figcaption> Two separate glide reflections are shown above.  Each has the same effect on point $P$, moving it to $P'$.
</figcaption>
</figure>

It turns out that two point-image pairs is enough to determine a glide reflection.
The key observation that we'll use is that the midpoint between a point and its image must be on the axis of reflection.
Usually, this will be enough, the midpoints between $P$ and $P'$ and between $Q$ and $Q'$ will be enough to define a line which must be the axis of reflection.
Every now and then, we'll get unlucky and those midpoints will coincide.
In this case, the remedy is to make the axis of reflection perpendicular to $\overrightarrow{PQ}$.
We'll summarize this in the the following procedure and then look at how it works.

<div class="procedure" text="Determining the Axis of Reflection" markdown="1">
Given two points, $P$ and $Q$,  and their images, $P'$ and $Q'$ respecitvely, we can determine the line of reflection, $\ell$.
* Find the midpoints between $P$ and $P'$ and $Q$ and $Q'$.  Call them $M\_P$ and $M\_Q$ respectively.
* If $M\_P$ and $M\_Q$ are different, then $\ell$ is the line containing $M\_P$ and $M\_Q$.
* If $M\_P$ and $M\_Q$ coincide, then $\ell$ is the line defined by the point $M\_P$ (which equals $M\_Q$) in the direction *perpendicular to* $\overrightarrow{PQ}$ (or $\overrightarrow{P'Q'}$).
</div>

<figure class="center">
<img src="{{imgdir}}/glide-midpoints.svg" alt="The two strategies for finding an axis of reflection." class="center">
<figcaption> Left: When the midpoints are different, the line bewtween them is the axis of reflection.  Right: When the midpoints coincide, the line will pe perpendicular to $\overline{PQ}$.
</figcaption>
</figure>

Once we've found the axis of reflection, by either means, it is not too difficult to find the translation vector.
Just use the axis of reflection to reflect $P$ (or $Q$) and take the vector from that point to $P'$ (or $Q'$).
<div class="warning">
Make sure that your translation vector is <em>to</em> $P'$ or $Q'$.  The direction does matter.
</div>

<figure class="center">
<img src="{{imgdir}}/glide-translation-vector.svg" alt="Finding the translation vector after the axis of reflection is found." class="center">
<figcaption> In both scenarios above, the translation vector is found by reflecting $P$ to the point $X$ and finding the vector from $X$ to $P'$.  The direction of the vector matters.
</figcaption>
</figure>

<div class="note">
You can somewhat check your work by verifying that the translation vector is in the same direction as the line.
</div>

We'll summarize this in the following procedure.
<div class="procedure" text="Determining a Glide Reflection's Translation"  markdown="1">
Given

* A glide reflection with axis of reflection $\ell$, 
* A point $P$, and 
* The image, $P'$ of $P$ under the glide reflection

We can find the translation vector by doing the following:

1. Apply the reflection across $\ell$ to $P$ and call the image $X$.
2. The translation vector is $\overrightarrow{XP'}$.

</div>

## Properties of Glide Reflections

We will very briefly list some properties of glide reflections.

### Composition of Glide Reflections

Applying a glide reflection twice in a row gives a simple translation.

<figure class="center">
<img src="{{imgdir}}/glide-double.svg" alt="Applying the same glide reflection twice" class="center">
<figcaption> A glide reflection moves $P$ to $P'$ and $P'$ to $P''$.  The total effect is a translation of $2\vec{v}$ from $P$ to $P''$.
</figcaption>
</figure>

### Orientation Reversing

Since a glide reflection is made up of two parts, a reflection and a translation, we can assess how it treats orientation by looking at each part individually.
The reflection part reverses order, and then the translation part preserves that reversed order, so the overall effect is to reverse order.

<figure class="center">
<img src="{{imgdir}}/glide-reverse-orientation.svg" alt="Glide reflections reverse orientation." class="center">
<figcaption> When applying a glide reflection, the reflection part reverses the orientation and the translation does not undo that.
</figcaption>
</figure>

### Composition of Translations and Reflections

We were strict to define a glide reflection so that the translation vector is in the same direction as the axis of reflection.
A curious student might wonder what would happen if we broke that rule and allowed the translation to be in a different direction.
From the previous discussion about orientation, we can conclude that the end result will still be a rigid motion which reverses orientation.
So according to our classification theorem, what we *should* have is either a glide reflection or just a plain reflection.
Indeed both of these are possible.

<figure class="center">
<img src="{{imgdir}}/glide-bad-translation.svg" alt="A reflection followed by a translation " class="center">
<figcaption> Left: A reflection followed by a translation <em>not</em> in the direction of the axis of reflection.  Right: The same result given by a normal glide reflection
</figcaption>
</figure>

If the translation vector is perpendicular to the axis of reflection, the result will just be a normal reflection, not a glide reflection.

## Objectives Covered
1. Graphically find images of objects under a glide reflection.
2. Determine the axis of reflection and translation vector of a glide reflection given two point-image pairs.

