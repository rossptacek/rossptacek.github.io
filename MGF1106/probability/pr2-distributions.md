---
layout: page
title: "PR2: Probabiliy Distributions"
---

{% assign basedir = site.url| append: "/MGF1106/probability" %}
{% assign imgdir = basedir| append: "/images" %}

# Likelihood and Probability Distributions

Now that we can use combinatorial tools to enumerate the outcomes in a sample space, we are ready to return to the fundamental question of probability: How likely are each of these outcomes?  Remember that we are dealing with theoretical probability where we will just decide what the likelihoods are instead of empirical probability where we would do repeated experiments to discover the probabilities.  Still, our idea of the theoretical probability is informed by the idea of repeated trials.  For each outcome in a sample space, we assign called its **probability**.  The interpretation of this number is that if we had performed repeated trials, the probability is the expected proportion of trials which would have the given outcome.

<div class="example">
<br>
If a fair coin were flipped 100 times, we would expect half (50) to be heads and the other half to be tails.  So the proportion of heads is $\frac{50}{100}=\frac12=0.5$.  Of course if one actually flips a coin 100 times, it is unlikely to have an exact 50-50 split, but this is out best guess at the result, and we imagine that with enough trials we'll get pretty close to a 50-50 split.
</div>

The probability can also be interpreted as a percentage by multiplying by 100.  A probability of 0.5 is the same as a $0.5\times 100 = 50\%$ chance.

This situation should be familiar.  In [WVS2 - Banzhaf Power]({{basedir}}/weightedvoting/wvs2-banzhaf.html) we divided up the power in a system among the players.  Here we are dividing up the realm of possibility among the possible outcomes.  Indeed, the probabilities must make up a **probability distribution**.

1. Each probability is a number between 0 and 1 (inclusive), and
  * Each probability is representing a proportion, and proportions must be between 0 (no trials should have this outcome) and 1 (all trials should have this outcome).
2. The probabilities must sum up to 1.
  * Remember that probabilities are representing proportions of the realm of possiblity.  So we need to account for the entire whole (1 or 100%) with the assignment.  No more and no less.
  
## Notation
This is where things get a bit thorny.  We want to assign probabilities to *events*, not just outcomes.  So although we just defined probability for outcomes, in reality we were defining probabilities of *simple events*, those which have only a single outcome.

<div class="definition">
Given an event $E$, the probability of $E$, denoted $P(E)$ is given by the sum of the probabilities of outcomes in $E$.  If $E$ has no outcomes (is the impossible event) then $P(E) = 0$.
</div>

It is often natural to refer to probabilities of outcomes.  Indeed, that's how we motivated this whole endeavor, so we will sometimes write $P(o)$ for some outcome, but know that the truth is that we mean $P(\lbrace o\rbrace)$ and we were too lazy to write the braces.

<div class="example" text="Fair Coin" markdown="1">
A standard US coin has sample space $\lbrace H, T\rbrace$ where $H$ denotes the coin landing on the "heads" side and $T$ denotes the coin landing on the "tails" side.  Because the coin is fair, we can deduce that both $H$ and $T$ should have a probability of $\frac12 = 0.5$.

* To be completely correct, we would write $P(\lbrace H\rbrace)=0.5$ and $P(\lbrace T\rbrace)=0.5$ because probability is defined for *events* and outcomes are represented as *simple events*.  
* However, we find writing extra $\lbrace$ and $\rbrace$ overly cumbersome and will write $P(H)=0.5$ and $P(T)=0.5$.

Although it seems obvious, let's look at the unstated algebra we're doing.
* Because the coin is fair, we have $P(T)=P(H)$, and
* Because the probabilities must sum to 1 we have $P(H)+P(T)=1$.

This is a system of equations that we can solve.

$$\begin{align*}
P(H)+P(T) &= 1 \\
P(H)+P(H) &= 1 && \text{(Because $P(H)=P(T)$)} \\
2\times P(H) &= 1 \\
P(H) &= \frac12
\end{align*}$$

