---
layout: page
usemathjax: true
title: "VT6 - Fairness in Election"
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

So at a glance it may seem like Arrow's theorem is not such a big deal after all.  However, there are weaker (but more complicated) versions of IIA for which Arrow's theorem still holds.  Since this is an introductory class, we won't dive too deeply into this.  Still, it is valid to complain that IIA as we've stated it is a tad too strong of a fairness criterion to be useful.

## Condorcet Criterion Criticism
Proponents of IRV and RCV will be quick to tell you that the Condorcet criterion is not necessarily one that you want.  IRV and RCV, of course, do not satisfy the Condorcet criterion.  Their criticism is similar to the line of reasoning that lead to the problems we found with IIA.  With IIA we can remove candidates until we're down to a head-to-head matchup without changing the winner, but just asking questions about head-to-head matchups doesn't show the full picture.

RCV proponents argue that Condorcet methods produce middle of the road candidates who won't really make anyone happy, just satisfied.  We looked at a similar example in reverse when studying the plurality method.

|\# Voters | 41 | 40 | 10 | 9 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | C |
| 2nd | C | C | A | B |
| 3rd | B | A | B | A |

In the preference schedule above, candidates A and B are from the "major parties" while C is a more centrist third party.  Under plurality, tactical voting incentivizes third party supporters to make a compromising vote.  In a Condorcet method, the third party wins every time.  So you'll always have a candidate that 19% of the electorate actually like.  Remember, a ballot of A,C,B doesn't mean that the voter sort of likes C.  It could be that the ballot hates C but hates B even more.  It isn't hard for the Condorcet candidate to actually be somewhat unpopular.

The discussion of the IIA and Condorcet criteria highlights the importance of math and the interplay between the math and other disciplines.  The math cannot tell us with certainty what the right fairness criteria to adopt are.  Once there is a proposed set of fairness criteria, then we can use math to analyze what is forced by the choice of criteria.  Arrow's theorem is an extreme example which shows that some fairly innocuous sounding critera are actually mutually exclusive!  Any revisions to the fairness criteria would require new analysis.

## Assessing Fairness
At a glance, here is a table that shows fairness violations.

|       | Majority | Condorcet | Monotonicity | IIA |
| :---: | :---: | :---: | :---: | :---: |
| Plurality |  | X | | X |
| Borda count | X | X | | X |
| IRV/RCV |  | X | X | X |
| Copeland |  |  | | X |

An X in the cell indicates that a method violates the corresponding criterion.  We see that all of the methods violate the IIA criterion, most violate the Condorcet criterion, but violations of the monotonicity and majority criteria are rare.

It would be a mistake to conclude from the table that Copeland's method is the most fair since it only has one fairness violation.  Remember that there are [many possible](https://en.wikipedia.org/wiki/Voting_criteria) fairness criteria.  We have only picked these four because they are the ones used in Arrow's theorem.  These four are just a few out of many possible criteria, and it's not hard to find some that Copeland's method fails.  For example, Copeland's method fails a criterion called the **participation criterion** because choosing not to participate can actually be beneficial to one's preferred candidate.  Copeland's method also had issues with ties and would need to fall back on some other method anyway!  It also isn't the case that all fairness criteria have equal weight.  We've already argued that the IIA criterion is maybe not that important while the majority criterion seems vital at least in political elections.  Fairness criteria just provide standards we can use to analyze voting methods, an results like Arrow's say that using them to declare a best method is misguided.

What follows is a brief catalog of how each method either satisfies or fails each of the four major fairnes criteria.  In many cases, the details of examples have been worked out in previous sections.

## The Majority Criterion Summary
The majority criterion says that if a voting method is fair then it will always elect the majority candidate if there is one.  The majority candidate is one which has more than 50% of the first place votes.
* The plurality method satisfies the majority criterion.  Having a majority of first place votes also means that you have the most first place votes compared to anyone else.
* Instant Runoff Voting and Ranked Choice Voting satisfy the majority criterion the same way that plurality does.  The elimination aspect of these methods is not needed to declare a winner if there is a majority candidate.
* Copeland's method (and any Condorcet method) satisfy the majority criterion.  The majority candidate is automatically the Condorcet candidate.

### Borda Violation
We saw this example in the section on the [Borda count]({{basedir}}/vt3-borda.html).

|\# Voters | 51 | 49 |
| :---: | :---: | :---: |
| 1st | A | C |
| 2nd | B | B |
| 3rd | C | D |
| 4th | D | A |

Candidate B is the winner in the Borda count, but candidate A is the majority candidate, so this is a violation.

## The Condorcet Criterion Summary
The Condorcet criterion says if a voting method is fair then that it will always elect the Condorcet candidate should one exist.  The Condorcet criterion is stronger than the majority criterion.  The majority candidate is automatically the Condorcet candidate, so if a method fails the majority criterion then it automatically fails the Condorcet criterion as well.  In particular this means that the Borda count fails the Condorcet criterion.  Of the methods we studied, only Copeland's method satisfies the Condorcet criterion.

### Plurality and IRV Violation
We saw this example in the section on plurality.

|\# Voters | 10 | 7 | 6 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | C |
| 3rd | C | A | A |

B is the Condorcet candidate, but A wins under plurality.  With IRV, B is the first eliminated with only 6 first place votes, and then C wins.  So both methods violate the Condorcet criterion.

