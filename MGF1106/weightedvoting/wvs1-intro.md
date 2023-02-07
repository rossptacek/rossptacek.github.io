---
layout: page
usemathjax: true
title: "WVS1: Introduction to Weighted Voting Systems"
---

{% assign basedir = site.url| append: "/MGF1106/weightedvoting" %}
{% assign imgdir = basedir| append: "/images" %}

One of the basic assumptions that we made when studying voting -- so basic that we didn't even state it directly -- is that of "one person one vote."  Everyone gets one vote, and anyone's one vote counts the same as everyone else's one vote.  However, there are many situations where this assumption is thrown out by design, and not everyone's vote counts equally.  Here are a few prominent real world examples.

* The UN Security council consists of 15 members.  Five of the members are permanent members, and ten are temporary members which rotate over time.  Any decision has to be approved by 9 or more of the council's 15 members, but any of the permanent members have veto power.  If they vote no, the decision fails to be approved, even if the other 14 members vote yes.
* The US electoral college consists of electors who actually vote for the president.  It is a convoluted system where the popular vote for president in each state determines how each state will vote for president.  Each state has a number of votes (electors) determined by their representation in congress (senators plus representatives.)  The precise details are not too important here, but the real voters here are the individual states and each state has a different number of votes.
* The President of the United States does not vote on whether to adopt laws or not, but does have veto power.  The veto can be overruled by a two thirds majority of both legislative houses.

Weighted voting systems appear in much more mundane contexts as well.  In publicly traded companies it is typical for shareholders to vote, and instead of "one person one vote" you have "one share one vote."  Many corporate structures will give extra votes or veto power to high ranking employees.  Just like with standard voting, once we define the pattern you'll likely start to see weighted voting systems all over the place.

The bulk of our study will be devoted to determining how powerful the voters (called **players** in these systems) are.  Looking at the examples above, it is clear that some players are more powerful than others.  It is clear, for example, that the permanent members of the UN Security Council have more power than the temporary members.  The permanent members have the same voting rights but an additional veto power.  It's also clear from our experience that California with 55 electors has more power than Alaska with it's 3.  Even though The President has no normal vote in the legislature, their veto power seems to make them more powerful than a senator or representative.

Situations are not always so straightforward, and even when it is clear that there is a power difference it can be difficult to quantify.  Are the permanent members twice as powerful as the temporary ones?  Three times?  And the quantification is often the most important part.  If you were to buy an extra voting share in a company, you would want to analyze the purchase in terms of precisely how much it increases your power.  We will spend most of this section looking at two of the most widely-used methods of computing power, the Banzhaf and Shapley-Shubik methods.  Although they become unwieldy with large systems, with small systems the methods are pretty easy to follow and have some beautiful mathematics under the hood.

## Setting and Terminology
Before we go any further we need to set the stage so that we can precisely discuss weighted voting systems.  To start with, the entities which vote in the system are called **players**.  When players in a weighted voting system vote, they are not casting votes for a pool of candidates as we studied previously.  To make things simpler, players in weighted voting systems are always voting on **motions**.  A motion is a simple yes/no vote, but it can be seen generally as any vote with two options.  If the motion gets enough votes we say it passes, and otherwise it fails.  

Most, but not all, weighted voting systems are easily described by the number of players, how many votes each player has and how many votes are needed to pass a motion.  We will typically use $$N$$ to denote the number of players.  The player names don't usually matter, so we will use $$P_1,P_2,P_3,..., P_N$$ as the default player names.  Each player's number of votes is called that player's **weight**.  We will use $$w_1,w_2,w_3,...,w_N$$ as the weights for $$P_1,P_2,P_3,...,P_N$$ respectively.  The combined weight is denoted by $$W$$.  In other words

\\[ W = w_1 + w_2 + \cdots + w_N\\]

The number of votes needed to pass a motion is called the **quota**.  The compact notation that we use for the whole system is

\\[[q\,:\,w_1,w_2,\cdots,w_N]\\]

It's often easier to read the system if the largest votes come first, so we'll usually reorder the players and weights so they are sorted in descending order ($$w_1$$ is the largest, followed by $$w_2$$, and so on.)

### Example
Consider the WVS $$[10\,:\,5,4,3,1]$$.  There is a variety of information we can determine from the compact notation.
* $$P_2$$ has 4 votes.  Remember that the players are given the default names of $$P_1, P_2,$$ and so on.  Then the weights are given in the same order as the players.
* There are $$5+4+3+1=13$$ total votes in the system.  In other words, for this system $$W=13$$.

### Variable Quota Example
Consider the WVS $$[q\,:\,5,4,3,1]$$.  Here we have specified the players' weights but have left the quota as an undetermined $$q$$.  This is useful when we want to see how changing the quota will affect the system.  For example, we may want to set the quota as a percentage of the total votes.
* If we wanted to require a majority of votes to pass a motion, we would set the quota to $$q=7$$.
  * There are $$5+4+3+1=13$$ total votes in the system.
  * Half of the votes is $$13/2 = 6.5$$.  So to *exceed* half of the votes, we round up to 7.
