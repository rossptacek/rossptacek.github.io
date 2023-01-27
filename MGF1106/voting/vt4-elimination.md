---
layout: page
usemathjax: true
title: "VT4 - Elimination Methods"
---

{% assign basedir = site.url| append: "/MGF1106/voting" %}
{% assign imgdir = basedir| append: "/images" %}

## Runoffs and Candidate Elimination
Voting in the US is close to the plurality method.  However, most US elections have a majority requirement.  With few exceptions the final winner needs to have a majority of the first place votes.  Recall that in the US we only indicate our first place choice on the ballot.   The most notorious exception is the presidential election.  Because votes are processed through the electoral college, which awards votes on a state-by-state basis in a convoluted way, it is [possible to win the presidential election with a mere 23.1% of the popular vote](https://www.npr.org/2016/11/02/500112248/how-to-win-the-presidency-with-27-percent-of-the-popular-vote).  In most cases, such as state or local elections, a majority would be required.  If no candidate achieved a majority, then a runoff election would be held between the top few (almost always two) candidates.

Nobody really wants a runoff to be held.  It's costly to have to open the polls a second time, and it's typical for voter turnout to decrease in a runoff.  Having a runoff may also increases the tendency for voters to vote tactically.  Imagine a situation where party support is 40%,40%,20% for three parties.  Nobody will win a majority, and a runoff is a certainty if everyone votes honestly.  A voter might as well just cast a vote for one of the major parties, and perhaps their choice will win without a runoff.  

Many of these problems can be solved simply by using preference ballots because preference ballots allow us to hold a runoff without making everyone vote again!

<figure>
    <img src="{{imgdir}}/Elimination.svg" alt="Eliminating a candidate from a ballot."/>
    <figcaption> B is eliminated from the above ballot.</figcaption>
</figure>

If we intend to remove a candidate from an election (as we would in a runoff) we can just remove the choice from each ballot.  In our initial discussion of the independence of irrelevant alternatives criterion we've already looked at how elimination can easily be simulated in a preference schedule.  A pairwise comparison (head-to-head match up) is an extreme form of elimination where all but two candidates are eliminated.

## Elimination Methods
There are a variety of voting methods that continuously remove the "worst" candidate until only one remains.  The ranking of the election is in reverse elimination order.  First to be eliminated finishes in last place and so on until the last candidate standing is the winner.  There are a wide variety of conditions that you can use to eliminate candidates.  Here are two somewhat straightforward ideas.
* Repeatedly eliminate the candidate with the fewest first place votes, and 
* Repeatedly eliminate the candidate with the most last place votes.
In the context of seeking a majority, the first option above is attractive because at a certain point the winner will have a majority of first place votes among not-yet-eliminated candidates.  In fact, elimination using fewest first place votes as the elimination criterion goes by many names such as Ranked Choice Voting (RCV), Instant Runoff Voting (IRV) and Plurality-with-Elimination.  These methods may differ slightly.  For example, RCV usually allows voters to rank as many or as few candidates as they would like (truncated preference ballot) while IRV usually requires a full preference ballot.

## Instant Runoff Voting (IRV)
As we said just previously, Instant Runoff Voting is an elimination method which uses a full preference ballot.  The candidate with the fewest first place votes is eliminated.  This process is repeated until only one candidate is left.  The ranking for the election is in reverse elimination order.  If the desired outcome of the election is not a full ranking but just a winner, then the elimination can stop when a candidate has a majority of the first place votes.  Let's look at an example election.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | B | C | 
| 2nd | B | B | C | D | D |
| 3rd | C | D | B | A | B |
| 4th | D | A | A | C | A |

In this election A has 20 first place votes, B has 4, C has 11, and D has 8.  B has the fewest first place votes, so candidate B will be the first eliminated candidate and will finish in last place.  Now you can write a whole new preference schedule without B.  If you did that you would have the following.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | D | C | 
| 2nd | C | D | C | A | D |
| 3rd | D | A | A | C | A |


Note that the second and last columns are identical.  You could merge these if you wanted.  However, it is not practical to rewrite the entire preference schedule after each elimination.  Instead, we will just strike through the eliminated candidate.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | ~~B~~ | C | 
| 2nd | ~~B~~ | ~~B~~ | C | D | D |
| 3rd | C | D | ~~B~~ | A | ~~B~~ |
| 4th | D | A | A | C | A |

One thing to keep in mind is that the labels "1st," "2nd," and so on **are not accurate anymore**.  In the fourth column, the one with four ballots, the first place vote is not the eliminated candidate B.  Instead, we have to look down to the first non-eliminated candidate, which is D.  Since D receives the four votes from B, the new counts are A with 20 first place votes, C has 11, and D has 12.  Since C has the fewest, they will be eliminated next.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | ~~C~~ | D | ~~B~~ | ~~C~~ | 
| 2nd | ~~B~~ | ~~B~~ | ~~C~~ | D | D |
| 3rd | ~~C~~ | D | ~~B~~ | A | ~~B~~ |
| 4th | D | A | A | ~~C~~ | A |

Candidate C was in first place in the second and last columns.  It just so happens that D is next in line in both of these columns, so D will receive all of C's 11 first place votes.  Now the counts are A with 20 and D with 23.  At this point D has a majority of the 43 possible ballots, so we can stop if we just want the winner.  There's only one candidate left to eliminate anyway.  The final ranking is D,A,C,B.

## Top Two IRV
Top Two IRV performs elimination like IRV except that all but the top two first place vote getters are eliminated.  This will not always turn out the same as normal IRV! Let's return to our previous example.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | B | C | 
| 2nd | B | B | C | D | D |
| 3rd | C | D | B | A | B |
| 4th | D | A | A | C | A |

When we solved this with normal IRV, D won the election.  Now, we see that A and C are the top candidates with 20 and 11 votes respectively.  So candidates B and D (the old winner) are eliminated.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | ~~D~~ | ~~B~~ | C | 
| 2nd | ~~B~~ | ~~B~~ | C | ~~D~~ | ~~D~~ |
| 3rd | C | ~~D~~ | ~~B~~ | A | ~~B~~ |
| 4th | ~~D~~ | A | A | C | A |

Now A has a majority with 24 of the possible 43 votes.  Top Two IRV is relatively uncommon compared to the other methods, so we will not spend much time on it.

## Ranked Choice Voting (RCV)
You can do elimination methods like IRV with truncated preference ballots.  One version of this is called Ranked Choice Voting or RCV for short.  RCV allows voters to rank as many or as few candidates as they would like.  This is advantageous because many voters may not know enough about some of the candidates to effectively rank them.

<figure>
    <img src="{{imgdir}}/maine_irv_ballot.png" alt="Various Ballot Types"/>
    <figcaption class="center"> A real preference ballot from Portland, Maine.</figcaption>
</figure>

The ballot above is a truncated preference ballot used in RCV.  As you can see in the instructions, the voter should "rank as many or as few candidates as you wish."  The downside to this is that some ballots may not end up contributing to the final tally.  If all of the candidates on a ballot are eliminated, that ballot is said to be exhausted.  It is removed from the election.  Importantly, this changes the needed threshold for majority.  Here's an example similar to the previous one.

|\# Voters | 20 | 10 | 6 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | B | C | 
| 2nd | C | B | C | D | D |
| 3rd |   | D | B |   | B |
| 4th |   |   | A |   | A |

You can see that we are using truncated preference ballots because not all ballots are fully filled out.  This is ok!  As in the previous example, B is eliminated first with only 4 votes.

|\# Voters | 20 | 10 | 6 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | ~~B~~ | C | 
| 2nd | C | ~~B~~ | C | D | D |
| 3rd |   | D | ~~B~~ |   | ~~B~~ |
| 4th |   |   | A |   | A |

The 4 first place votes that B had pass to D, but this doesn't stop D from being eliminated.  It now has the fewest first place votes with only 10 while C has 11 and A has 20.

|\# Voters | 20 | 10 | 6 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | ~~D~~ | ~~B~~ | C | 
| 2nd | C | ~~B~~ | C | ~~D~~ | ~~D~~ |
| 3rd |   | ~~D~~ | ~~B~~ |   | ~~B~~ |
| 4th |   |   | A |   | A |

And now something new has happened.  The ballots in the fourth column are exhausted and are thrown out.  Previously, there were 41 votes total, but with those four being removed, there are only 37.  With 20 first place votes, A has a majority and wins!

This may seem like a bad thing since the four voters seem like their votes weren't counted, but it is more akin to those voters abstaining from a runoff between A and C since they had no preference between the two of them.  If they favored one over the other, they would have put it on their ballot!  It's important to keep in mind that this is the heart of elimination methods.  We're simulating runoff elections after determining that candidates are not suitable.

## Majority and Majority Loser Criteria
It should be clear from the description of IRV (and RCV) that a candidate with the majority of first place votes will win.  Indeed, if all that is desired is a winner, then the process terminates once a candidate has a majority of the first place votes.  It is impossible for a majority candidate to ever be eliminated since a majority candidate by definition has more first place votes than anyone else.

It is a little harder to see, but IRV also satisfies the majority loser criterion.  RCV doesn't make much sense in this context because different ballots may have ranked a different number of candidates.  In IRV however if a candidate has a majority of the last place votes, then that that candidate will never inherit the first place votes on that ballot unless all other candidates were eliminated.  However, that won't happen.  Let's say candidate X is the majority loser.  If candidate X were to win the election, then they would not ever be eliminated.  But let's imagine the last elimination, where it's just candidate X and one remaining opponent, say candidate Y.  Since candidate X is last on a majority of ballots, it must be that candidate Y is now first on those ballots.  So then Y would have a majority and win, not X.

So IRV passes the tests of both Majority and Majority Loser Criteria.

## Condorcet Criterion
Unfortunately, IRV (and RCV) fail the Condorcet criterion.

|\# Voters | 10 | 7 | 6 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | C |
| 3rd | C | A | A |

In the above example, candidate B is the Condorcet candidate.  We covered this in the section on the [plurality method]({{basedir}}/vt2-plurality.html), so you can review it there.  However, candidate B is the first to become eliminated since they have the fewest number of first place votes.

## Tactical Voting Analysis
IRV and RCV are less susceptible to the tactical voting issues as the plurality method from which they are derived.  For example a compromising vote makes much less sense for IRV compared to plurality.

|\# Voters | 41 | 40 | 10 | 9 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | C |
| 2nd | C | C | A | B |
| 3rd | B | A | B | A |


Recall the example we gave for plurality method where the C party supporters are incentivized to compromise by pushing their second choice to the top.  For IRV, this would make no sense at all.  Yes, the C candidate has no chance of winning, but there's no reason to compromise because once C is eliminated the C supporters will have their vote transferred to their second place choice automatically.

That said, there are some sort of convoluted situations where tactical voting could pay off.  However, we'll see that these scenarios are pretty impractical.  Let's return to the example that we first considered for IRV.

|\# Voters | 20 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | D | B | C | 
| 2nd | B | B | C | D | D |
| 3rd | C | D | B | A | B |
| 4th | D | A | A | C | A |

Remember that D ends up winning this election.  Recall that what happened is that after B's elimination, C was eliminated by a very narrow margin, 11 to 12.  After that, D held a majority of first place votes.  For the 20 voters in the first column, this is the worst possible outcome, so they are highly motivated to vote tactically.  The obvious move is to move B to first place.  This would immediately give B a majority (24 of 43) of first place votes, and B winning would be much preferable to D winning for these voters.

Here's where it gets weird.  The A voters, with sufficient coordination, can actually do much better.  They can manage to get A elected!  Can you see the move?  It might be fun to pause here and see if you can figure out how the A voters can manage this feat.

The trick here is for _exactly two_ of the A supporters to change their ballot to C,A,B,D.  This may seem ridiculous since A would be giving up two first place votes this way.  But let's see what happens.

|\# Voters | 18 | 2 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | C | D | B | C | 
| 2nd | B | A | B | C | D | D |
| 3rd | C | B | D | B | A | B |
| 4th | D | D | A | A | C | A |

B will still be eliminated first with only four first place votes.

|\# Voters | 18 | 2 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | C | D |~~B~~| C | 
| 2nd |~~B~~| A |~~B~~| C | D | D |
| 3rd | C |~~B~~| D |~~B~~| A |~~B~~|
| 4th | D | D | A | A | C | A |

And now we see the convoluted way in which this would work.  Whereas before C would get eliminated, now C barely edges out D 13 to 12 and D is eliminated!

|\# Voters | 18 | 2 | 10 | 8 | 4 | 1 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | C | ~~D~~ |~~B~~| C | 
| 2nd |~~B~~| A |~~B~~| C | ~~D~~ | ~~D~~ |
| 3rd | C |~~B~~| ~~D~~ |~~B~~| A |~~B~~|
| 4th | ~~D~~ | ~~D~~ | A | A | C | A |

With D eliminated, A gets access to four more 1st place votes and has a majority, 22 of the 43 votes.

In summary, compromising is still effective with IRV but it is not quite as large of an issue as it is with plain old plurality.  Recall that by the [Gibbard-Satterthwaite theorem](https://en.wikipedia.org/wiki/Gibbard%E2%80%93Satterthwaite_theorem), all methods are vulnerable to some tactical voting.  It takes a pretty complete knowledge of the whole preference schedule to understand the cascading effects on elimination.  And as we're about to see a compromising vote can actually have the opposite effect!

## Monotonicity Criterion
The somewhat overly complicated tactical voting example shows very odd behavior.  Two voters decreased A's ranking without making any other changes, but the result increased A's final ranking!  This is somewhat counter-intuitive.  It would also be strange if increasing a candidate's rank on some ballots without changing the relative ranking of the other candidates would decrease that candidate's final ranking.  These are both examples of violating the monotonicity criterion.

For consistency with other textbooks we'll define monotonicity only in terms of positive effects.  So for us, the monotonicity criterion means that if a voting method is fair then a change on some ballots to improve a candidate's rank (without making changes to the relative ranks of other candidates) should never decrease that candidate's final rank.  Let's take just a moment to make sure we understand what "without making changes to the relative ranks of the other candidates" means.

<figure>
    <img src="{{imgdir}}/ValidMove-Horiz.svg" alt="A monotonic change in a ballot."/>
    <figcaption> A monotonic change to a ballot just shifts one candidate up or down.  No other modifications are made.</figcaption>
</figure>

It's important that the change only shifts the target candidate up without making any other changes to the order.  The change on the left is fine because it just moves C from 4th to second.  If C were removed from the "before" and "after" ballots, they would both read D,B,A.  On the right, B and A are flipped in addition to moving C up, and this is a problem.  If C were removed from the "before" and "after" ballots, the order would be D,B,A before and D,A,B after.  If we make changes like this, we have no idea what the effect on the overall election should be, but if changes are like the one on the left, we would assume that C's position could only improve in the overall election.

Let's work through an example.  Remember that to analyze monotonicity we have to have an original election, make a valid change as above, and then analyze the new election.  So let's look at the following original election.

## Example of Monotonicity Violation

|\# Voters | 9 | 8 | 7 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | C |
| 2nd | B | A | B | A |
| 3rd | C | C | A | B |

In this election, B will be the first elimination candidate.  After B's 8 votes are transferred to A, A will win the election.  Now we'll make a monotonic change to the preference schedule.  The two CAB voters will change their ranking to ABC as shown below.

|\# Voters | 9 | 8 | 7 | **2** |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | **A** |
| 2nd | B | A | B | **C** |
| 3rd | C | C | A | **B** |

Now C will be the first elimination candidate with only 7 votes.  These votes will all go to B.  The result is that B will win with 15 votes!  Paradoxically, the improvement to A lead to a worse result.

## Learning Objectives
* Compute the ranking of candidates according to elimination methods (emphasis on IRV).
* Explain which fairness criteria are satisfied and not satisfied by elimination methods.
  * Elimination methods do satisfy the majority criterion.
  * Elimination methods do satisfy the majority loser criterion.
  * Elimination methods do not satisfy the Condorcet criterion.
  * Elimination methods do not satisfy the Monotonicity criterion.
* Understand how tactical voting can impact elimination methods (but it is quite difficult). 

[Next: VT5 - Condorcet Methods]({{basedir}}/vt5-condorcet.html)
