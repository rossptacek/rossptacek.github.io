---
layout: page
usemathjax: true
title: "VT5 - Condorcet Methods"
---

{% assign basedir = site.url| append: "/MGF1106/voting" %}
{% assign imgdir = basedir| append: "/images" %}

Voting methods which satisfy the Condorcet criterion are called Condorcet methods.  Up until this point we have not studied any methods which satisfy the Condorcet criterion!  There are essentially two broad categories of Condorcet methods.  On the one hand there are methods that determine their winner solely through looking at head-to-head matchups (pairwise comparisons) and no other information.  Since the Condorcet candidate will have a flawless head-to-head record, they will be guaranteed the victory.  Other methods first check for the existence of a Condorcet candidate.  If one exists, they are given the victory.  Otherwise an alternate method is used to determine the winner.  This type of strategy can be used to try to "patch" flaws in other voting methods.  For example, the Borda count fails the Condorcet and majority criteria, but you can "fix" it by first electing the Condorcet candidate if one exists and then falling back to a Borda count if one does not exist. 

## Copeland's Method
We'll start by considering the former type, where the entire outcome is determined by the head-to-head matchups.  The simplest example of these is called Copeland's method.  In some books this is called the "method of pairwise comparisons."  Copeland's method functions like a round robin tournament.  Every candidate is paired against every other candidate exactly once.  For each head-to-head matchup won, the candidate earns one point.  A tied matchup earns each candidate involved in the tie 1/2 of a point.  Let's look at a simple example.

### Example
Consider the following preference schedule.

|\# Voters | 14 | 12 | 5 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | C |
| 3rd | C | A | A |

With only three candidates, you should be able to figure out that there are only three comparisons that need to be checked: A vs. B, A vs. C, and B vs. C.  Still it is useful to make an auxiliary table to store the results.

|   | A | B | C |
| :---: | :---: | :---: | :---: |
| A | **A vs A**  | A vs B | A vs C |
| B | **Also A vs B** | **B vs B** | B vs C |
| C | **Also A vs C** | **Also B vs C** | **C vs C** |

We see that the bolded cells do not need to be filled out.  There is no need to compare a candidate with themself.  All of the cells along the diagonal are self-comparisons that can be removed.  In addition, the cells below this diagonal are duplicates of the cells above.  So they can be eliminated.  We're left with the three comparisons we already identified.  Here are the results.

* A loses to B 14 to 17.
* A loses to C 14 to 17.
* B defeats C 17 to 14.

You can always work out a pairwise comparison by counting each candidate's votes, but sometimes it's faster to compute the majority threshold and just stop counting when a candidate reaches it.  For example in the above election there are 31 ballots, so a candidate needs to be preferred on 16 of them to win the comparison.  

The results are shown in the filled out table below.  The unneeded cells are X-d out now.

|   | A | B | C |
| :---: | :---: | :---: | :---: |
| A | **X** | B wins | C wins |
| B | **X** | **X**  | B wins |
| C | **X** | **X** | **X** |

So we see that B has two victories for 2 points, C has 1 point, and A has 0 points.  So the final ranking is B,C,A.  One additional note here is that B is also the Condorcet candidate.  It is easy to detect the Condorcet candidate because **the Condorcet candidate will have N-1 points when there are N candidates**.

## Truncated Preference Ballots
There is no trouble using Copeland's method with truncated or incomplete preference ballots.  Let's return to the example we studied with Ranked Choice Voting.  We've altered it somewhat.

|\# Voters | 20 | 10 | 6 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | B | C | 
| 2nd | C | B | C | D | D |
| 3rd |   | D | B |   | B |
| 4th |   |   | A |   | A |

The only thing that we have to watch out for is that sometimes ballots won't be counted in a comparison, and this can change the majority threshold.  The first column won't count at all if we are computing B vs. D because neither candidate is even present on those ballots.  A more subtle issue is how should we count that first column if we are comparing C to B?  Our point of view is that **candidates not ranked on a ballot should be considered as below any candidate that is ranked**.  So those 20 ballots in the first column would count toward C over B.  Here is the auxiliary table for the four candidates.

|   | A | B | C | D |
| :---: | :---: | :---: | :---: | :---: |
| A | **X** |       |       |       |
| B | **X** | **X** |       |       |
| C | **X** | **X** | **X** |       |
| D | **X** | **X** | **X** | **X** |

