---
layout: page
usemathjax: true
title: "COM2: Counting Subsets"
---

{% assign basedir = site.url| append: "/MGF1106/probability" %}
{% assign imgdir = basedir| append: "/images" %}

# When Order is Irrelevant
The counting that we used the multiplication rule for was explicitly **ordered**.  We always had a first step, a second step, and so on.  Furthermore, we had that every different selection arrived at a different result.  Let's look at an example where this is not the case.  Let's start with the set of primary colors

$$P =\lbrace \text{Red}, \text{Blue}, \text{Yellow} \rbrace. $$

We'll perform the following procedure:
1. Pick one primary color,  (**3 options**)
2. Pick a different primary color, and (**2 options**)
3. Mix the two colors together.  (**1 option**)

The multiplication rule would say that there are $$3\times 2\times 1 = 6$$ ways that
this could be carried out.  We can even list all of the possible options out:

$$\begin{array}{ccc}
(\text{Red},\text{Blue}) & (\text{Red},\text{Yellow}) & (\text{Blue},\text{Yellow}) & \\
(\text{Blue},\text{Red}) & (\text{Yellow},\text{Red}) & (\text{Yellow},\text{Blue}) & \\
\end{array}$$

However, there are not really six possibilities for the final result.  That third step of mixing the colors together removes some of the variation.  The order in which the colors are chosen does not influence the final, mixed color.
* Both $(\text{Red},\text{Blue})$ and $(\text{Blue},\text{Red})$ yield Purple
* Both $(\text{Red},\text{Yellow})$ and $(\text{Yellow},\text{Red})$ yield Orange
* Both $(\text{Blue},\text{Yellow})$ and $(\text{Yellow},\text{Blue})$ yield Green

## Dividing Duplicates
What we learned from the above example is that **every possible ordering of the same subset** gave a duplicate result.  So when counting subsets of a particular size, we always have to **divide by the number of ways to order the subset** to account for duplicates.

<div class="warning">
In the previous section we counted the number of subsets of <strong>any size</strong> a set has.  Here, we are considering only subsets <strong>of a particular size</strong>.  In the prior example, we picked two colors, so we only consider subsets of size 2.
</div>

<div class="example" markdown="1">
Suppose that there is a team of five people: Alice, Bob, Carol, Derek, and Ellen.  The team needs to send three members off to a conference.  How many different teams can be sent?

Mathematically, we want to know how many different size three subsets we can make.  If we try to apply the the multiplication rule we get the following process:
1. Pick one person to go to the conference, (**5 options**)
2. Pick another person to go to the conference, and (**4 options**)
3. Pick the final person to go to the conference (**3 options**).

According to the multiplication rule, there are $5\times 4\times 3 = 60$ possible teams.  However, just as before, this will be an overcount because many sequences of choices lead to the same result.  For example the choices
$(\text{Alice}, \text{Bob}, \text{Carol})$ and $(\text{Bob}, \text{Carol}, \text{Alice})$ will both lead to duplicate results, the set $\lbrace \text{Alice}, \text{Bob}, \text{Carol}\rbrace$.  How many duplicates will there be?  Any ordering of the three people will give the same team going, and twe know that there are $3!= 3\times 2\times 1 = 6$ ways to order three objects.  So there are not $60$ teams but the $60$ possible orderings can be arranged into $60\div 6 = 10$ teams.
</div>

So if we have a set with $N$ objects, and we want to make a subset of size $k$, we do the following general procedure.
1. Count the number of ways the subset could be made in sequential order.
  * Previously, we called this the number of $k$-permutations or ${}_NP_k$.
  * A formula for ${}_NP_k$ is $\frac{N!}{(N-k)!}$, but it's always possible to recover this with the multiplication rule as we did in the above example.
2. Divide out the number of ways the subset can be ordered.
  * We know that $k$ elements can be ordered $k!$ ways.
3. Then there are $\frac{ {}_NP_k}{k!} = \frac{N!}{(N-k)!k!}$ different subsets of size $k$. 

<div class="theorem" text="Counting Subsets">
A set with $N$ objects has $\frac{ {}_NP_k}{k!}$ subsets of size $k$.  Sometimes this quantity is denoted ${}_NC_k$. Using the formula that $\frac{ {}_NP_k}{k!} = \frac{N!}{(N-k)!}$ we can rewrite the equation as

$$ {}_NC_k = \frac{N!}{(N-k)!k!}$$
</div>

The notation ${}_NC_k$ comes from the fact that sometimes the subset count is referred to the number of *combinations* (or $k$-combinations) of the set.

<div class="warning">
Counting problems come in two main types depending on whether the order of selection influences the final result or not.
<div markdown=1>
1. If the selection order matters to the final outcome, use the $k$-permutations or the multiplication rule directly as in the previous section.
2. If the selection order does **not** influence the final outcome, then you are just choosing a subset.  Be sure to divide out the duplicates as just covered.
</div>
</div>

<div class="note">
	The formula can be hard to plug into. It's often better to break it up into steps.  First count the $k$-permutations and divide by $k!$.
</div>

<details class="example">
<summary>Lottery Tickets</summary>
Most lotteries have players guess which numbered balls will be chosen.  The choice is not an ordered choice.  Even though the balls are chosen one at a time, a ticket will win if it matches the numbers chosen.  It is not necessary to also indicate the order of selection.  Suppose a lottery has balls numbered 1 through 69, as the current Powerball Lottery has.  Of those 69 balls, five will be chosen as the winning numbers.  How many different lottery tickets can there be?

