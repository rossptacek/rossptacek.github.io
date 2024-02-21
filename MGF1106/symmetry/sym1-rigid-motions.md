---
layout: page
title: "SYM1: Rigid Motions"
---	

{% assign basedir = site.url| append: "/MGF1106/symmetry" %}
{% assign imgdir = basedir| append: "/images" %}

# Symmetry

Symmetry is a concept that everyone has some intuition about.
In this chapter, we will undertake a mathematical study of symmetry for two-dimensional objects.
This will involve formally defining what it means for an object to be symmetric.
But further than that, we will understand all of the different ways that objects can be symmetric.
Consider for a moment, the letters "A" and "H".
<figure class="center">
    <img src="{{imgdir}}/lettersymmetry.svg" alt="The letters A and H with symmetries." class="center"/>
    <figcaption> Both the letter "A" and "H" have symmetry, but "H" is more symmetrical. </figcaption>
</figure>
Using our intuition about symmetry, we can see that both letters are symmetric because the left half of each letter is a mirror image of the right half.
However, the letter "H" has even more symmetry because the top half is a mirror image of the bottom half.
Beyond just defining what a symmetry is, we will also classify all of the different ways that objects can be symmetric.

## Rigid Motions

The mathematics of symmetry begins with **rigid motions**.

<div class="definition" text="Rigid Motion">
A <strong>rigid motion</strong> is a way of moving an object without
bending, stretching, or breaking it.
</div>

By **motion** we just mean a way of moving an object.
A **rigid motion** goes further by promising that the movement will not change the shape of the object by bending, stretching, or breaking it.
Some texts will call a rigid motion an **isometry**, roughly translating to
"same measure" in Latin, because a rigid motion will change absolutely nothing about the shape of an object.

<div class="definition" text="Image">
The result of applying a motion to an object is called the <strong>image</strong> of the object.
</div>

First, we'll look at a few examples of how motions can fail to be rigid.

<details class="example" markdown="1" open>
<summary>Non-Rigid Motions</summary>
The image below indicates how a rigid motion moves the star $S$ onto its image $S'$.

<img src="{{imgdir}}/nonrigidmotion1.svg" alt="A star is streched horizontally" class="center">

We can see from the image that the star is moved away from its initial position.
In addition, the star has been stretched horizontally.
The stretching indicates that this is <strong>not</strong> a rigid motion.
Note that we are only using color to visually indicate the image.

<img src="{{imgdir}}/nonrigidmotion2.svg" alt="A star is scaled down" class="center">

The above motion preserves the shape and position of the star but not its size.
Since the star is shrunken down, this is not a rigid motion.
</details>

When thinking about rigid motions of two-dimension object, it's useful to imagine that a thin object made of some inflexible material like stone on your desk.
A rigid motion is any way that you can that object up and place it back down on the desk.


<details class="example" markdown="1" open>
<summary>Rigid Motions</summary>
Below is an example of a rigid motion.
<img src="{{imgdir}}/rigidmotion1.svg" alt="The mirror image of the letter R" class="center">
The letter "R" has been moved to the right, but also it's been flipped backwards.
This is still a rigid motion because the shape and size of the object has been preserved.
Imagine that the "R" was just picked up and flipped over before being placed back down.

Below is one more example of the letter "R" being moved by a rigid motion.
<img src="{{imgdir}}/rigidmotion2.svg" alt="The mirror image of the letter R" class="center">
</details>

## Types of Rigid Motions

After seeing a few examples, it may seem like there is such a variety of possible rigid motions that it would be impossible to list them all out.
However, it turns out that there are only a few type of rigid motions.
We'll describe them informally now.

1. **Translations.** The object is slid across the desk without spinning it at all.
2. **Reflections.** The object is flipped over and placed back on the desk.
3. **Rotations.**  The object is spun around on the desk.  Alternately, imagine that the desk itself spins.
4. **Glide Reflections**. The object is reflected and then translated.

<div class="theorem">
Any rigid motion can be classified as a translation, reflection, rotation, or glide reflection.
</div>

## Composition

It may seem odd for glide reflections to be in the previous list since they're just a combination of other rigid motions.
Namely, a glide reflection consists of two steps:
1. Reflect the object, and
2. Translate the object.

Performing rigid motions in sequence is called *composing* them.

<div class="definition" text="Composition of Rigid Motions">
The <strong>composition</strong> of two rigid motions refers to the act of doing one rigid motion and then immediately performing the other.
</div>

So we would say that a glide reflection is the *composition* of a translation and a reflection.

<div class="theorem">
The composition of two rigid motions is a rigid motion.
</div>

<details class="example" markdown="1" open>
<summary>Composition</summary>
Because we haven't described rigid motions in detail, we'll keep things simple for these examples.
Below we see a composition of two rigid motions.
<img src="{{imgdir}}/composition-ex1-1.svg" alt="The letter R is translated and then rotated." class="center">
In this example, the capitial "R" is first translated to the right, and then it is rotated.
We observe that this compound motion could be achieved by a single rotation.
<img src="{{imgdir}}/composition-ex1-2.svg" alt="A single rotation achieves the same result" class="center">
Rather than spinning the figure in place, we instead spin it about the black dot.
You can imagine that the entire background spins around the black dot and carries the figure with it.
</details>


In light of this, perhaps the list of rigid motions makes a bit more sense and the fact that there are only four types is more impressive.
If you were to perform many rigid motions in sequence, the overall result would still be one of the four basic types.
It's amazing that a glide reflection is the only explicit composition (translate then reflect) and that we don't need separate types for "rotate then reflect" and so on.
