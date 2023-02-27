---
layout: page
usemathjax: true
title: "COM1: The Multiplication Rule"
---

{% assign basedir = site.url| append: "/MGF1106/probability" %}
{% assign imgdir = basedir| append: "/images" %}

# Counting Is Hard, Really.
While we generally learn how to count before even entering school, it is a very primitive type of counting.  Typically a child will point objects one at a time while counting out loud "one, two, three" and so on.  However, even this method is ripe for disaster.  The child may lose track of which objects have already been pointed to and point to the same one twice, resulting in an overcount.  Or the child may not notice an object and forget to point at it, resulting an undercount.  Maybe the child will get lucky and the overcounts will cancel out the undercounts.

It turns out that as adults, we're only marginally better than the child.  If the numbers get large enough, we'll make exactly the same mistakes.  In mathematics, we're usually not counting actual physical objects, but *possibilities*.  In studying elections, we wondered how many ways a ballot could be filled out.  Back then, we came up with an answer:  For $N$ candidates, there are $N!$ ways to fill out the ballot.  We'll recover that result in this section as well.  When studying weighted voting, we did even better and came up with a systematic way to list them out.  If we hadn't done that work (or if you're reading this out of order), then this would be a challenge.  For a small number of candidates it wouldn't be too bad.  For example, with three candidates (say A,B and C), we could come up with the result

$$\begin{array}{ccc}
(A,B,C) & (B,A,C) & (C,A,B) \\
(A,C,B) & (B,C,A) & (C,B,A). \\
\end{array}$$

Note that we're using *ordered tuple* notation.  Sometimes (for example in thw WVS chapter)  you will see $\langle\rangle$ instead of $()$.  With a little work we can convince ourselves that we haven't accidentally listed the same one twice, and that we've really listed every possibility.  However, if there were more candidates, this would be essentially impossible.  Even with six candidates, it would be 720 listings, which can not be manually checked.  Moreover, there are some examples which are physically not countable.  Claude Shannon computed that there are approximately $10^{120}$ ways that a chess game can go.  Meanwhile there are only about $10^{80}$ atoms in the universe.  This means that if you were to list out every possible chess game, you would need to write about $10^{40}$ of them on each atom.  Keep in mind that a billion is a mere $10^9$.

The branch of mathematics that lets us count these vast possibilities is called **combinatorics**.  In this section we'll learn a few basic combinatorial techniques for counting.

## The Multiplication Rule
Often times, complicated processes can be broken down into a   The **multiplication rule** gives is a way of counting how many possibilities there are in a process if we can figure out how many possibilities there are at each step of the process.

<div class="theorem" text="Multiplication Rule for Two Steps">
Suppose that a process has two steps, the first step has $N$ possibilities, and the second step has $M$ possibilities <strong>regardless of how the first step occurs</strong>.  Then the process as a whole has $N\times M$ possibilities.
</div>

We can see why this works by making a table.  Let's say that step 1 has possible outcomes $X_1, X_2, \dots, X_N$ while step 2 has possible outcomes $Y_1, Y_2, \dots, Y_N$.  Then we can arrange all possibilities as follows.

|Step 2 \ Step 1 | $X_1$ | $X_2$ | ... | $X_N$ |
| :---: | :---: | :---: | :---: | :---: |
| $Y_1$ |$X_1$ then $Y_1$|$X_2$ then $Y_1$| ... then $Y_1$ | $X_N$ then $Y_1$|
| $Y_2$ |$X_1$ then $Y_2$|$X_2$ then $Y_2$| ... then $Y_2$ | $X_N$ then $Y_2$|
| ... | $X_1$ then ... | $X_2$ then ... | ... | $X_N$ then ... |
| $Y_M$ |$X_1$ then $Y_M$|$X_2$ then $Y_M$| ... then $Y_M$ | $X_N$ then $Y_M$|
 
We see that there are $N$ columns and $M$ rows, and so there are $N\times M$ total outcomes.

<details class="example" markdown="1">
<summary>Two Step Process</summary>
Suppose that a person's wardrobe contains 5 shirts and 3 pants.  How many different outfits can they make of a shirt and pants?

This can be thought of as a two-step process.  First they must pick a short, and then they must pick pants.  The multiplication rules says that because there are 5 shirts and 3 pants, there are $5\times 3 = 15$ ways that this person can combone them.

