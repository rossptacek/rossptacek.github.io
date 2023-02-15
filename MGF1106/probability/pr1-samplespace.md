---
layout: page
usemathjax: true
title: "PR1: Random Experiments and Sample Space"
---

{% assign basedir = site.url| append: "/MGF1106/probability" %}
{% assign imgdir = basedir| append: "/images" %}

# Uncertainty and Random Experiments
Probability theory is the study of any process with an uncertain outcome.  These can range from the very simple, such as tossing a coin to decide who gets to go first, to the very complicated, such as wondering what the price of a stock will be in a year or predicting the weather.  In probability theory we want to compute how likely various results are.  What is the chance that the coin comes up heads?  How likely is it that the stock I invested in will increase in value?  How likely is it to rain tomorrow?

A challenge when discussing probability is that there are really two broad ways in which people discuss probability.  One is to consider probability from the point of view of data, also called **empirical probability**.  If one wondered about the likelihood that a coin comes up heads, they might flip it a handful of times and record the results.  Perhaps after 10 flips, 6 of them were heads.  We may conclude that the coin is unfair and flips heads 60% of the time and tails the remaining 40%.  Or perhaps we'd keep flipping and find that 52 out of 100 flips were heads.  Now we may conclude that the coin is 52% heads and 48% tails, or perhaps we'd just assume that the coin is fair and we'd see that if we flipped the coin enough.  Empircal probability is great for determining the likelihood of processes that are easily repeatable or for which data exists.  Estimating the probability just amounts to looking at the percentage of the data which meets whatever condition is being tested.

Not all random processes are easily repeatable.  Weather forecasts and stock prices exist at a particular point in time which can not be repeated.  Assessments about the likelihood of such events are usually based in **theoretical probability**.  In theoretical probability, we make some assumptions about the situation.  For example, instead of flipping the coin 100 times, we may just begin by assuming that it's a fair coin.  It may seem like this is cheating if our goal is to determine the likelihood of something happening.  However, the power in theoretical probability is that we can cobble together large, complicated processes from the simple ones that we make assumptions about.  We may assume that a coin is fair, but then that allows us to study more complicated things like flipping the coin 100 times.  Even extremely complex examples like the weather can be broken down into smaller pieces.

## Sample Space
Before even beginning to talk about actual likelihood, we begin with the task of enumerating all of the possibilities which may occur in a random process. Each possible result is called an **outcomes**, and the set of all posible outcomes is called the **sample space**.  There are two broad categories under which the sample space might fit.

1. The outcomes may be **discrete**.  This means that there is no "wiggle room" between the outcomes.  The example to keep in mind for this the counting numbers (1, 2, 3, 4, and so on).  If you make a small change to a counting number, you no longer have a counting number.
  * A flipped coin will have a discrete sample space.  There are only two options for how the coin lands:  On the heads side or on the tails side.  There is no in-between.  Even if you want to be picky and add in the possibility that a coin can land on its edge, it's still discrete because there are no outcomes between heads and edge or tails and edge.
  * A card chosen from a deck will have a discrete sample space.  The outcome is just one of the cards from the deck with nothing possible in between.
2. The outcomes may be **continuous**.  With a continuous sample space you can move freely (continuously) between two outcomes and see nothing but other outcomes on the way.  The model for a continuous sample space is the real number line.  As you slide your finger along the real number line, you are always pointing to a real number.  Whereas there are gaps between the counting numbers.
  * When measuring the weather, temperature is continuous.  Between any two possible temperatures you have nothing but more possible temperatures.  Temperatures could be 0 degrees, 100 degrees, or any number in between.
  * Color is another quantity that is continuous.  Although there are three primary colors, and this is discrete (there are no more primary colors between red, green, and blue), the full color gamut is continuous.  One can slide their finger over this image of the gamut without hitting any gaps in the image.
<figure class="center">
    <img src="{{imgdir}}/ciegamut.svg" alt="The CIE 1931 color gamut." class="center"/>
    <figcaption> An approximation of the visible gamut (CIE 1931).  Taken from <a href="https://commons.wikimedia.org/wiki/File:CIExy1931.svg">https://commons.wikimedia.org/wiki/File:CIExy1931.svg</a> </figcaption>
</figure>

We're simplifying greatly in the above discussion of continuous spaces because they are much more complicated than discrete spaces.  For one, continuous spaces are inherently infinite.  And while discrete spaces can be infinite too (the counting numbers don't stop), in this class we will stick to **finite, discrete** sample spaces.

### Notation
Samples spaces are sets, and as such we will often use set notation when discussing them.  For this class, set notation just means to put the members of the set between curly braces.  When the sample space is too large to be written in this way, we will stick to plain English descriptions.  Here are a few simple examples.