We'll go through each of the six comparisons now.
* **A vs. B.** A wins in the first column, but loses in the others except the last.  In the last column, neither is listed so neither wins that ballot.  Note that even though B is not listed in the first column, because A is listed we count A as preferered over B.  So it is 20 for A and 10+6+4=20 for B, and A and B tie.
* **A vs. C.** A wins in the first column with 20.  C wins in the other columns.  The exception is the fourth column where neither A nor C is listed.  So it is 20 for A and 10+6+1=17 for C, so A wins.
* **A vs. D.** A wins by default in the first column for 20 votes.  Hoewever, D wins in all of the other columns for 10 + 6 + 4 + 1 = 21 votes.  So D wins.
* **B vs C.** C wins in every column except the one where it is not present for an overwhelming victory.
* **B vs D.**  B wins in the second and fourth columns for 10 + 4 = 14 votes while D wins in the third and fifth for 6 + 1 = 7 votes.  So B wins.
* **C vs. D.** C wins in all columns except the fourth.  That makes 20+10+6+1=37 for C and 4 for D so C wins.

The final matchup table looks as follows.

|   |   A   |   B   |   C   |   D   |
| :---: | :---: | :---: | :---: | :---: ||
| A | **X** | A, B Tie | A wins | D wins |
| B | **X** | **X** | C wins | B wins |
| C | **X** | **X** | **X** | C wins |
| D | **X** | **X** | **X** | **X** |

C earns 2 points, A and B earn 1.5 points each, and D earns 1 point.  So while C is the clear winner, some tiebreaker would be needed to determine who finished in second place.  Note that there is no Condorcet winner here.  Each candidate manages to lose one of their comparisons.

This example also illustrates a significant issue with Copeland's method:  **Ties appear frequently**.  In the above example, there were only 6 possible points to hand out.  The only way that these points could be allocated without a tie at some rank is if the candidates earned 0,1,2, and 3 points repsectively.  There are a few other options when candidates can tie in the head-to-head comparisons, but we consider ties between candidates to be fairly rare events.  So methods like these are unlikely to produce a full ranking by themselves.

## How Many Matchups?
One interesting mathematical question here is how many different head-to-head matchups do we need to consider?  Copeland's method may stop being so useful if the number of comparisons grows too quickly as the number of candidates grows.  Let's look at what the matchup table would look like for N candidates.

|   | 1 | 2 | 3 | ... | N |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1   | **X** |       |       |       |       |
| 2   |       | **X** |       |       |       |
| 3   |       |       | **X** |       |       |
| ... |       |       |       | **X** |       |
| 4   |       |       |       |       | **X** |

Now remember that self-comparisons marked with an **X** are unneeded, and we only have to count _half_ of the remaining boxes because the ones above and blow the **X** diagonal are redudant.  This number turns out to be easy to count.  There are $$N\times N$$ boxes total, and $$N$$ of them have been **X**-ed out, so there are $$N\times N - N = N(N-1)$$ other boxes.  And then half of that is simply $$\frac{N(N-1)}{2}$$.

There's another interesting way to think about counting the boxes in the top half of the table.

|   | 1 | 2 | 3 | ... | N |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1   | **X** |   1   |   2   |   ...   |   N-1   |
| 2   |       | **X** |   2   |   ...   |   N-1    |
| 3   |       |       | **X** |   ...   |   N-1    |
| ... |       |       |       | **X** |   N-1    |
| 4   |       |       |       |       | **X** |

Counting column at a time, we see that ther are $$1 + 2 + 3 + \cdots + (N-1)$$ boxes, so we have the identity

$$1 + 2 + 3 + \cdots + (N-1) = \frac{N(N-1)}{2}.$$

If we had started with N+1 candidates instead of N, then we would have

$$ 1+2+3+\cdots+(N-1)+N = \frac{(N+1)(N)}{2}.$$

And this is exactly the formula we came up with for the number of Borda points on a ballot with N candidates.  At the time, we had no justification of it, but now we do!

## Fairness Criteria