### The Monotonicity Criterion Summary
The monotonicity criterion says that if a voting method is fair then improving a candidate's ranking on some ballots (without changing the order of the other candidates) should not lower that candidate's ranking in the election.
* The plurality method satisfies the monotonicity criterion.  Improving a candidate's ranking on some ballots can only increase the number of first place votes and will not increase anyone else's first place vote count.  Therefore this in turn improves their ranking.
* The Borda count method satisfies the monotonicity criterion.  Improving a candidate's ranking on some ballots will only improve that candidate's Borda points.  No other candidate's points will increase from this change, so the improved candidate's final ranking can only increase.  The image below shows how improving C increases only C's points while either decreasing or not changing the other candidates.
<figure>
    <img src="{{imgdir}}/BordaMove.svg" alt="Borda points in a monotonic change."/>
    <figcaption> Increasing candidate C on a ballot improves C's points and does not improve any other candidate's points.
    </figcaption>
</figure>
* Copeland's method satisfies the monotonicity criterion.  Improving a candidate's ranking without changing the relative order of the other candidates will only improve that candidate's head-to-head matchups without changing any matchups which do not involve that candidate.  This can only improve that candidate's ranking in the election's outcome.

### Instant Runoff Voting Violation
We covered this example in the section on [Instant Runoff Voting]({{basedir}}/vt4-elimination.html).  Consider the following preference schedule.

|\# Voters | 9 | 8 | 7 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | C |
| 2nd | B | A | B | A |
| 3rd | C | C | A | B |

B is eliminated, and this causes A to win.  If the voters in the last column improve A's position we get this new preference schedule.

|\# Voters | 9 | 8 | 7 | **2** |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | **A** |
| 2nd | B | A | B | **C** |
| 3rd | C | C | A | **B** |

But this does not help A.  Now C is first to be eliminated and A wins.  This violates monotonicity.

## IIA Criterion Summary
The IIA Criterion says that if a voting method is fair then a candidate other than the winner dropping out should not change the winner.  This is a conceptual simplification of the IIA criterion you'll find in voting theory literature, but it works well enough for our purposes.  You can review the full explanation in the Borda count section.  Every method that we covered in this class fails the IIA criterion.

For most methods, we can easily find a violation by beginning with a Condorcet cycle (A beats B, B beats C, and C beats A).  Whoever wins the election we eliminate the candidate that the winner beats head-to-head.  The remaining candidate will now beat the old winner.

### Plurality and IRV Violation
In the following election, A wins according to plurality.

|\# Voters | 10 | 9 | 8 |
| :---: | :---: | :---: | :---: |
| 1st | A | B | C |
| 2nd | B | C | A |
| 3rd | C | A | B |

If B (an irrelevant alternative) were to dropout, then this would make C the winner.

## Borda Count Violation
This example is covered in detail in the section on the [Borda count]({{basedir}}/vt3-borda.html).

|\# Voters | 51 | 49 |
| :---: | :---: | :---: |
| 1st | A | C |
| 2nd | B | B |
| 3rd | C | D |
| 4th | D | A |

Candidate B is the winner by the Borda count.  Removing D (an irrelevant alternative) from the election and recalculating points will have A win.  

### Copeland's Method Violation
Copeland's method requires more care to find a violation, but we already did this work in the section on Condorcet methods.  Here is the preference schedule from that election.

|\# Voters | 11 | 9 | 7 | 6 | 3 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | B | A | D | C | D | 
| 2nd | A | C | B | A | C |
| 3rd | C | D | C | D | B |
| 4th | D | B | A | B | A |

You can check that A wins under Copeland's method.  If D drops out, then B wins.  The details are worked out fully in the [Condorcet method section]({{basedir}}/vt5-condorcet.html).

## Why Preference Voting?
We've spent so much time studying voting methods that rely on preference ballots not because it's the perfect best way to vote but because it's just about the simplest way to improve on the single choice ballots that are prevalent in the US.  It's not a big conceptual jump from "pick your favorite candidate" to "rank the candidates," but the small change leads to many interesting new phenomena to analyze.  It is also likely that preference ballots will become common within our lifetimes.  Preference ballots are already in use in local elections in [various parts of the US](https://en.wikipedia.org/wiki/Ranked-choice_voting_in_the_United_States), and their use is only growing more widespread.  It's likely that you'll have to interact with it regularly in your life, so it's essential to be able to think critically about them.

## Why Not Preference Voting?
It's clear that preference ballots are more expressive than single choice ballots.  While this does create some challenges with how to appropriately aggregate the results, it's worth it.  However, there are still some issues with how preference ballots express voter attitudes.  We saw one of these prominently when we discussed criticism of Condorcet methods, namely that two voters with very different preferences can have the same preference ballot.  The fact that a voter orders candidates A,B,C does not mean much about their absolute preferences.  The ballot A,B,C could mean loving A, hating C, and being indifferent about B or it could mean liking A and hating B just slightly less than C.  It even be that the voter is fairly positive about all three but has a slight preference for A over B over C.  You can come up with any number of scenarios that would all result in the same ballot being cast.

There's also a slight argument that the increased complexity of the ballot may discourage voters or increase misvoting.
<figure>
    <img src="{{imgdir}}/maine_irv_ballot.png" alt="Ranked Choice Voting ballot"/>
    <figcaption class="center"> A real preference ballot from Portland, Maine.</figcaption>
</figure>
You can see that the ballot is a little more imposing than a standard single choice ballot.  Of course, the only way to overcome this issue is through practice and education and that's why we're here!
