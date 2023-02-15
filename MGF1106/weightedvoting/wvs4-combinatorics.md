---
layout: page
usemathjax: true
title: "WVS4: Combinatorics"
---

{% assign basedir = site.url| append: "/MGF1106/weightedvoting" %}
{% assign imgdir = basedir| append: "/images" %}

# Shapley-Shubik Power
[LLoyd Shapley](https://en.wikipedia.org/wiki/Lloyd_Shapley) and [Martin Shubik](https://en.wikipedia.org/wiki/Martin_Shubik) were mathematicians and economists who proposed an alternate method of computing power in weighted voting systems.  While Bazhaf power feels realistic -- one can imagine players in a winning coalition threatening to leave if their demands are not met -- Shapley-Shubik power takes a bit more of a theoretical approach.

In Shapley-Shubik power, one imagines a scenario in which players will vote in order.  We further imagine that all players support the motion.  Remember, this is an *apriori* measurement of power, so it only complicates things to imagine which players support or do not support the motion.  We can still obtain some useful information about power in this case.  As the players vote, at first the motion doesn't have enough votes to pass.  Eventually a player will vote which will push the vote total to meet the quota, and then all votes after that player are inconsequential.  The idea is that player whose votes caused the total to meet the quota, the **pivotal player** is the one who is exercising power.  Of course, the pivotal player depends on the voting order, so one should look at all possible voting orders.  Then power will be determined by how often a player is pivotal. 

## Voting Orders
A voting order conceptually is the same as a preference ballot.  We are ordering the players by who will vote first, second, and so on instead of ordering them by preference.  When specifying a voting order, we will prefer to use pointy braces ($$\langle$$ and $$\rangle$$) because it's the choice in other textbooks.  In the broader mathematical world, just plain parentheses would likely be used.  So to specify a voting order we will just list the players, in order, within pointy braces.  For example $$\left<P_1, P_3, P_4, P_2\right>$$ indicates that $$P_1$$ votes first, followed by $$P_3$$, followed by $$P_4$$, and finally $$P_2$$ votes.  In other books, voting orders may be called **sequential coalitions**.

###  How Many Voting Orders?
Our previous analysis of preference ballots also applies to voting orders.  Just as there were $$N!$$ ways to fill out a preference ballot with $$N$$ candidates, there are $$N!$$ different voting orders when there are $$N$$ candidates.  We will revisit this computation later in the chapter.

## Pivotal Players
Given a voting order, we can compute the **pivotal player**.  Recall that the pivotal player is the player whose vote causes the total to meet the quota.  There will be exactly one pivotal player for each sequential coalition.  Just as with critical players in Banzhaf power, we will underline the pivotal player.

### Example
For the following, we will use the WVS \[8: 5, 4, 3, 2\].
* $$P_2$$ is pivotal in 
$$\newcommand{\ul}{\underline}
\newcommand{\lpb}{\langle}
\newcommand{\rpb}{\rangle}\lpb P_1, \ul{P_2}, P_3, P_4\rpb$$.
  * $$P_1$$ votes first and contributes a weight of 5, which does not yet meet the quota.
  * Then $$P_2$$ votes and contributes a weight of 4.  This brings the total to 5+4=9, which meets the quota.  Therefore $$P_2$$ is pivotal.
* $$P_3$$ is pivotal in $$\lpb P_2, P_4, \ul{P_3}, P_1 \rpb$$
  * $$P_2$$ contributes 4 (not winning)
  * $$P_4$$ contributes 2 (4+2=6, not winning)
  * $$P_3$$ contributes 3 (4+2+3=9, **winning**)
  
## Shapley-Shubik Power
The procedures for Banzhaf power and Shapley-Shubik power are essentially identical.  We just swap "coalition" for "voting order" and "critical player" for "pivotal player."

1. **List all voting orders.**  As previously discussed, there will be $$N!$$ of these when there are $$N$$ players.
2. **Mark the pivotal player in each coalition.**  Unlike Banzhaf power, where there could be many (or no) critical players in a coalition, there will always be exactly one pivotal player in each coalition.
3. **Count the number of times each player is pivotal.**  As for Banzhaf power, we'll use $$C_i$$ to denote each player's pivotal count.  We'd use **P** for **P**ivotal, but that's already taken, so we'll just imagine it's **C** for **C**ount.  The total pivotal count, $$C_T$$, will always be $$N!$$.
4. **Each player's Shapley-Shubik power is their proportion of the pivotal counts.**  The power of $$P_i$$ is computed as $$\displaystyle S_i = \frac{C_i}{N!}$$

For exactly the same reasons as for Banzhaf power, this will define a distribution.

### Example
We will find the Shapley-Shubik power distribution for the WVS [4: 3, 2, 1].  It is a little bit of work to find all of the sequential coalitions, so we'll leave that for later.  For now, we'll take for granted that the sequential coalitions are

$$\begin{align*}
&\lpb P_1, P_2, P_3 \rpb&\, &\lpb P_1, P_3, P_2\rpb&\, &\lpb P_2, P_1, P_3\rpb \\
&\lpb P_2, P_3, P_1 \rpb&\, &\lpb P_3, P_1, P_2\rpb&\, &\lpb P_3, P_2, P_1\rpb \\
\end{align*}.$$

One very nice aspect of Shapley-Shubik power is that this part of the procedure is the same for *every* three player system.  So we'll move straight on to

**2. Mark the pivotal player in each coalition.**

* \\(\lpb P_1, \ul{P_2}, P_3 \rpb\\)
  * $$P_1$$ adds 4 weight (3, not winning)
  * $$P_2$$ adds 2 weight (3+2=5, **winning**)
* \\(\lpb P_1, \ul{P_3}, P_2 \rpb\\)
  * $$P_1$$ adds 4 weight (3, not winning)
  * $$P_3$$ adds 1 weight (3+1=4, **winning**)
* \\(\lpb P_2, \ul{P_1}, P_3 \rpb\\)
  * $$P_2$$ adds 2 weight (2, not winning)
  * $$P_1$$ adds 3 weight (2+3=5, **winning**)
* \\(\lpb P_2, P_3, \ul{P_1} \rpb\\)
  * $$P_2$$ adds 2 weight (2, not winning)
  * $$P_3$$ adds 1 weight (2+1=3, not winning)
  * $$P_1$$ adds 3 weight (2+1+3=6, **winning**)
* \\(\lpb P_3, \ul{P_1}, P_2 \rpb\\)
  * $$P_3$$ adds 1 weight (1, not winning)
  * $$P_1$$ adds 3 weight (1+3=4, **winning**)
* \\(\lpb P_3, P_2, \ul{P_1} \rpb\\)
  * $$P_3$$ adds 1 weight (1, not winning)
  * $$P_2$$ adds 2 weight (1+2=3, not winning)
  * $$P_1$$ adds 3 weight (1+2+3=6, **winning**)

**3. Count the number of times each player is pivotal.**
* $$P_1$$ was pivotal 4 times
* $$P_2$$ was pivotal 1 time
* $$P_3$$ was pivotal 1 time

We know that there ought to be 3!=6 pivotal players, and indeed our counts give a total of 4+1+1=6.

**Each player’s Shapley-Shubik power is their proportion of the pivotal counts.**
* $$P_1$$ has a power of $$S_1 = \frac46$$.
* $$P_2$$ has a power of $$S_2 = \frac16$$.
* $$P_3$$ has a power of $$S_3 = \frac16$$.

This is a power distribution of $$\bigl(\frac46, \frac16, \frac16\bigr)$$.

## Comparison to Banzhaf
Without going into detail we have the following Banzhaf power table for the previous example.

| Coalition | Weight ($$w$$) | Weight to Lose ($$w-q$$)
| :---: | :---: | :---: |
| $$\{\ul{P_1}, P_2, P_3\}$$ | 6 | 2 |
| $$\{\ul{P_1}, \ul{P_2}\}$$ | 5 | 1 |
| $$\{\ul{P_1}, \ul{P_3}\}$$ | 4 | 0 |

The result is a power distribution of $$\bigl(\frac35, \frac15, \frac15\bigr)$$.  This example shows that the two methods produce similar but not identical results.

### Pivotal vs Critical
Even though pivotal and critical players are defined in very different contexts, the two are related.  Note that when we have a marked voting order, for example  $$\lpb P_1, P_3, \ul{P_4}, P_2\rpb$$ we have the following two facts about winning coalitions.

1. $$\lbrace P_1, P_3 \rbrace$$ **is not** a winning coalition, and
2. $$\lbrace P_1, P_3, P_4 \rbrace$$ **is** a winning coalition.

So the pivotal player of the voting order is also a critical player in $$\lbrace P_1, P_2, P_3 \rbrace$$.  Of course, there may be many critical players in that coalition, but the pivotal player is certainly one of them.

### Structure of Pivotal Players
We can push this idea a little bit further to accelerate the process of finding pivotal players.  Suppose $$\lpb P_2, P_1, P_3, \ul{P_4}\rpb$$.  As before, this indicates that $$\lbrace P_1, P_2, P_3\rbrace$$ is **not** winning but $$\lbrace P_1, P_2, P_3, P_4\rbrace$$ is winning.  So whenever $$P_1$$, $$P_2$$, and $$P_3$$ appear at the start of the voting order (in whatever order), if they are followed by $$P_4$$, then $$P_4$$ will be pivotal.  So without any further work we can immediately mark the following:

$$\begin{align*}
&\lpb P_1, P_2, P_3, \ul{P_4} \rpb&\, &\lpb P_1, P_3, P_2, \ul{P_4} \rpb&\, &\lpb P_2, P_1, P_3, \ul{P_4} \rpb&\\
&\lpb P_2, P_3, P_1, \ul{P_4} \rpb&\, &\lpb P_3, P_1, P_2, \ul{P_4} \rpb&\, &\lpb P_3, P_2, P_1, \ul{P_4} \rpb&.\\
\end{align*}$$

All of the above have the non-winning coalition (in some order) followed by the pivotal player known to push the total to meet the quota.

### Dictators and Dummies
A dictator will still have a power of 1.  We showed that every pivotal player is a critical player some winning coalition.  Since a dictator is the *only* critical player in that scheme, it must be that the dictator is also the only pivotal player.  Similarly, a dummy will still have a power of 0 in Shapley-Shubik power.  If a dummy were pivotal in some voting order, then they would be critical in some winning coalition, which is impossible.

### From Winning Coalitions
Just as with Banzhaf power, Shapley-Shubik power can be determined just from a list of winning coalitions.  Again, we will lean on the idea that the players before the pivotal player in the voting order do not make a winning coalition, but the addition of the pivotal player does make a winning coalition.

Suppose that a system has the following winning coalitions.

$$\begin{align*}
\lbrace P_1, P_2, P_3 \rbrace &\, &\lbrace P_1, P_2 \rbrace &\, &\lbrace P_1, P_3 \rbrace \\
\end{align*}$$

**1. List all voting orders.**
The voting orders are the same for every three player system.  We already found them to be

$$\begin{align*}
&\lpb P_1, P_2, P_3 \rpb&\, &\lpb P_1, P_3, P_2\rpb&\, &\lpb P_2, P_1, P_3\rpb \\
&\lpb P_2, P_3, P_1 \rpb&\, &\lpb P_3, P_1, P_2\rpb&\, &\lpb P_3, P_2, P_1\rpb \\
\end{align*}.$$

**2. Mark the pivotal player in each coalition.**

* \\(\lpb P_1, \ul{P_2}, P_3 \rpb\\) - $$\{P_1\}$$ is not winning but $$\{P_1, P_2\}$$ is, so $$P_2$$ is pivotal.
* \\(\lpb P_1, \ul{P_3}, P_2\rpb\\) - $$\{P_1\}$$ is not winning but $$\{P_1, P_3\}$$ is, so $$P_3$$ is pivotal.
* \\(\lpb P_2, \ul{P_1}, P_3\rpb\\) - $$\{P_2\}$$ is not winning but $$\{P_2, P_1\}$$ is, so $$P_1$$ is pivotal.
* \\(\lpb P_2, P_3, \ul{P_1} \rpb\\) - $$\{P_2\}$$ is not winning,  $$\{P_2, P_3\}$$ is still not winning, but $$\{P_2, P_3, P_1\}$$ is so $$P_1$$ is pivotal.
* \\(\lpb P_3, \ul{P_1}, P_2\rpb\\) - $$\{P_3\}$$ is not winning but $$\{P_3, P_1\}$$ is, so $$P_1$$ is pivotal.
* \\(\lpb P_3, P_2, \ul{P_1}\rpb\\) - $$\{P_3\}$$ is not winning,  $$\{P_3, P_2\}$$ is still not winning, but $$\{P_3, P_2, P_1\}$$ is so $$P_1$$ is pivotal.

**3. Count the number of times each player is pivotal.** and
**4. Each player’s Shapley-Shubik power is their proportion of the pivotal counts.**
These can be done together.  There are 3!=6 pivotal players.  $$P_1$$ accounts for 4 of them, while $$P_2$$ and $$P_3$$ have 1 each.  The final power distribution is, as before, $$\bigl(\frac46, \frac16, \frac16\bigr)$$.


## Enumerating Voting Orders
The one topic which we have avoided until now is presenting a method for listing every possible voting order.  Remember, that this is something that depends only on the number of candidates so you won't need to do this for every question.

We know from our previous study of voting methods that there are $$N
!$$ voting orders when there are $$N$$ players.  But this count does not directly become a method for listing all $$N!$$ of them out.  Just as in the voting method section, we will build up from $$N=1$$.  When there is one player, there is but a single voting order: $$\lpb P_1\rpb$$.  When we add $$P_2$$, we see that there are only two ways to add them, either before $$P_1$$ or after.

$$\require{mathtools} \lpb P_1 \rpb \xrightarrow{+P_2} \lpb P_1, {\color{blue}P_2}\rpb, \lpb {\color{blue}P_2}, P_1 \rpb$$

Now for each two-player voting order we have three ways to insert $$P_3$$
* \\(\lpb P_1, P_2\rpb\xrightarrow{+P_3} \lpb P_1, P_2, {\color{blue} P_3}\rpb, \lpb P_1, {\color{blue} P_3}, P_2\rpb, \lpb {\color{blue} P_3}, P_1, P_2\rpb \\)
* \\(\lpb P_2, P_1 \rpb \xrightarrow{+P_3} \lpb P_2, P_1, {\color{blue} P_3} \rpb,\lpb P_2, {\color{blue} P_3}, P_1 \rpb,\lpb {\color{blue} P_3}, P_2, P_1 \rpb\\)

Each of the two two-player voting orders gives rise to three three-player voting orders. This reproduces the list of $$2\times 3 = 6$$ voting orders which we already found previously.  But now we can take the next step and add in $$P_4$$ to get all voting orders for four players. 

* \\(\lpb P_1, P_2, P_3 \rpb\xrightarrow{+P_4} \lpb P_1, P_2, P_3, {\color{blue} P_4} \rpb, \lpb P_1, P_2, {\color{blue} P_4}, P_3 \rpb, \lpb P_1, {\color{blue} P_4}, P_2, P_3 \rpb, \lpb {\color{blue} P_4}, P_1, P_2, P_3 \rpb\\) 
* \\(\lpb P_1, P_3, P_2 \rpb\xrightarrow{+P_4} \lpb P_1, P_3, P_2, {\color{blue} P_4} \rpb, \lpb P_1, P_3, {\color{blue} P_4}, P_2 \rpb, \lpb P_1, {\color{blue} P_4}, P_3, P_2 \rpb, \lpb {\color{blue} P_4}, P_1, P_3, P_2 \rpb\\)
* \\(\lpb P_3, P_1, P_2 \rpb\xrightarrow{+P_4} \lpb P_3, P_1, P_2, {\color{blue} P_4} \rpb, \lpb P_3, P_1, {\color{blue} P_4}, P_2 \rpb, \lpb P_3, {\color{blue} P_4}, P_1, P_2 \rpb, \lpb {\color{blue} P_4}, P_3, P_1, P_2 \rpb\\)
* \\(\lpb P_2, P_1, P_3 \rpb\xrightarrow{+P_4} \lpb P_2, P_1, P_3, {\color{blue} P_4} \rpb, \lpb P_2, P_1, {\color{blue} P_4}, P_3 \rpb, \lpb P_2, {\color{blue} P_4}, P_1, P_3 \rpb, \lpb {\color{blue} P_4}, P_2, P_1, P_3 \rpb\\)
* \\(\lpb P_2, P_3, P_1 \rpb\xrightarrow{+P_4} \lpb P_2, P_3, P_1, {\color{blue} P_4} \rpb, \lpb P_2, P_3, {\color{blue} P_4}, P_1 \rpb, \lpb P_2, {\color{blue} P_4}, P_3, P_1 \rpb, \lpb {\color{blue} P_4}, P_2, P_3, P_1 \rpb\\)
* \\(\lpb P_3, P_2, P_1 \rpb\xrightarrow{+P_4} \lpb P_3, P_2, P_1, {\color{blue} P_4} \rpb, \lpb P_3, P_2, {\color{blue} P_4}, P_1 \rpb, \lpb P_3, {\color{blue} P_4}, P_2, P_1 \rpb, \lpb {\color{blue} P_4}, P_3, P_2, P_1 \rpb \\)

Again, we see that $$P_4$$ can be added 4 ways into each of the 6 three-player voting orders to produce $$6\times 4 = 24$$ four-player voting orders.  We'll stop here because the next level would be 5 ways to insert $$P_5$$ into each of the 24 four-player voting orders for $$24\times5=120$$ five-player voting orders, and that's just too many.

## Learning Objectives
* Determine which player is pivotal in a voting order (sequential coalition)
* Find all possible voting orders a WVS
* Determine the Shapley-Shubik power distribution for a WVS
  * Usually when explicitly weights are given, but also 
  * When only the winning coalitions can be determined.