* The sample space of a coinflip could be written as $$\{H, T\}$$ where H stands for the coin landing with the heads side up and T stands for the coin landing tails side up.  We're assuming that the coin is standard US currency which has a heads and tails side, but this is immaterial.  However the sides of the coin are labeled, the sample space will be a set with exactly two members.
* The sample space of a standard six-sided die could be written as $$\{1, 2, 3, 4, 5, 6\}$$.  Other six-sided dice may have different markings, but essentially the same sample space.  The somewhat popular board game King of Tokyo uses dice with strange markings like claws and lightning bolts.  The sample space for one of their dice is $$\{1, 2, 3, \text{claw}, \text{bolt}, \text{heart}\}$$.  Even though the names have changed, this is the same sample space.  We could just call claw 4, bolt 5 and heart 6.

<figure class="center">
    <img src="{{imgdir}}/kotdice.png" alt="The dice from King of Tokyo." class="center"/>
		<figcaption> A six-sided die may have strange markings, but the sample space is the same as a standard die.  Taken from <a href="https://jkgeekly.com/portfolio/king-of-tokyo/">https://jkgeekly.com/portfolio/king-of-tokyo/</a> </figcaption>
</figure>
* If a card is to be drawn from a standard deck, there are 52 outcomes.  A standard deck has four suits (clubs, spades, hearts, and diamonds) and within each suit there are 13 cards (2 through 10, Jack, Queen, King, and Ace).  So there are $$13\times 4 = 52$$ cards.  It's not feasible to write them out, so we'd just say something like "The set of cards in a standard deck."  And as we've seen in the previous two examples, **knowing the number of outcomes is more important than the particular names attached to the outcomes.**

## Sequential Processes
We often will repeat a certain random process some number of times.  For example we may take a coin and flip it many times or we may roll some number of dice.  When referring to outcomes like these, we tend to use ordered pair notation.

<div class="example" markdown="1">
Suppose that a coin is flipped twice in a row.  Each coin has two outcomes, heads (H) or tails (T).  We would use $(H,T)$ to represent the first coin being heads and the second coin being tails.  This notation is called **ordered pair** notation.  It is important that we recognize the first symbol as corresponding to the first coin and the second symbol corresponding to the second coin.

|2<sup>nd</sup> Flip \ 1<sup>st</sup> Flip | H | T |
| :---: | :---: | :---: |
| H | $(H,H)$ | $(T,H)$  |
| T | $(H,T)$ | $(T,T)$  |

>**Note:**
>If we had flipped the coin three times in a row, we would extend this to an ordered triple.  That is $(H,T,H)$ would indicate heads on the first and third flips and tails on the second.

* Since the parentheses and commas can quickly clutter our work, we often employ a shorthand where for example we would write $HTH$ instead of $(H, T, H)$.
* With the shorthand, the above sample space is $\lbrace HH, HT, TH, TT\rbrace$ which is much more readable than $\lbrace(H,H), (H,T), (T,H), (T,T)\rbrace$

</div>

>**Note**
>asdf

<div class="example" markdown="1">
Suppose that a standard four-sided die (sample space $\lbrace 1, 2, 3, 4\rbrace$) is rolled twice.  The sample space can be written in a table as follows:

|2<sup>nd</sup> Roll \ 1<sup>st</sup> Roll| 1 | 2 | 3 | 4 |
| :---: | :---: | :---: | :---: | :---: |
| 1 | $(1,1)$| $(2,1)$ | $(3,1)$ | $(4,1)$ |
| 2 | $(1,2)$| $(2,2)$ | $(3,2)$ | $(4,2)$ |
| 3 | $(1,3)$| $(2,3)$ | $(3,3)$ | $(4,3)$ |
| 4 | $(1,4)$| $(2,4)$ | $(3,4)$ | $(4,4)$ |

We can see from the table that there are $4\times 4 = 16$ outcomes when two four-sided dice are rolled.  Note that the shorthand that worked for heads and tails does **not** work here because shortening $(1,1)$ to $11$ would make it look like eleven was an outcome.
</div>

## Events
A related concept is that of an **event**.

<div class="definition" text="Event, Simple Event">
An <strong>event</strong> is a subset of the sample space.  There are some types of events with special names.
<div markdown="1">
* A **simple event** consists of a single outcome,
* The **certain event** consists of the entire sample space, and 
* The **impossible event** consists of no outcomes (is empty).
</div>
</div>
Informally, events are just categories of outcomes.  If a standard six-sided die is rolled we may ask questions such as "Is the outcome even?" or "Is the outcome greater than three?"  The outcomes which answer "yes" to these questions make up the corresponding event.

