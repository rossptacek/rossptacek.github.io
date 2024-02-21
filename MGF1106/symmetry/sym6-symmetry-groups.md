---
layout: page
title: "SYM6: Symmetry Groups"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Symmetry

Now that we thoroughly understand rigid motions of the plane, we are ready to discuss symmetry of two-dimensional objects.
When we began this chapter, we consdired the example of a few letters. 

<figure class="center">
    <img src="{{imgdir}}/lettersymmetry.svg" alt="The letters A and H with symmetries." class="center"/>
    <figcaption> Both the letter "A" and "H" have some "mirror" symmetry. </figcaption>
</figure>

We understand that the letters have some symmetry because they look identical on either side of the dashed lines.
However, now we have the tools to view this more precisely.
The letters have symmetry because *reflection* across the dashed lines does not change the appearance of the figure.

<div class="definition" text="Symmetry">
A <strong>symmetry</strong> of an object is a rigid motion which does not appear to change that object.
</div>

Viewing symmetry in this way reveals some extra structure that symmetries have.
Recall that two rigid motions can be *composed* by following one after the other.
In the particular case of symmetries, this is especially powerful because composing symmetries yields another symmetry!
If the first motion does not appear to change the object and neither does the other, then performing one and then the other will not appear to change the object either.

<div class="theorem"> The composition of two symmetries gives another symmetry.
</div>

In this section, we'll only consider *finite* two dimensional objects.
With this restriction, we see that the only types of rigid motions that can possibly be symmetries are rotations and reflections.
* A translation can not be a symmetry because repeatedly composing a translation with itself will move the object off itself.
* A glide reflection can not be a symmetry because composing a glide reflection with itself gives a translation, which can not be a symmetry.

So in the end we'll find that there are only two options.
1. **The object has only rotations as symmetries.**
  Every object has at least the 0 degree rotation, so it's impossible to avoid rotations entirely.
2. **The object has both rotations and reflections as symmetries.**

## Objects with Only Rotations

Objects which lack reflection symmetry are sometimes called **chiral**.
Our hands, for example, are chiral because our thumbs only point out of one side.

<figure class="center">
<img src="{{imgdir}}/symmetry-rotations.svg" alt="A chiral object." class="center">
<figcaption>The shuriken is chiral.  The gray shuriken's points wind in a counterclockwise direction, but its mirror image (blue) winds in a clockwise direction.
</figcaption>
</figure>