Since $P(T)=P(H)$ we can work backwards to say that $P(T)=\frac12$ as well.
</div>

<div class="example" text="Loaded Coin" markdown="1">
Suppose that a coin has been modified so that when flipped the heads side is twice as likely to come up as the tails side.  Now what is the probability distribution?

The unfair coin has sample space $S=\lbrace H, T \rbrace$, but we have not been given any probabilities directly.  In order to come up with the distribution, we have to repeat the algebra from the previous example.  Now we have that

* $P(H) = 2\cdot P(T)$ (Heads is twice as likely as tails), and like before
* $P(H) + P(T) = 1$.

We can solve the system the same way.

$$\begin{align*}
P(H)+P(T) &= 1 \\
2\cdot P(T)+P(T) &= 1 && \text{(Because $P(H)=2\cdot P(T)$)} \\
3\cdot P(T) &= 1 \\
P(T) &= \frac13
\end{align*}$$

And so $P(H)=\frac23$.

</div>

<details class="example" markdown="1">
<summary>Three-Way Race</summary>
Suppose that three friends, Alice, Bob, and Carol (A, B, and C), are going to race.  They are somewhat evenly matched and it is possible that anyone can win.  Alice has a 20% chance to win, and the other two are equally likely to win.  What is the probability that either Alice or Carol win the race?

In this scenario we have
* $P(A) = 0.2$,
* $P(B) = P(C)$, and
* $P(A)+P(B)+P(C) = 1$

As before, we can use algebra to fill in the gaps. 

$$\begin{align*}
P(A)+P(B)+P(C) &= 1 \\
0.2 + P(B) + P(C) &= 1 \\
0.2 + P(B) + P(B) &= 1 && \text{(Because $P(B)=P(C)$)} \\
2\cdot P(B) &= 0.8 \\
P(B) &= 0.4
\end{align*}$$

So $P(A)=0.2$, $P(B)=0.4$, and $P(C)=0.4$.  With the simple events filled in, we can determine the probability of any event.  Because it's small enough, we can list all possible events in a table.

| Event ($E$) | Probability ($P(E)$) |
| :---: | :---: |
| $\emptyset = \lbrace\,\rbrace$| 0 |
| $\lbrace A \rbrace$| 0.2 |
| $\lbrace B\rbrace$| 0.4 |
| $\lbrace C\rbrace$| 0.4 |
| $\lbrace A, B\rbrace$| $P(A)+P(B)=0.6$ |
| $\lbrace A, C\rbrace$| $P(A)+P(C)=0.6$ |
| $\lbrace B, C\rbrace$| $P(B)+P(C)=0.8$ |
| $\lbrace A,B,C\rbrace$| $P(A)+P(B)+P(C)=1$ |

</details>

## Uniform Distributions
A **uniform** distribution represents a situation where all outcomes are equally likely.  Objects that are "fair" are good examples of when a uniform distribution would be used.
* A fair coin is one in which both sides are equally likely to be flipped.
* A fair die is one in which every side is equally likely to be rolled.

We saw examples of both a fair coin and a fair die above.  In order to make a uniform distribution, we must divide up the total probaility of 1 equally.  This means that if the sample space has $N$ outcomes, each must have a probability of $\frac1N$.  This makes probability computations significantly simpler as well.

<div class="theorem">
Suppose that a random process has a sample space $S$ with $N$ outcomes and a uniform distribution.  If an event $E$ has $k$ outcomes in it, then

$$P(E) = \frac{k}{N},$$

or equivalently,

$$P(E) = \frac{\text{Number of outcomes in $E$}}{\text{Number of outcomes in $S$}}$$

</div>

<details class="example" markdown="1">
<summary>Fair Six-Sided Die</summary>
A normal six-sided die has a sample space of $\lbrace 1,2,3,4,5\rbrace$.  Suppose that the die is a fair die so that each outcome has a probability of $\frac16$.  We'll compute the probability of some events.
<ul>
<li>If $E$ is the event "The result of the die is an even number.", then $E = \lbrace 2,4,6 \rbrace$.  Since each outcome in $E$ has a probability of $\frac16$, we have 

