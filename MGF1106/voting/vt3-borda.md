---
layout: page
usemathjax: true
title: "VT3 - The Borda Count Method"
---

{% assign basedir = site.url| append: "/MGF1106/voting" %}
{% assign imgdir = basedir| append: "/images" %}

[Jean-Charles de Borda](https://en.wikipedia.org/wiki/Jean-Charles_de_Borda) was another 18th century French mathematician who studied voting theory.  If you read the Wikipedia article, you can see that he also was a metric system fanatic who proposed, among other things, a 10 hour day with 100 minutes per hour.  He and Condorcet were aware of one another's work on voting theory and disagreed on how voter preferences were best served.  While Condorcet's analysis involved pairwise comparison's Borda's focused only on the raw number of first place, second place, third place, and so on votes that each candidate received.  In other words, for Borda the information in this preference schedule:

|\# Voters | 10 | 5 | 5 | 2 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | B | D | C | 
| 2nd | B | B | D | C | D |
| 3rd | C | D | C | B | A |
| 4th | D | A | A | A | B |

could be reduced to the following table:

| Candidate | \# 1st | \# 2nd | \# 3rd | \# 4th |
| :---: | :---: | :---: | :---: | :---: |
| A | 10 | 0 | 1 | 12 |
| B | 5 | 15 | 2 | 1 |
| C | 6 | 2 | 15 | 0 |
| D | 2 | 6 | 5 | 10 |

Note that this is less information than the full preference schedule.  If you only have the counts of the votes, you can not in general reproduce the preference schedule.  You can interpret its lower complexity as something of an advantage.

So how does Borda turn the point counts into an outcome?  A Borda count assigns a point value to each type of votes.  Typically a last place vote is worth a single point, a second-to-last place vote is worth 2 points, and so on.  A first place vote would then be worth N points where N is the number of candidates.  Let's see how this election would turn out with a standard Borda count.

* A has **10**×4+**0**×3+**1**×2+**12**×1=54 points.  This is so because A has **10** first place votes, **0** second place votes, **1** third place vote, and **12** last place votes.
* B has **5**×4+**15**×3+**2**×2+**1**×1=70 points.
* C has **6**×4+**2**×3+**15**×2+**0**×1=60 points.
* D has **2**×4+**6**×3+**5**×2+**10**×1=46 points.

### Alternate Point Systems

There's nothing special about the point assignments 1,2,...,N that we usually use.  For example, the Cy Young voting system uses a Borda count.  Voters list their top five choices.  The points assigned are 7 (first) ,4,3,2, and 1 for last place.  The Cy Young voting also demonstrates that a truncated preference ballot is compatible with the Borda count.  There are more than five pitchers in the league, but voters only rank five of them.  

There's nothing wrong with fractional point values either!  The Republic of Nauru uses a Borda count where a first place vote is worth a whole point, a second place vote is worth 1/2 of a point, a third place vote is worth 1/3 of a point and so on.  The only important feature is that higher rank votes are worth more point than lower rank votes.

## Counting Points

One potential time save for the Borda count is that we can somewhat easiliy compute the total number of points in an election.  They key is that each ballot will award the same number of points.  For example, with three candidates, each ballot in a standard Borda count awards 3+2+1=6 points because it gives one first place, one second place, and one third place vote.  If there are 11 voters, then each of the 11 voters would award 6 points for 11×6=66 total points.

This has the potential to save time and/or check your work.  Let's take another look at our first example.

|\# Voters | 10 | 5 | 5 | 2 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | B | D | C | 
| 2nd | B | B | D | C | D |
| 3rd | C | D | C | B | A |
| 4th | D | A | A | A | B |

* There are four candidates in the election, so each ballot is awarding $$4+3+2+1=10$$ points in total.
* We can sum up the top row of the preference schedule to see that there are $$10+5+5+2+1=23$$ voters in the election, and so 23 ballots will be counted.
* If there are 23 ballots and 10 points per ballot then there will be $$23\times10 = 230$$ points in the entire election.

You can use this in a two main ways.
1. You can try to use this as a shortcut.  In the above, we may have computed A, B, and C to have 54, 70, and 60 points respectively.  This accounts for $$4+70+60=184$$ points.  So it follows that candidate D must have $$230-184 = 46$$ points.  However, this is dangerous because if you made an error computing for any of A, B, or C then your answer for D will also be wrong.
2. (Preferred) You can use this to check your work.  Once you've computed the point totals.  Verify that they sum up to the right thing.  If you've made an error, you will almost always detect it this way.

### An Interesting Formula
What if there were 10 candidates?  It's a little cumbersome, but we can compute 1+2+3+4+5+6+7+8+9+10=55 points per ballot.  But what if there were 20 candidates?  Or 100 candidates?  Of course it's hard to imagine that there's an election with this many candidates, but who knows!  It turns out that sums of this form actually come up all the time, and this is just one example.  In fact, it will come up again when we cover Copeland's method for voting.  For now, we'll just say that there's a fairly fast formula for adding up 1+2+...+N.

$$ 1+2+\cdots+(N-1)+N = \frac{N(N+1)}{2}. $$

We'll check a few cases just to see how the formula works.
* For N=3 we have $$ 1+2+3 = 6 = \frac{3(3+1)}{2}$$. 
* For N=4 we have $$ 1+2+3+4 = 10 = \frac{4(4+1)}{2}$$.

We'll justify this formula in a bit more detail when we cover Copeland's method.

### Example: Fewest Points to Win
This is another application of point counting for a Borda count.  In the previous example, we saw that there were 230 points in the election and 4 candidates.  If the four of them split the vote evenly, then each would have 230/4=57.5 points.  Of course fractional points are impossible, so this means you would need at least 58 points in order to win.

It's a minor point, but in this case, winning with 58 points would require a tiebreaker because if one candidate has 58 points and the rest have 57, that's only 58+3×57 = 229 points.  This is short of the 230 we know we have, so it must be that at least two candidates have 58 points.  In order to win without a tiebreaker, you would need 59 points.

## Majority Loser Criterion
We saw that one of the flaws of the plurality method was that it can elect a candidate who has a majority of the last place votes.  It turns out that the Borda count does fix this problem.  This is very hard to prove though.  There are so many (infinitely many) different ways that you can write a preference schedule where a candidate has a majority of last place votes, and you would need to check them all to be certain!

However, the work we just did gives us an out.  We showed that you need at least 1/N of the total points to have a chance of winning where N is the number of candidates.  Let's say that there are M total voters.  Our work showed that there are

$$ T = M\times\frac{N(N+1)}{2}$$

total points in the election.  So in order to win the election you need _at least_

$$ \frac{T}{N} = M\times\frac{N+1}{2}$$

total points.  So all we have to show is that there's no way to get that many points when you have a majority of the last place votes.  Roughly speaking, if you have a majority of the last place votes and there are M voters you have at least M/2 last place votes.  Your best possible case is to have the rest be first place votes.  You'll get 1 point for each last place vote and M points from each first place vote.  Call X your best possible score, then

$$\begin{align*}
X &< \left(\frac{M}{2}\times 1\right) + \left(\frac{M}{2}\times M\right)\\
X &< \frac{M}{2}\times(N+1)\\
X &< \frac{T}{N}
\end{align*}$$

So the majority loser's best score can never win!  Note that it is much more difficult to show that a method satisfies a fairness criterion than to show that it violates one.  To show that a method satisfies a fairness criterion, we need to come up with a way to incorporate all possible elections in a single argument.  To show that a method violates a fairness criterion we need only come up with one particular election where the criterion is violated.

## The Majority Criterion

The Borda count is not so lucky when it comes to the majority criterion.  Remember that the majority criterion says that if a voting system is fair, then it should elect a candidate with a majority of first place votes without fail.  In other words, it is unfair if it is possible for a majority winner to not win the election.

|\# Voters | 51 | 49 |
| :---: | :---: | :---: |
| 1st | A | C |
| 2nd | B | B |
| 3rd | C | D |
| 4th | D | A |

In the above election A has a majority of first place votes, but let's see how the point totals work out.
* A has 51×4+49 = 253 points.
* B has 100×3 = 300 points.
* C has 51×2+49×4 = 298 points.
* D has 51×1+49×2 = 149 points.

So the majority candidate is not the winner!  In fact, candidate A places 3rd behind both B and C.  So **the Borda count is unfair according to the majority criterion**.  Note that this automatically means that **the Borda count is unfair according to the Condorcet criterion**.  The majority candidate is automatically the Condorcet candidate, so failure to elect the majority candidate is also failure to elect the Condorcet candidate.  This explains Condorcet's misgivings about Borda's method.

## Independence of Irrelevant Alternatives (IIA)
The idea of [independence of irrelevant alternatives](https://en.wikipedia.org/wiki/Independence_of_irrelevant_alternatives) (IIA for short) is a little bit complicated, and there are many different ways to express it.  You can see this if you try to read the linked Wikipedia article.  The central idea behind it is that if A is preferred to B in an election, then people changing their mind about another candidate, say candidate C, shouldn't change that fact.  Everyone keeps their relative opinions of A and B the same in this scenario. So if A was above B before they changed their mind about C, then A will still be above C after.  

<figure>
    <img src="{{imgdir}}/IIA-Change.svg" alt="C is changed while A and B's relative order remains."/>
    <figcaption> In the above ballots, the relative ranking of A and B is unchanged on each ballot.</figcaption>
</figure>

In the above image, the arrows show how each voter changes their ballot.  While their opinions about C and D may have changed, their relative opinions about A and B have not.  If A is above B in the original election, it still is after the changes.  So these changes _should_ be irrelevant to whether A is preferred above be in the election.  At least this seems to something desirable for a voting system to have.

At this level of study, the full IIA criterion is difficult to work with.  So we'll simplify it a bit.  Instead of looking at arbitrary changes to the preferences which don't change the relative ranks of two candidates (like the above), we'll look at one particular type of change.  We'll look at how the winner changes if one of the other candidates drops to the bottom of the preference table on every ballot.  In some books they just assume that the candidate drops out of the race, and this is good enough for our purposes.  So the simplified IIA criterion is that if a voting system is fair, then a non-winner dropping out should not change the winner of the election.  Equivalently, a voting method is unfair if a candidate who would not win (is irrelevant) can change the winner by dropping out.

<figure>
    <img src="{{imgdir}}/PreferenceSchedule-Borda-IIA.svg" alt="Preference schedules showing the removal of candidate D."/>
    <figcaption> The original preference schedule (left), a modification where D is moved last (D), and a modification where D is removed (right).</figcaption>
</figure>

In the original election we have
* A has 51×4+49 = 253 points,
* B has 100×3 = 300 points,
* C has 49×4+51×2 = 298 points, and
* D has 51+49×2 = 149 points.

So B (barely) wins the election.  Now imagine a scenario where candidate D is rocked by a scandal and is forced to withdraw from the election.  Then our preference schedule looks like the one on the right in the image above.  In this new scenario we have
* A has 51×3+49 = 202 points,
* B has 100×2 = 200 points, and
* C has 49×3+51×1 = 198 points.

Now A wins the election!  And this would seem unfair to B supporters.  Why should the withdrawal of the last place candidate change the result of the election?  A similar effect happens even if D is just moved to last place on all ballots, but that is left as an exercise to the reader.

IIA may make sense at a glance.  We don't want the introduction/removal of candidates to change the rankings of the other candidates.  However, a closer look will show that IIA might be asking for a little bit too much. We'll look more at IIA in other sections, especially when we give a more thorough treatment to all of the fairness criteria.

## Teaming
We saw how the removal of a candidate could shake up an election.  The other side of this is the the introduction of new candidates can do the same.  Imagine instead that we start in the scenario above where only A, B, and C are running.  B supporters might urge a very unpopular candidate such as D to run, knowing that the result will make candidate B.  Teaming is a version of this where a party will enter multiple, similar candidates to improve their changes of victory.  You won't see this in plurality elections because dividing your voters up is clearly a problem, but the Borda count is quite susceptible to teaming.

### Teaming Example
Imagine a situation from US polities where Republicans and Democrats evenly split the electorate.  Instead of the usual plurality voting that we do in the US, the election will be held with the Borda count.  The Democratic party will send two candidates into the election, D1 and D2, while the Republican party will just send one candidate, R.  The preference schedule may look something like this.

|\# Voters | 25 | 25 | 45 | 5 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | R | R | D1 | D2 |
| 2nd | D1 | D2 | D2 | D1 |
| 3rd | D2 | D1 | R | R |

Here is a more detailed description of the preference table.
* The first two columns are the 50% of the population who support the R party.  They randomly choose whether to put D1 or D2 in second place.
* The second two columns are the 50% of the population who support the D party.  90% of them (45 of 50) support D1 and 10% of them support D2.  All of them put the R candidate in last place

And we can see the results are as follows:
* R gets 50×3+50 = 200 points,
* D1 gets 45×3+30×2+25 = 220 points, and
* D2 gets 5×3+70×2+25 = 180 points.

Now you may think that this is just a matter of R supporters choosing their second place votes 50-50 when they should just put the stronger D party candidate last.  This is an example of tactical voting called **burying**.  We'll see that this doesn't work either!

|\# Voters | 50 | 45 | 5 |
| :---: | :---: | :---: | :---: |
| 1st | R | D1 | D2 |
| 2nd | D2 | D2 | D1 |
| 3rd | D1 | R | R |

And now the results are can see the results are as follows:
* R gets 50×3+50 = 200 points,
* D1 gets 45×3+5×2+50 = 195 points, and
* D2 gets 5×3+95×2 = 205 points.

This should make some sense in the context of computing total points.  No matter what, the R candidate will get 50 first place and 50 last place votes for 200 points.  We can compute that there are 100×6=600 points. It is possible that the R voters perfectly split their votes between D1 and D2 so that they both get 200 points resulting in a 3-way tie, but if they don't vote perfectly, one of D1 or D2 will have more than 200 points.  In practice, it is impossible to do this because it also depends on how the Democrats split their support between D1 and D2.  So teaming has turned a 50-50 tie into an almost-assured win for one party.

## Learning Objectives
* Compute the ranking of candidates according to the Borda count method.
* Explain which fairness criteria are satisfied and not satisfied by the Borda count method.
  * The Borda count method does not satisfy the majority criterion.
  * The Borda count method does satisfy the majority loser criterion.
  * The Borda count method does not satisfy the Condorcet criterion.
* Demonstrate how teaming works under the Borda count.
* Determine how voters may vote tactically (burying) under the plurality method. 

[Next: VT4 - Elimination Methods]({{basedir}}/vt4-elimination.html)