* If we wanted to require a two-thirds majority of votes to pass a motion, we would set the quota to $$q=9$$.
  * As before, there are $$13$$ total votes in the system.
  * Two thirds of the votes is $$13\times\frac{2}{3}\approx 8.667$$, and the first whole number exceeding that is $$9$$.

### Not Suitable for All Systems
Not all systems are easily put into this notation.  Take for example the UN security council.  It looks like every member has one vote, but how do we indicate the veto power of the permanent members?  We will look at other ways to represent systems, but the notation we just introduced will be the simplest and will work easily in most cases.

## Valid Quotas
In theory, you could write any numbers you want for  the quota and the weights and have a perfectly fine looking piece of notation.  However, with a little bit of thought we see that not just any numbers will do.  Let's look at the system $$[5\,:\,4,3,2,1]$$.  Can you see the problem?  If P1 and P4 vote for a motion while P2 and P3 vote against then the votes will be split 5 to 5.  These two groups (called **coalitions**) both meet the quota, so they could go back and forth passing opposite motions.  The problem is that the quota has been set too low.  To avoid this undesirable situation, sometimes called **anarchy**, any reasonable system will require at least a majority of votes to pass a motion.  There is an equally undesirable situation that occurs if the quota is too high.  If the system were instead \[11 : 4,3,2,1\], then no motion could ever pass.  There are only 10 total votes, but the quota is 11!  In some textbooks, this situation is called **gridlock**.

Let's call $$W$$ the total weight of all players ($$W=w_1+w_2+...+w_N$$.)  Then we can state these conditions with some simple inequalities.
* Requiring a majority of votes means $$q>\frac{W}{2}$$.
* Requiring the quota does not exceed the number of votes means $q\le W$.
These inequalities can be combined into the compound inequality
\\[\frac{W}{2} < q \le W.\\]

## Power in Weighted Voting Systems
Coming up with a reasonable definition of power in a weighted voting system is going to take some serious work.  First we'll look at a few examples to show the need for such systems.  Power is not always easy to ascertain from the players' weights.  Two players with the same weights should have the same power, but almost everything else is up in the air.

### Example: Similar Weights but Very Different Powers
Imagine a company where there are 30 voting shares.  According to company rules, a vote must pass with a two-thirds majority, or 21 votes.  Over time, the shares have been bought up by three individuals who own 11, 10, and 9 shares respectively.  This is the system given by $$[21\,:\,11, 10, 9]$$.  Despite their similar number of votes, the players have very different powers in the system.  Particularly $$P_3$$ has no power at all because $$P_3$$ is irrelevant when it comes to passing a vote.  There are only two scenarios in which a vote can pass:

1. $$P_1$$ and $$P_2$$ decide to vote yes while $$P_3$$ votes no.
2. All three players decide to vote yes.  It may seem like $$P_3$$'s opinion matters here, but it does not.  If $$P_3$$ decided vote no instead, the vote would still pass just with $$P_1$$'s and $$P_2$$'s votes.

So a vote passing depends only on $$P_1$$ and $$P_2$$ agreeing, not on $$P_3$$ at all.  When a voter's opinion doesn't matter, we call that person a **dummy**.  As we get more precise with our definitions we'll return to this term.

### Example: Very Different Weights but Same Powers
Imagine a highly divided US Senate where there are 49 Democrats, 49 Republicans, and 2 independent senators -- I know it's a stretch but let's try.  Ignoring tiebreakers by the Vice President, it takes 51 votes for a bill to pass the US Senate.  Let's stretch a little bit more and imagine that the senators vote strictly along party lines.  Then we can view this as a weighted voting system with three voters: D, R, and I with 49,49, and 2 votes respectively.  This is the system \[51 : 49, 49, 2\].  Note that here D is $$P_1$$, R is $$P_2$$ and I is $$P_3$$.  We're just using slightly more descriptive names for the purpose of the example.

If you only look at the vote counts, you would think that D and R have all of the power while I has very little power.  But if we again look at the ways that a vote could pass, we see a different story.  Here are the four ways that a vote could pass.

1. All three parties vote yes.
2. Any two of the parties vote yes.  This can happen three ways: D with R, D with I, and R with I.

We see from the above description that all three parties are equally powerful.  Each needs only one other ally to pass a motion.
  
## Dictators, Dummies, and Veto Power
Here are some special terms applied to players in a weighted voting system depending how they can make winning coalitions.  This is a first step toward our formal description of power.

* A **dictator** is a player who has enough weight to pass a motion by themself.  In other words, **the dictator's weight is at least as large as the quota**.
* A **dummy** is a player whose vote doesn't matter.  Any collection of players who win with the dummy will still win without the dummy.  This is something that we'll return to when we learn about Banzhaf power.  A player with 0 weight is always a dummy, but players with positive weight can still be dummies. We saw with \[21 : 11,10,9\] that $$P_3$$ was a dummy.
* A player has **veto power** if the all of the other players' combined weight is not enough to pass a motion.  The player with veto power will be in every winning coalition.  Equivalently this means that, as we expect, the player with veto power can prevent any motion from passing by voting no.  In \[21 : 11,10,9\], $$P_1$$ has veto power because the remaining two players have only 10+9=19 weight, which is not enough to win.