It is important that any shirt can go with any pants.  It is important to the multiplication rule that we know *exactly* how many options we have on the second step and that the number does not depend on the first choice made.  If the person were more particular about what matched with what, then we'd need to use different methods.
</details>

It's not a big jump to get to the general version of the multiplication rule.
<div class="theorem" text="Multiplication Rule">
Suppose that a random process has many steps, and that the number of possible outcomes at each step is fixed <strong>regardless of how any other step occurs</strong>.  Then the total number of possibilities is found by multiplying the numbers of possible outcomes at each step together.
</div>

Let's look at a few examples.
<details class="example" markdown="1">
<summary>Many Step Process</summary>
Suppose that the person in the previous example has now discovered that shoes also exist.  Now, they own 5 shirts, 3 pants, and 2 pairs of shoes.  If they want to make an outfit consisting of a shirt, pants, and shoes then the multiplication rules says that there are $5\times 3\times 2=30$ different outfits that they can make.
</details>

It is vital that the number of options does not depend on the particular choices made.  Here are some examples of what might happen when that rule is broken.

<details class="example" markdown="1">
<summary>Different Types</summary>
Say that in the previous example (5 shirts, 3 pants, and 2 shoes) that clothing can either be casual or for work.  When making an outfit, casual and work clothes can not be mixed.  Here's the breakdown:
* 3 casual shirts and 2 work shirts,
* 2 casual pants and 1 pair of work pants, and
* 1 pair of casual shoes and 1 pair of work shoes.

To figure out how many outfits there are, we need to first break outfits up into two categories: work outfits and casual outfits.
* For casual outfits, the multiplication rule says there are $3\times 2\times 1 = 6$ possible outfits, and
* For work outfits, the multiplication rule says there are $2\times 1\times 1 = 2$ outfits.

So in total there are $6+2=8$ possible outfits.
</details>

<details class="example" markdown="1">
<summary>Conflicting Options</summary>
Forget about work and casual distinctions (just 5 shirts, 3 pants, and 2 shoes), but now our imaginary person has discovered dresses and has obtained 4 of them.  Now, an outfit consists of either
1. A dress and shoes, or
2. A shirt, pants, and shoes.

Within each category, the multiplication rule applies.
* There are $4\times 2 = 8$ outfits that consist of a dress and shoes, and
* There are still $5\times 3\times 2=30$ outfits made of a shirt, pants, and shoes.

In total there are $8+30=38$ outfits.
</details>

## Permutations
A **permutation** is an ordering of a set.  Remember that sets do not come with an order.  For example if I called S the set or Arnold Schwarznegger films,

$$S=\{\text{The Terminator}, \text{Terminator 2}, \text{Total Recall}, \dots, \text{Batman and Robin}\}$$,

This notation does not mean that *The Terminator* is his best film just because it's written first -- even though it probably is -- and it does not mean that *Batman and Robin* is his worst film just because it appears last -- even though it probably is.  There are many ways to order the set.  You could order by personal preference, by date of release, or even by the number of cringeworthy Arnold quips, in which case *Commando* probably ranks first.  Pure set notation tells you none of this.

We've seen a few examples of permutations in other parts of the class.
* In voting theory, a preference ballot is an ordering of the set of candidates, and
* In weighted voting theory, Shapley-Shubik power depended on the order in which players voted.

Ordering a set of $N$ objects, can be thought of as $N$-step process.
* **Step 1.** Pick an object to go first ($N$ choices), 
* **Step 2.** Pick an object to go second ($N-1$ choices from the remaining objects),
* **Step 3.** Pick an object to go third ($N-2$ choices from the remaining objects),
* ...
* **Step N-1.** Pick an object to go second from last ($2$ choices remaining)
* **Step N.** Pick an object to go last ($1$ choice)

According to the multiplication rule, there are
$$N\times (N-1)\times (N-2)\times \cdots \times 2\times 1$$
permutations (orderings) of $N$ objects.  Another name for the long multiplication is $N!$ (said as "N factorial").  It is important the number of possibilities at each step did not depend on the particular choice made.

<div class="theorem">
A set with $N$ elements has $$N! = N\times (N-1)\times (N-2)\times \cdots \times 2\times 1$$
possible permutations.
</div>

### Partial Permutations