<div class="example"  markdown="1">

</div>

## Compound Processes and the Multiplication Rule

As we said in the introduction, we want to build complicated processes from simple ones.  This is the power in theoretical probability.  A fundamental question then is how do we figure out the sample space when we combine simple processes.  One way that processes can be combined is by doing them **sequentially**: Do the first, then the second, and so on.  The **multiplication rule** gives a way to count the number of outcomes in the sample space.

<div class="theorem" text="Multiplication Rule for Two Steps">
Suppose that a random process has two steps, the first step has $N$ possible outcomes, and the second step has $M$ possible outcomes <strong>regardless of how the first step occurs</strong>.  Then the process as a whole has $N\times M$ outcomes.
</div>

We can see why this works by making a table.  Let's say that step 1 has outcomes $X_1, X_2, \dots, X_N$ while step 2 has outcomes $Y_1, Y_2, \dots, Y_N$.  Then we can arrange all possible outcomes as follows.

|Step 2 \ Step 1 | $X_1$ | $X_2$ | ... | $X_N$ |
| :---: | :---: | :---: | :---: | :---: |
| $Y_1$ |$X_1$ then $Y_1$|$X_2$ then $Y_1$| ... then $Y_1$ | $X_N$ then $Y_1$|
| $Y_2$ |$X_1$ then $Y_2$|$X_2$ then $Y_2$| ... then $Y_2$ | $X_N$ then $Y_2$|
| ... | $X_1$ then ... | $X_2$ then ... | ... | $X_N$ then ... |
| $Y_M$ |$X_1$ then $Y_M$|$X_2$ then $Y_M$| ... then $Y_M$ | $X_N$ then $Y_M$|
 
We see that there are $N$ columns and $M$ rows, and so there are $N\times M$ total outcomes.

<div class="example"  text="Two Step Process" markdown="1">
Suppose that a person's wardrobe contains 5 shirts and 3 pants.  How many different outfits can they make of a shirt and pants?

This can be thought of as a two-step process.  First they must pick a short, and then they must pick pants.  The multiplication rules says that because there are 5 shirts and 3 pants, there are $5\times 3 = 15$ ways that this person can combone them.

It is important that any shirt can go with any pants.  It is important to the multiplication rule that we know *exactly* how many options we have on the second step and that the number does not depend on the first choice made.  If the person were more particular about what matched with what, then we'd need to use different methods.
</div>

It's not a big jump to get to the general version of the multiplication rule.
<div class="theorem" text="Multiplication Rule">
Suppose that a random process has many steps, and that the number of possible outcomes at each step is fixed <strong>regardless of how any other step occurs</strong>.  Then the total number of outcomes is found by multiplying the numbers of possible outcomes at each step together.
</div>

Let's look at a few examples.
<div class="example" text="Many Step Process" markdown="1">
Suppose that the person in the previous example has now discovered that shoes also exist.  Now, they own 5 shirts, 3 pants, and 2 pairs of shoes.  If they want to make an outfit consisting of a shirt, pants, and shoes then the multiplication rules says that there are $5\times 3\times 2=30$ different outfits that they can make.
</div>

It is vital that the number of options does not depend on the particular choices made.  Here are some examples of what might happen when that rule is broken.

<div class="example" text="Different Types" markdown="1">
Say that in the previous example (5 shirts, 3 pants, and 2 shoes) that clothing can either be casual or for work.  When making an outfit, casual and work clothes can not be mixed.  Here's the breakdown:
* 3 casual shirts and 2 work shirts,
* 2 casual pants and 1 pair of work pants, and
* 1 pair of casual shoes and 1 pair of work shoes.

To figure out how many outfits there are, we need to first break outfits up into two categories: work outfits and casual outfits.
* For casual outfits, the multiplication rule says there are $3\times 2\times 1 = 6$ possible outfits, and
* For work outfits, the multiplication rule says there are $2\times 1\times 1 = 2$ outfits.

So in total there are $6+2=8$ possible outfits.
</div>

<div class="example" text="Conflicting Options" markdown="1">
Forget about work and casual distinctions (just 5 shirts, 3 pants, and 2 shoes), but imagine that our imaginary person has now discovered dresses and has obtained 4 of them.  Now, an outfit consists of either
1. A dress and shoes, or
2. A shirt, pants, and shoes.

Within each category, the multiplication rule applies.
* There are $4\times 2 = 8$ outfits that consist of a dress and shoes, and
* There are still $5\times 3\times 2=30$ outfits made of a shirt, pants, and shoes.

In total there are $8+30-38$ outfits.
</div>

The above examples show how even more complicated enuermerations can be broken down into simpler ones where the multiplication rule applies.