We should recognize that filling out a lottery ticket is the same as choosing a subset of size 5 from the set of 69 balls.  The formula says that we can find the number of subsets as

$$\begin{align*}
{}_{N} C_k & = \frac{N!}{(N-k)!k!} \\
{}_{69} C_5 & = \frac{69!}{(69-5)!5!} = \frac{69!}{64!\times 5!} \\[1em]
&= \frac{69\times68\times67\times66\times65\times 64!}{64!\times 5!} \\[1em]
&= \frac{69\times68\times67\times66\times65}{5!} \\[1em]
&= 11238513
\end{align*}$$

</details>
<div class="warning">
Like with $k$-permutations, plugging directly into the formula will often result in numbers too large for the calculator.  Be sure you can cancel factorials as in the above example.
</div>

<details class="example" markdown="1">
<summary>Pizza Toppings</summary>
A pizza parlour advertises that they have 12 toppings.  They are running a weekly special where a pizza with three different toppings can be bought at a discounted price.  How many different possible pizzas can be ordered that qualify for the special?

Choosing three different toppings means choosing a subset of the set of toppings.  The final pizza does not change depending on the order in which the three toppings are chosen.

</details>

### Symmetry
In the first example, we looked at the situation of choosing three members from a team of five to go to a conference.  One observation to make is that instead of choosing which three should go, we could just as easily choose which two members will *not* go.  We can confirm this directly.

$$\begin{align*}
{}_5 C_3 = \frac{5!}{(5-3)!\times 3!} &= \frac{5!}{2!\times 3!} \\[1em]
{}_5 C_2 = \frac{5!}{(5-2)!\times 2!} &= \frac{5!}{3!\times 2!}
\end{align*}$$

Since multiplication is commutative, these are the same quanity.  And indeed, regardless of the size of the set, the formula tells the same story.  For a set of $N$ objects, there are the same number of subsets of size $k$ and of size $N-k$

$$\begin{align*}
{}_N C_k &= \frac{N!}{(N-k)!\times k!} \\[1em]
{}_N C_{N-k} = \frac{N!}{(N-(N-k))!\times (N-k)!} &= \frac{N!}{k!\times (N-k)!}
\end{align*}$$

## Putting It All Together
Many counting problems are solved with some combination of the three techniques we've looked at so far.  Typically, we break a process up into smaller steps, and then on each step we can use the multiplication rule or a subset selection.  The rest of this section will be devoted to examples.

<details class="example" markdown="1">
<summary>Conference Redo</summary>
Suppose that the team of five people is once again sending three people to a conference.  But now, rather than just sending three people, they will send three people and designate one of them to be a leader.  This situation is not exactly a subset question.  The same set of three can be chosen with a different leader designated.  But it also is not a purely sequential process because the two people who are not the team leader can be chosen in any order without changing the result.  This indictates that we should break the process up into two steps.

1. Choose a group leader, (**5 options**) and
   * Step 1 has 5 options any member can be the leader.
2. Choose two other members to go along (**6 options**).
   * Step 2 is asking us to pick a subset of two from the remaining members.  There are $\frac{4!}{2!2!} = 6$ ways to do so.

So in total, the multiplication rule gives us $5\times6 = 30$ ways to choose the team.

The means of devising a multi-step process is by no means unique.  Instead, we could have decided the way to proceed is to

1. Choose three members to go to the conference, and (**10 options** from previous example)
2. Designate one member to be the leader (**3 options**).

This Gives $10\times 3 = 30$ possibilities just as before.
</details>

<details class="example" markdown="1">
<summary>Pizza Toppings Redo</summary>
Our pizza parlour from before is offering a new special.  Of their 12 toppings, 5 are meats and 7 are vegetables.  Their new weekly special allows the customer to build their own supreme pizza by choosing two different meats and three different vegetables.  How many such pizzas can be built?

This is a two step process:
1. Choose 2 of the 5 meats, and (**10 options**)
  * There are ${}_5 C_2 = \frac{5!}{3!2!} = 10$ ways to do this.
2. Choose 3 of the 7 vegetables (**35 options**)
  * There are ${}_7 C_3 = \frac{7!}{4!3!} = 35$ ways to do this.
  
So in total there are $10\times 35 = 350$ different pizzas that can be made.
</details>

<details class="example" markdown="1">
<summary>Full House</summary>
A standard deck has 13 types of cards (1-10, Jack, Queen, King, Ace) appearing in four suits (clubs, spades, hearts, and diamonds).  In most versions of the card game Poker, a *full house* is when a five-card hand has three of one type of cards and two of another type.  For example having three 2's and two Aces would be a full house.  How many different full houses can we make?  We devise the following scheme to construct a full house.

1. Choose a card type for the "three of a kind" part, (**13 options**)
  * We already noted that there are 13 types of cards, and any type can be our three of a kind.
2. Choose three of the four suits for the "three of a kind" to be, (**4 options**)
  * Choosing three of the four suits is the same as choosing the suit to leave out, so there are 4 choices.  
  * It's fine to say ${}_4 C_3 = \frac{4!}{1!3!}=4$ as well.
3. Choose a card type for the "two of a kind" part, and (**12 options**)
  * We need to choose a type other than what we chose for the three of a kind part.
4. Choose two of the four suits for the "two of a kind" (**6 options**).
  * Choosing two of four is ${}_4 C_2 = \frac{4!}{2!2!} = 6$.
  
Finally, the multiplication rules gives $13\times 4\times 12\times 6 = 3744$
different possible full houses.
</details>

## Learning Objectives
1. Compute the number of subsets of a given size a set has.
2. Combine various counting rules to determine the number of possibilities for complicated processes.