A **partial permutation** occurs when only some objects in a set are ordered.  A good example from voting theory is the trucated preference ballot.  Or, if someone is asked to give their top three Arnold Schwarzneggar movies, it would be highly unlikely that they would even know his complete filmography in order to give a full permutation.  It's far more reasonable for them to give their first, second, and third place movies but do not rank the rest of the set (e.g. $($*The Terminator*, *Total Recall*, *Predator*$)$).  Note the use of parenthesis for the ranking.  The type of permutation where only $k$ of the $N$ objects in a set are ranked is called a 
**$k$-permutation**.  The top-3 Arnold movies is an example of a 3-permutation.

We can approach $k$-permutations with the multiplication rule the same way as before.  Except that instead of there being $N$ steps, there will be only $k$.

* **Step 1.** Pick an object to go first ($N$ choices), 
* **Step 2.** Pick an object to go second ($N-1$ choices from the remaining objects),
* **Step 3.** Pick an object to go third ($N-2$ choices from the remaining objects),
* ...

At this point it's good to stop and notice that on step $i$ the number of choices is $N-(i-1)$.  For example on step 3 ($i=3$), there are $N-2$ choices.  That number subtracted from $N$ is always one less than the step number.  So then at the very end we have.

* **Step k.** Pick an object to go $k$th ($N-(k-1)=N-k+1$ choices remaining)

The multiplication rule says that there are 
$$N\times(N-1)\times\cdots\times(N-k+1)$$
different $k$-permutations.  The product above has $k$ different factors in it.  And this is the best way to remember it.  Just take the first $k$ factors of $N!$.

This is an awfully cumbersome expression to write, especially compared to the neat factorial notation for full permutations.  There is a slight improvement that we can make.  Observe that

$$\begin{aligned}
\frac{N!}{(N-k)!} &= \frac{N\times (N-1)\times (N-2)\cdots\times(N-k+1)\times(N-k)!}{(N-k)!} \\[1em]
&= N\times (N-1)\times\cdots\times (N-k+1)\\
\end{aligned}$$

A common notation for the number of $k$-permutations is $\_{N}P_{k}$.

<div class="theorem">
The number of $k$-permutations of a set with $N$ elements is denoted ${}_{N}P_k$ and 
$${}_{N}P_k = \frac{N!}{(N-k)!}.$$
</div>

<div class=note>
When counting the number of $k$-permutations, think of it as multiplying the first $k$ numbers from $N!$.  The formula above can be hard to remember.
</div>

<details class="example" markdown=1>
<summary>Top-Three Rankings</summary>

