---
layout: page
usemathjax: true
title: "VT5 - Condorcet Methods"
---

{% assign basedir = site.url| append: "/MGF1106/voting" %}
{% assign imgdir = basedir| append: "/images" %}

## Fairness Criteria
During our study, we've looked at a number of fairness criteria.  To review, each fairness criterion provides a way that an election can fail to be fair.  They are all stated as "If an election is fair then X" where X is the particular criterion, but this is the same as saying "An election is unfair if X can fail to happen."  Let's review the fairness criteria we've looked at so far.  These five are far from comprehensive, but as we'll see they're enough to make the point we're after.
* **The Majority Criterion.**  If a candidate has a majority of the first place votes, then that candidate should win first place in the election.  (It is unfair for a majority candidate to not win.)
* **The Condorcet Criterion.**  If a Condorcet candidate (wins all head-to-head matchups) exists then that candidate should win the election.  (It is unfair for a Condorcet candidate to not win.)
* **The Monotonicity Criterion.**  If the ballots are changed so that a candidate is ranked higher on some ballots with no other changes to the relative rankings of candidates, then that candidate's ranking should not decrease in the election's result.  (It is unfair if improving a candidate on some ballots worsens their overall result.)
* **The Idependence of Irrelevant Alternatives (IIA) Criterion.**  If a candidate other than the winner were to drop out of the election, then the winner should not change.  (It is unfair if a loser dropping out changes the winner.)

These four are the main criteria we looked at but we also saw a few others along the way.  These are less important to remember.
* **The Majority Loser Criterion.**  If a candidate has a majority of the last place votes, then that candidate should not win the election.
* **The Condorcet Loser Criterion.**  If a candidate loses every head-to-head matchup, then that candidate should not win the election.
* **The Smith Criterion.**  The voting system always elects a member of the Smith set.

## Who's the Fairest of Them All?
As we were discussing the various voting methods that we studied, they all had some problem with them.  Plurality violated the Condorcet criterion.  It turns out it also violates the IIA criterion.  We showed that the Borda count violated the majority criterion, and it too can be shown to violate the IIA criterion.  Instant Runoff Voting violates monotonicity and IIA.  Copeland's method manages to satisfy all of the main four except for IIA.  It seems like we point our finger at any voting method and declare it unfair.  And indeed we can.

Kenneth Arrow proved what is called Arrow's Impossibility Theorem.  It states that every voting method will have a problem with one of the four major fairness criteria we listed.  While reading up until now, it may have seemed possible to find the perfect method.  Maybe we could find the perfect way to eliminate candidates or the right balance of points for a Borda count.  But Arrow's theorem definitively says that if your definition of fairness includes those four main criteria, then you're out of luck.

So why bother?  What is the point of learning about all of these different methods if they're all flawed?  The fact that they're all flawed is the point.  If there were a best, fairest voting method then we would learn it and be done with it.  The fact that every method will have issues highlights the need to be able to analyze them.  In this class we've learned some basic ways of assessing voting methods in the fairness criteria, and these are basic tests that can be applied to any voting method you are to encounter.  Remember, elections are everywhere!

Hopefully by now you see that while every method is flawed, some are more flawed than others.  We've seen how the plurality method that our (the US) system essentially uses has critical flaws.  Other than its fairness violations and the fact that it ignores preference beyond first place, plurality is easily gamed in a way that leads to third parties being squeezed out.  But change is impossible without an electorate broadly aware of the problems and equipped to analyze potential solutions.

The rest of this section will be devoted to some more detailed analysis of the various fairness criteria.  One way "out" of Arrow's theorem is to find faults in the fairness criteria.  We'll conclude with a few more examples of how various methods violate fairness criteria.

## IIA Criterion Criticism
You may have noticed that every method that we discussed is a violation of the IIA criterion.  One of the primary criticisms raised about Arrow's theorem is that IIA is just too strong of a criterion.  Let's briefly review the IIA criterion.  The IIA criterion says that the electorate's preferences between two options should not be influenced by the addition or removal of other options.  There's a famous Sidney Morgenbesser quip about why IIA is desirable.

>Morgenbesser, ordering dessert, is told by the waitress that he can choose between apple pie and blueberry pie. He orders the apple pie. Shortly thereafter, the waitress comes back and says that cherry pie is also an option; Morgenbesser says "In that case I'll have the blueberry pie."

The above is supposed to indicate why IIA is natural.  We are supposed to think Morgenbesser is crazy for choosing blueberry at the end because we already established that he prefers apple to blueberry.  The addition of cherry shouldn't change that, right?  This definitely makes sense for an individual but for a group things are less clear.  Now let's imagine that we're ordering pie for the whole table.  For whatever reason the whole table has to order the same kind of pie.  A preference schedule might look like the following.

|\# Voters | 10 | 9 | 8 |
| :---: | :---: | :---: | :---: |
| 1st | A | B | C |
| 2nd | B | C | A |
| 3rd | C | A | B |

If you ask the table "Apple or blueberry?" the result is Apple winning 18 to 9.  But if cherry is added in, now we have a cycle.  Apple beats Blueberry, Blueberry beats Cherry, and Cherry beats Apple.  The mere fact that Apple is preferred to Blueberry does not prevent Blueberry from being the overall winner.

In some sense, IIA is at odds with the majority criterion.  It's impossible for a method which satisfies both criteria to provide a winner when there's a cycle as there is above.  If the method produces A as a winner, then we have a problem because B dropping out would make C the winner because C beats A.  This violates IIA.  If  B were to win, then C dropping out causes a violation, and if C were to win then A dropping out causes a violation.  We can create problems like these any time there isn't a Condorcet candidate.

So at a glance it may seem like Arrow's theorem is not such a big deal after all.  However, there are weaker (but more complicated) versionsn of IIA for which Arrow's theorem still holds.  Since this is an introductory class, we won't dive too deeply into this.  Still, it is valid to complain that IIA as we've stated it is a tad too strong of a fairness criterion to be useful.

##Condorcet Criterion Criticism
Proponents of IRV and RCV will be quick to tell you that the Condorcet criterion is not necessarily one that you want.  IRV and RCV, of course, do not satisfy the Condorcet criterion.  Their criticism is similar to the line of reasoning that lead to the problems we found with IIA.  With IIA we can remove candidates until we're down to a head-to-head matchup without changing the winner, but just asking questions about head-to-head matchups doesn't show the full picture.

RCV proponents argue that Condorcet methods produce middle of the road candidates who won't really make anyone happy, just satisfied.  We looked at a similar example in reverse when studying the plurality method.

|\# Voters | 41 | 40 | 10 | 9 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | C |
| 2nd | C | C | A | B |
| 3rd | B | A | B | A |

In the preference schedule above, candidates A and B are from the "major parties" while C is a more centrist third party.  Under plurality, tactical voting incentivizes third party supporters to make a compromising vote.  In a Condorcet method, the third party wins every time.  So you'll always have a candidate that 19% of the electorate actually like.  Remember, a ballot of A,C,B doesn't mean that the voter sort of likes C.  It could be that the ballot hates C but hates B even more.  It isn't hard for the Condorcet candidate to actually be somewhat unpopular.