$$P(E) = P(1) + P(2) + P(3) = \frac16 + \frac16 + \frac16 = \frac36 = \frac12$$

Equivalently, since the event has 3 outcomes and the sample space has 6 outcomes, we can arrive directly at $P(E)=\frac36=\frac12$ with the formula above.</li>
<li>If $E$ is the event "The result of the die is a negative number." then $E =\lbrace\rbrace =\emptyset$ is the impossible event and $P(E) = 0$.</li>
<li>If $E$ is the event "The result of the die is a positive number." then $E =
\lbrace 1,2,3,4,5,6\rbrace$ is the certain event.  We know that this should have a probability of 1.  We can verify that
<div>
$$\begin{align*} P(E) &= P(1)+P(2)+P(3)+P(4)+P(5)+P(6) \\[1em]
 &= \frac16 + \frac16 + \frac16 + \frac16 + \frac16 + \frac16 \\[1em]
 &= 6
\end{align*}.$$
</div>
As before, the formula would immediately give $P(E)=\frac66=1$.
</li>
</ul>

This last example should reinforce why the sum of all outcomes should be 1 in a probability distribution.
</details>

From this point on, we will almost exclusively work with uniform distributions.

## Complementary Events

<div class="definition" text="Complementary Event">
Given an event $E$, the <strong>complementary event</strong>, denoted $E'$ consists of all outcomes which are not in $E$.
</div>

Note that if we take the complement of $E'$ we would get the outcomes not in $E'$, or equivalently the outcomes which are <strong>not</strong> not in $E$, which is a roundabout way of saying the outcomes in $E$.  For this reason, we will often say that $E$ and $E'$ are complementary rather than specifying one is the complement of the other.  It is a completely symmetric relationship.

<div class="example"><br>
For a standard six-sided die ($S=\lbrace 1,2,3,4,5,6\rbrace$) the event $E$ = "An even number is rolled" in set notation is $\lbrace 2,4,6\rbrace$.  The complementary event $E' = \lbrace 1,3,5\rbrace$, all of the outcomes in $S$ which are not in $E$.  Note that taking the complement of $E'$ would just get us right back to $E$.
</div>

If we want to put a logical meaning behind a complementary event, it is saying "*not* the event E."  In the previous example, the complementary event could have been specified in English as $E'$ = "An even number is *not* rolled."  At its heart we are just saying that all of the outcomes in $S$ can be divided into two categories: $E$ and not $E$.  So if we add up the probabilities of both, we should get 1 because every outcome will be represented exactly once.

<div class="theorem" text="Law of Total Probability">
Suppose that $E$ and $E'$ are complementary events.  Then