Copeland's method **satisfies the Condorcet condition**.  If there are N candidates, the Condorcet candidate will win all N-1 head-to-heads for N-1 points.  Everyone else will lose at least the matchup versus the Condorcet candidate, so they will all have less than N-1 points.  Therefore the Condorcet candidate will be the winner by points. Since Copeland's method satisfies the Condorcet criterion **it satisfies the majority criterion** for free.  A majority candidate will be the Condorcet candidate.  **Copeland's method even satisfies the majority loser criterion**.  A candidate with a majority of last place votes can not win any head-to-head matchups and every other candidate will at least earn a point from beating the majority loser.  **Copeland's method even satisfies monotonicity**.  Improving a candidate on some ballots can only increase the number of points that candidate earns.  Because improving the candidate does not change the relative order of the other candidates, it only changes matchups involving the moved candidate.

The bad news is that Copeland's method still fails independence of irrelevant alternatives.  Let's look at the following situation.  Four people (Alice, Bob, Carol, and Dale) are applying for a job at the same company.  The 36 employees of the company rank the applicants.  They will choose who to hire according to Copeland's method.  The results are shown in the preference table below.

|\# Voters | 11 | 9 | 7 | 6 | 3 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | B | A | D | C | D | 
| 2nd | A | C | B | A | C |
| 3rd | C | D | C | D | B |
| 4th | D | B | A | B | A |

Just as before, because the election has four candidates we have six pairwise comparisons to consider.
* A vs. B.  B earns 11+7+3=21 votes to A's 9+6=15 votes so **B wins**.
* A vs. C.  A earns 11+9=20 votes to C's 7+6+3=16 votes so **A wins**.
* A vs. D.  A earns 11+9+6=26 votes to D's 7+3=10 so **A wins**.
* B vs. C.  B earns 11+7=18 votes to C's 9+6+3=18 so **B and C tie**.
* B vs D.  D earns 9+7+6+3=25 votes to B's 11 so **D wins**.
* C vs. D.  C earns 11+9+6=26 votes to D's 7+3=10 to **C wins**.

The matchup table looks like this for the election.

|   |   A   |   B   |   C   |   D   |
| :---: | :---: | :---: | :---: | :---: ||
| A | **X** | B wins | A wins | A wins |
| B | **X** | **X** | B, C tie | D wins |
| C | **X** | **X** | **X** | C wins |
| D | **X** | **X** | **X** | **X** |

According to Copeland's method, A should win with two points, B and C come in second with 1.5 points, and D finishes last with one point.  So the result of Copeland's method would be that A is given a job offer.

Let's say that after the ballots are cast but before the result is announced that Dale informs the company that he has accepted a job elsewhere and he no longer wishes to be considered for the position.  That's no problem!  His removal will have no effect on the comparisons which do not involve candidate D.  So we can just blank out D's comparisons and recompute!  The IIA criterion says that Dale dropping out shouldn't change the winner in a fair system.  Let's see what happens.

|   |   A   |   B   |   C   |   D   |
| :---: | :---: | :---: | :---: | :---: ||
| A | **X** | B wins | A wins | **X** |
| B | **X** | **X** | B, C tie | **X** |
| C | **X** | **X** | **X** | **X** |
| D | **X** | **X** | **X** | **X** |

To indicate Dales's removal, his comparisons have been X-ed out of the table.  The removal does not influence any of the other comparison.  So now B wins with 1.5 points, A comes in second with 1 point, and C comes in last with half a point.  Removing (the irrelevant) D from consideration changed the winner from A to B.  This is a violation of IIA.  The reason this happens is that D performed poorly against every candidate except for B.  So removing B took away a point from everyone except for B.

For the other definitions of IIA, we'll note that if D had just been moved to last place on every ballot the same thing would have happened.  A and C already beat D, so they would get no extra points.  However now B will beat D and get an extra point to win the election with 2.5 points to A's 2 and C's 1.5.  Either way we can produce a violation.

## Tactical Voting

Copeland's method (and other Condorcet methods) are vulnerable to burying and compromising.  It is not too difficult to insincerely shift candidates up and down to influence their head-to-head matchups.  There's a related, but distinct, type of tactical voting called push-over voting.  This involves elevating the position of a weaker candidate like compromising.  The difference is that the intetion with push-over voting is not for that candidate to win but for that candidate's elevation to weaken other candidates so that the tactical voter's choice will win.  Here's an example election where we can witness this.