[Wikipedia](https://en.wikipedia.org/wiki/Arnold_Schwarzenegger_filmography) says that there were 49 Arnold Schwarzneggar movies.  So, in theory, there are 

$${}_{49}P_3 = 49\times 48\times 47 = 110544$$

possible ways to come up with a top-three ranking.  Note that we're using a bit of shorthand here because the full formula is much more difficult to implement.  We would have

$$\begin{align*}
{}_{49}P_3 & = \frac{49!}{(49-3)!} = \frac{49!}{46!} &&(*) \\[1em]
&= \frac{49\times 48\times 47\times 46!}{46!} \\[1em]
&= 49\times 48\times 47 = 110544
\end{align*}$$

On the line marked $(*)$ it is possible that your calculator could evaluate this expression, but it might be too large.  $49!$ alone is $6.08281864\times10^{62}$.  You'll likely need to do the cancellation as in the rest of the steps.

</details>

<div class="warning">
When computing the number of $k$-Permutations, the formula will produce numbers too large for many calculators.  Be familiar with the cancellation technique used in the previous example!
</div>
## Other Types of Scenarios
We see the same overall pattern play out in a number of situations. As long as

1. The process can be broken up into a number of steps, and
2. The possibilities for each step do not change depending on the choice made at each step,

then we can use the multiplication rule.

<details class="example" markdown="1">
<summary>Forced Second Place</summary>
Suppose that there are four candidates in an election (A, B, C, and D).  How many ways can a ballot be filled out such that canidate B is in second place?

Filling out the ballot can still be broken up into four steps.  The only difference is that the number of options at each step will change due to the restriction of having B be second.

* **Step 1.** Choose a candidate to place first.  There are **3 options** for this step.  We are not allowed to choose B because they must be second, but we can choose any other candidate.
* **Step 2.** Choose a candidate to place second.  There is only **1 option** for this step because we are forced to place candidate B here.
* **Step 3.** Choose a candidate to place third.  We've used up two candidates in the previous step, but any of the remaining **2 options** are fine.
* **Step 3.** Choose a candidate to place fourth.  Now there is only **1 option** remaining.

The multiplication rule says that we can fill out the ballot in

$$ 3\times 1 \times 2\times 1 = 6 $$

ways.  This shouldn't be surprising, because this is equivalent to asking how the remaining 3 candidates other than B should be ranked, and we know that there are $3!=6$ ways to do so.
</details>

<details class="example" markdown="1">
<summary>License Plate</summary>
Suppose that a car's license plate consists of seven symbols with the following rules.
* The first symbol is a number other than 0 (1 through 9),
* the next three symbols are capital letters (A through Z), and
* the final three symbols can be any digit (1 through 9).

Now we can apply the multiplication rule.  The first symbol has 9 options, the next three each have 26 options, and the final three each have 10 options.  Multiplying all of these up we get

$$\begin{aligned}
	9\times 26\times 26\times 26\times 10\times 10\times 10 &= 9\times (26)^3\times (10)^3 \\ 
	&= 158184000\\
\end{aligned}$$

Now suppose that the license plate is not allowed to have any repeat symbols.  We have to be careful that this type of restriction follows the conditions of the multiplication rule, namely that the number of possibilities for each symbol does not depend on particular choices for other symbols.  We see that that is the case and in particular.
* For the first symbol you still have **9 options**,
* For the second symbol you still have **26 options**, 
* For the third symbol, you must choose a letter other than the one previously chosen, so there are **25 options**.
* For the fourth symbol, you must choose a letter other than the two previously chosen, so there are **24 options**.
* For the fifth symbol, you must choose a digit other than the one chosen for the first symbol, so there are **9 options**,
* For the sixth symbol, you must choose a digit other than the two previously chosen, so there are **8 options**, and
* For the seventh symbol, you must choose a digit other than the three previously chosen, so there are **7 options**.

So in total there are

$$ 9\times 26\times 25\times 24\times 9\times 8\times 7 = 70761600 $$

possible license plates.  Note that this restriction greatly decreases the number of possibilities as we would expect.
</details>

<details class="example" markdown="1">
<summary>Pin Numbers</summary>
A typical bank card PIN (personal identification number) consists of four digits.  With the multiplication rule we can easily see that there are 10 choices for each digit for $10\times 10\times 10\times 10 = 10^4=10000$ different PINs.  We didn't really need the multiplication rule for this because any number 0 to 9999 is a valid PIN, and there are 10000 such numbers.

Sometimes people have the perception that PINs with repeated digits are somehow less random or secure than those without any repeated digits.  If we want to count the number of PINs without repeat digits, we can use the multiplication rule.
* There are **10 choices** for the first digit,
* There are **9 choices** for the second digit because one is used already,
* There are **8 choices** for the third digit because two have been used alaready, and
* There are **7 choices** for the fourth digit because three have been used already.

So in total there are $10\times9\times8\times7=5040$ PINs without repeated digits.  So only about half of all possible PINs have no repeated digits.  This means it's much easier to guess someone's PIN if you know they won't repeat digits!
</details>

### Counting Subsets

A particular type of example that deserves special attention is that question of how many subsets a particular set has.  Here we are supposing that the set has some finite number of objects, say $N$.  It turns out that all we need is the multiplication rule.  This type of question first arose when we discussed weighted voting sytems, so let's star with an example where there is a weighted voting system with four players ($P_1$, $P_2$, $P_3$, and $P_4), and we wonder how many subsets (coalitions) we can make.  We can make a subset of the set by answering the following four questions:
1. Should $P_1$ be included in the set? (**2 options**)
2. Should $P_2$ be included in the set? (**2 options**)
3. Should $P_3$ be included in the set? (**2 options**)
4. Should $P_4$ be included in the set? (**2 options**)

Every different answer to these questions will build a different subset.  Answering "yes" to all four will give the grand coalition, while answering "yes", "no", "yes", "no" would give $\lbrace P_1, P_3 \rbrace$.  The multiplication rule says then that there are $2\times 2\times 2\times 2 = 2^4 = 16$ different subsets.  The only small detail is that answering "no" to every question gives the empty set, which counts as a subset but does not technically count as a coalition.  So while there are 16 subsets, there are only 15 coalitions.

<div class="theorem">
A set with $N$ elements has $2^N$ possible subsets.
</div>

## Learning Objectives
* Use the multiplication rule to count the number of possibilities a process with multiple steps has,
* Compute the number of permutations a set has using the multiplication rule, and
* Compute the total number of subsets a set has.