$$ P(E) + P(E') = 1.$$

Or equivalently,

$$P(E) = 1-P(E')$$
</div>

The point of theorem is not obvious at first.  So let's look at an example.
<div class="example" markdown="1">
Suppose that two fair six-sided dice are rolled.  We know from our work with combinatorics that there are 36 possible outcomes in $S$.  To recap, there are 6 possibilities for the first die and 6 for the second, so the multiplication rule says that there are $6\times 6=36$ outcomes.  We also know that this process has a uniform distribution.
<div class="warning">
We are <strong>not yet</strong> saying anything about the sum of the dice.  We're just saying that rolling a 1 and then a 4 ($(1,4)$) is just as likely as rolling a 2 and then a 3 ($(2,3)$) or any other outcome.
</div>
The fact that this has a uniform distributuion means that to compute the probability of any event, we need only count how many outcomes it has and divide by 36 (the size of $S$).  Let's find the probability that the sum of the dice is 10 or less.

The law of total probability says that we have two options.
1. Directly find $P(E)$ (count how many outcomes result in a sum of 10 or less and divide by 36), or 
2. Find $P(E')$ (count how many outcomes result in a sum of 11 or more and divide by 36) and compute $P(E)=1-P(E')$.

Often times one of these will be significantly easier.  In this case, option 2 is far nicer.  We see that there are only three ways to get a sum of 11 or more:

$$ E' = \lbrace (5,6), (6,5), (6,6)\rbrace.$$

So $P(E') = \frac{3}{36} = \frac1{12}$ and 

$$P(E) = 1-P'(E) = 1-\frac1{12} = \frac{11}{12}.$$

If we tried to find the number of outcomes in $E$ directly, we would have been forced to enumerate all 33 (36-3) of them, and that is both harder and more error-prone than listing out the complementary 3 outcomes.

</div>

## Putting it All Together
Now, since we're focusing on uniform distributuions, questions of probability become questions of counting.  Recall that for a random process with sample space $S$ and a uniform probability distribution we have the formula

$$P(E) = \frac{\text{Number of outcomes in $E$}}{\text{Number of outcomes in $S$}}.$$

So every probability question turns into two counting questions: one for the number of outcomes in the sample space $S$ and one for the number out comes in the chosen even $E$.

### Brief Review of Combinatorial Techniques

We have two main counting techniques
1. **The Multiplication Rule**.  If a process can be broken down into smaller steps, the number of possibilities (outcomes) for each step is, and each different selection gives a truly different outcome, then the number of total outcomes is the product of the number of outcomes at each step.
  * A special case is when $k$ objects from a set of size $N$ are put in order.  This is called a $k$-permutation and has the formula
  $${}_N P_k = \frac{N!}{(N-k)!}$$
  * If all $N$ objects of the set are to be ordered, this is called a permutation and the formulat reduces to $N!$.
2. **Subsets**.  If a subset of size $K$ is to be chosen from a set of size $N$, then there are $\frac{N!}{(N-k)!k!}$ ways to do so.

The general procedure is to come up with a step-by-step process where each step is a subset selection or a $k$-permutation, and then use the multiplication rule to find the total number of outcomes.  The rest of this section will be devoted to examples.

<details class="example" markdown="1">
<summary>Multiple Fair Coin Flips</summary>
Suppose that a fair coin is flipped five times.  What is the probability that three of the coins come up heads?

For now ignore the event whose probability we are computing and focus on the random process itself.  A coin flipped five times has outcomes such as $HTHHT$ or $THTTH$ or any string of five $H$'s and $T$'s.  Because the coin is fair, all outcomes are equally likely, so this will have a uniform distribution.  We will use the formula.

$$P(E) = \frac{\text{Number of outcomes in $E$}}{\text{Number of outcomes in $S$}}.$$

Each coin flip is a step in the process, and there are five flips so the multiplication rule says that there are $2^5=32$ possible outcomes in $S$.  This takes care of the denominator of the above formula.

Now, we need to determine how many of those 32 possibilities has exactly three flips come up heads.  To do so, we need to choose 3 of the 5 flips to come up as heads.  This is choosing a *subset* of the five flips.  There is no ranking or ordering of the three heads involved.  There are ${}_5 C_3 = 10$ such subsets.  So we can conclude that the probability is $\frac{10}{32} = \frac5{16}$.
</details>

<details class="example" markdown="1">
<summary>Multiple Fair Dice</summary>
Suppose that five fair standard six-sided dice are rolled (equivalently, one fair die is rolled five times).  What is the probability that at least one die comes up as a 6?

Since the dice are fair, the process has a uniform distributuion.  Again, we can use the simpler formula 

$$P(E) = \frac{\text{Number of outcomes in $E$}}{\text{Number of outcomes in $S$}}.$$

Since each die has six options, the samples space $S$ for five dice has $6^5=7776$ possible outcomes.  These outcomes would have the form $(1, 4, 6, 1, 3, 2)$ where any number 1-6 is possible in each spot.  This takes care of the numerator of the above formula.

Now, we need to figure out how many outcomes have at least one six appear.  This turns out to be rather tricky, because there are many possible ways in which this may happen.
* Exactly one die can have a 6.
* Exactly two dice can have a 6.  This is very tricky because even within this category there are sub-categories.  Maybe the first two dice are sixes?  Maybe the first and last?
* And so on...

We are saved by complementary events.  The complementary event is that **no** dice have a six, and this is one that we can do more simply!  This means we can choose any number 1-5 for each of the five dice.  So the multiplication rule says that there are $5^5=3125$ ways that we can completely avoid 6.  So there are $7776-3125=4651$ outcomes which do not avoid 6, and our probability is $P(E) = \frac{4651}{7776}$
</details>

<details class="example" markdown="1">
<summary>Multiple Fair Dice II</summary>
Let's return to the previous example of five fair six-sided dice being rolled.  Now we'll consider the probability that exactly two dice come up as 6.  Just as before, there are $6^6=7776$ outcomes in the sample space.  We just need to determine how many have exaxtly two sixes.

We can device the following procedure to find them all.
1. Choose two dice to make into sixes (**15 options**)
  * This is choosing a subset of size two from the five rolls.  There are $_{5}C_2 = 10$ ways to do so.
2. Choose non-six results for the remaining three dice (**125 options**)
  * There are 5 options for each of the remaining dice, so the multiplication rule gives $5^3=125$ options.
  
In total then there are $10\times125=1250$ ways to get exactly two sixes for a probability of $\frac{1250}{7776}$.  This can be simplified, but we'll leave it as-is.

It is worth noting that we could have implemented this same strategy for exactly 1, 2, 3, 4, or 5 sixes and found the same result as in the previous example.
* There are $5\times 5^4=3125$ ways to get exactly one six.
  * $5$ ways to choose the one die to be a six and $5^4$ choices for the remaining four dice.
* There are $10\times 5^3=1250$ ways to get exactly two sixes as we just established.
* There are $10\times 5^2=250$ ways to get exactly three sixes.
  *${}_5C_3=10$ ways to choose three dice and $5^2$ ways to choose non-six on the remaining two dice.
* There are $5\times 5=25$ ways to get exactly four sixes.
  *${}_5C_4=5$ ways to choose three dice and $5$ ways to choose non-six on the remaining die.
* There is $1$ way to get all five sixes

So in total there are $3125+1250+250+25+1=4651$ ways to get at least one six.  But is is much nicer to use complementary events.
</details>

<details class="example" markdown="1">
<summary>Mixed Committee</summary>
Every month a small company holds a social event.  A (uniformly) randomly selected team of four is in charge of planning.  If the company has 5 senior employees and 15 junior employees, what is the probability that the team consists of two senior and two junior members?

The process produces a subset of size four from the set of 20 employees.  There are 

$$\begin{align*}
{}_{20} C_4 & = \frac{20!}{(20-4)!4!} = \frac{20!}{16!\cdot 4!} \\[1em]
& = \frac{20\times19\times18\times17}{4\times 3\times 2\times 1} \\[1em]
& = 4845
\end{align*}$$

possible teams that can chosen.  This is the number of outcomes in the sample space $S$.

To find the number that have exactly two juniors and two seniors, we devise the following process which can select all possible teams.
1. Choose two of the 5 senior employees (**10 options**)
  * There are ${}_5 C_2 = 10$ options.
2. Choose two of the 15 junior employees (**105 options**)
  * There are ${}_15 C 2 = 105$ options.
  
So in total there are $10\times 105 = 1050$ possible teams by the multiplication rule.  Consequently, the probability is $\frac{1050}{4855}$.
</details>

<div class="warning">
The types of counting problems that can appear in probability questions are diverse.  The general guidance is to break down the process into steps that either (1) have a fixed number of choices or (2) select a subset.  Then use the multiplication rule to find the total number of choices.
</div>

## Learning Objectives
* Use verbal descriptions of a situation to determine probability distributions
* Find probabilities of events given a distributuion.
* Use complementary events (law of total probability) to find probabilities of events.
* Use combinatorial techniques to find probabilities of events in processes with a uniform distributuion.