|\# Voters | 11 | 10 | 2 | 1 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | C |
| 2nd | B | A | C | A |
| 3rd | C | B | A | C |
| 4th | D | D | B | B |

Here are the results:
* A beats B 24 to 0 (1 point for A)
* A ties C 12 to 12 (1/2 point for A,C)
* A beats D 21 to 3 (1point for A)
* C beats B 13 to 11 (1 point for C)
* C beats D 24 to 0 (1 point for C)
* B beats D 21 to 3 (1 point for B)

The result is an order of A=C,B,D.  A and C both have 2.5 points, B has 1 point, and D has 0 points.  If the first column's voters make insincere votes by changing their ballot to A,B,D,C then all of the matchups stay the same except that now D beats C 14 to 10.  This takes a point from C and gives it to D.  So the new order is A,C,B=D.  A has 2.5 points, C has 1.5 points, and both B and D have 1 point.  This is an example of push-over voting.  The A supporters elevated D not so that D would win but to damage one of C's matchups.

## Two Step Methods (Advanced)
Remember that a two step Condorcet method is one that elects the Condorcet candidate if one exists and will otherwise pass to some other method.  However, it is common for these methods to do a little bit of elimination before passing the reins to the other method.  The idea is to find what is called a **dominating set** of candidates.  A set of candidates is a dominating set if every candidate inside of the set beats every candidate outside of the set.  The idea is that all of the candidates outside of the dominating set can be eliminated as a weak candidate.  If the voters were asked whether they prefer a candidate from inside the set or outside the set, the answer is always the one inside the the set.  This is similar to our reasoning for why the Condorcet candidate is a good choice.  The idea is to find the smallest possible dominating set, equivalently we want to eliminate as many candidates as possible.  The smallest dominating set is called the **Smith set**.  Voting systems that always elect a member of the Smith set satisfy the Smith criterion.  The Smith criterion is a more more general version of the Condorcet criterion.

So how do we find the Smith set?  The key observation is that if a candidate is in the Smith set, then so is every candidate who beats or ties them.  We work backwards in this manner and keep adding candidates who beat the candidates in our dominating set.  When we're out of candidates to add, we know that the dominating set candidates beat everyone else!  Do this with every candidate, and you'll find the smallest dominating set.  Let's see this in action.  To save time, we're going to skip the preference schedule and go straight to the matchup table.

|   |   A   |   B   |   C   |   D   |  E  |
| :---: | :---: | :---: | :---: | :---: | :---: |
| A | **X** | B wins | C wins | A, D tie | E wins |
| B | **X** | **X** | B wins | B wins | B, E tie |
| C | **X** | **X** | **X** | C wins | E wins |
| D | **X** | **X** | **X** | **X** |  E wins|
| E | **X** | **X** | **X** | **X** | **X** |

Pick a candidate at random, say A, and see who else has to be added to a dominating set containing A.
Because B, C, and E beat A, they all must be added.  Since D ties with A (A does not beat D either) then D must be added too.  Now we've added all the candidates, so the dominating set that begins with A is A,B,C,D, and E.  This doesn't really help us because we don't eliminate anyone.

Can we do better?  Let's pick another candidate other than A, say C, to start with.  C is beaten by B and E so they must be added.  Now we must add everyone who beats B and E.  We see that the only candidate who isn't beaten by B is E (they tie) and the only candidate who isn't beaten by E is B.  So we don't have anything new to add.  So the dominating set that begins with C is C,B, and E.  Note that this is smaller than before, and now we know that A and D are eliminated.

The only non-eliminated and non-checked candidates left to check are B and E. If we check either B or E, we see that they are undefeated and only tie one another.  So the smallest dominating set containing them is just B and E.

The result of this all is that the smallest dominating set, the Smith set, is just B and E.

## Learning Objectives
* Compute the ranking of candidates according to Copeland's method.
* Explain which fairness criteria are satisfied and not satisfied by Copeland's method.
  * Satisfies all criteria we've discussed except for IIA.
* Understand how tactical voting (particularly pushover voting) can impact Copeland's method.
* (Advanced) Compute the Smith set of an election.

[Next: VT6 - Fairness in Elections]({{basedir}}/vt6-fairness.html)
