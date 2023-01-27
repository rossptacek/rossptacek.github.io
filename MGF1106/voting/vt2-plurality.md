---
layout: page
usemathjax: true
title: "VT2: The Plurality Method"
---

{% assign basedir = site.url| append: "/MGF1106/voting" %}
{% assign imgdir = basedir| append: "/images" %}

Our first voting method is the one that looks the most like the voting you're used to.  The winner of an election under the plurality method is the candidate who obtains the **most first place votes**.  If a ranking is desired as an outcome rather than just a winner, then the candidates are ranked according to how many first place votes they get.  Sometimes you'll see this voting method called **first past the post** voting.

### Example
Here's an election with three candidates.

|\# Voters | 10 | 7 | 6 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | C |
| 3rd | C | A | A |

It is easy to compute the ranking because we only have to look at the first row of the table.
* Candidate A finishes in 1st place with 10 first place votes,
* Candidate C finishes in 2nd place with 7 first place, and
* Candidate B finishes in 3rd place with 6 first place votes.

The ranking could also be written more compactly as A, C, B (or A > B > C).

## Plurality vs. Majority
Students often get confused at the difference between _plurality_ and _majority_.

* Plurality means that the candidate has more votes than any other candidate, but
* Majority means that the candidate has more than half of the votes.

We can see from the above example that the winner according to the plurality method need not have a majority of the votes.  There are $$10+7+6=23$$ votes, so a majority would need to exceed $$\frac{23}{2} = 11.5$$ votes.  So a majority candidate needs 12 or more votes.  Here, the winner (A) has only 10 votes, not a majority.

However, it is the case that a majority candidate will win the plurality method.  Certainly, if one has a majority of the votes then they must have more than anyone else, more than everyone else combined even!  In other words, the plurality method satisfies the majority criterion. So while a candidate with a majority will win under the plurality method, it is not the case that the winner of the plurality method will have a majority of the votes.


## The Majority Loser Criterion
For readability, we'll repeat the preference schedule used in the previous example here.

|\# Voters | 10 | 7 | 6 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | C |
| 3rd | C | A | A |

Recall that there are 23 ballots so 12 or more make a majority.  We have already discussed how the winner (A) does not have a majority of first place votes.  Even worse, A has a majority of the last place votes!  A majority of the voters believe that A is the worst possible candidate yet A will win the election.  A candidate with a majority of last place votes is sometimes called the **majority loser**.  Many would say that's not fair and indeed the **majority loser criterion** says that a fair election should never be won by a majority loser.  As the above example shows, **plurality voting does not satisfy the majority loser criterion**.

## The Condorcet Criterion
The name Condorcet comes from [an 18th century French mathematician](https://en.wikipedia.org/wiki/Marquis_de_Condorcet) who studied these issues.  Condorcet studied elections in terms of their pairwise comparisons.  In general, analyzing an election in terms of its pairwise comparisons is tricky, but there is exactly one case where it's easy!  If you have a candidate who can defeat every other candidate one-on-one, then they should be the winner according to Concordet.  This candidate is called the Condorcet candidate.  If, you ask the electorate whether they prefer any of the alternatives to the Condorcet candidate, the answer collective will be no.  So it seems like the Condorcet candidate is a reasonable winner.  Let's return to a previous example to study this.

|\# Voters | 10 | 7 | 6 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | C |
| 3rd | C | A | A |

* B defeats A 13 to 10 (B wins in the second and third columns),
* B defeats C 16 to 7 (B wins in the first and third columns)

So B is the Condorcet Candidate, and it seems like B is a good pick to win the election.  Would you prefer candidate A?  No!  A majority prefers B over A.  Would you prefer candidate C?  No!  A majority prefers B over C.  So it would seem only fair for the Condorcet candidate to be the winner.

Indeed, this is the **Condorcet criterion**.  It says that **any fair voting method will elect the Condorcet candidate** when one exists.  Equivalently, a voting method is unfair if it can fail to elect the Condorcet candidate.  We can immediately conclude that the plurality method is unfair according to the Condorcet criterion.  Remember, the plurality method has A winning the above election, not B!

### Condorcet's Paradox

There does not need to be a Condorcet Candidate.  It is possible for the pairwise comparisons to work out like a game of Rock Paper Scissors where each candidate can defeat one of the others and also be defeated by one of the others.

|\# Voters | 1 | 1 | 1 |
| :---: | :---: | :---: | :---: |
| 1st | A | B | C |
| 2nd | B | C | A |
| 3rd | C | A | B |

In the simple election above we see how this might happen.  A beats B (2 to 1) and B beats C (2 to 1).  It's tempting to think that winning a pairwise comparison makes that candidate better than their opponent.  So A would be better than B and B would be better than C.  If that were the case, we would be confident to say that A is better than C.  If preferences were **transitive** we could make this assertion, but if you look at the preference schedule you can clearly see that C is actually preferred to A (2 to 1).  So the preferences are **nontransitive**.  When preferences are nontransitive, there is a cycle of candidates who beat eachother like in Rock Paper Scissors.  

<figure>
    <img src="{{imgdir}}/Condorcet-Cycle.png" alt="Various Ballot Types"/>
    <figcaption> A beats B, B beats C, and C beats A.</figcaption>
</figure>

Here A beats B, B beats C, and C beats A just like Rock beats Scissors, Scissors beats Paper, and Paper beats rock.

## Plurality Method and Tactical Voting
Tactical voting (or insincere voting) is when a voter does not honestly list their preferences on their ballot in order to obtain a better outcome in the election.  Their sincere preferences do not best serve their desired outcome.  Tactical voting is undesirable and somewhat defeats the purpose of an election.  The [Gibbard-Satterthwaite theorem](https://en.wikipedia.org/wiki/Gibbard%E2%80%93Satterthwaite_theorem) essentially says that every voting system is susceptible to tactical voting, but we'll see that plurality method is disastrously simple to game.

Let's consider a _completely hypothetical_ situation where two candidates, say A and B, come from the two major parties and candidate C comes from a third party.  The two major parties dislike one another more than the third party candidate.  Those who prefer the third party candidate are roughly evenly split between having candidate A and candidate B as a second choice.  A preference schedule for this may look like the following.  In fact, an opinion poll prior to the election may publish results similar to the following.

|\# Voters | 41 | 40 | 10 | 9 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | C |
| 2nd | C | C | A | B |
| 3rd | B | A | B | A |

You can see that this election has 100 voters, but it's safe to imagine that this preference schedule is measuring percentages of voters.  It's OK to list a preference schedule in terms of percentages, because we can always turn it back into raw vote numbers if needed.

In the above situation, a slight plurality of voters favor candidate A.
* Candidate A has 41% of the first place votes,
* Candidate B has 40% of the first place votes, and
* Candidate C has 10+9=19% of the first place votes.

Seeing this poll may have the B-leaning C supporters (the last column) consider tactically voting.  They can see from the poll that C is highly unlikely to win, and A winning is their least desired outcome.  They would improve the outcome for themselves by casting a ballot of BCA instead of CBA as below.  This type of tactical voting, where a less desirable candidate is tactically elevated on the ballot is called **compromising**.  We can see what this tactical choice would do below.

|\# Voters | 41 | 40 | 10 | **9** |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | **B** |
| 2nd | C | C | A | **C** |
| 3rd | B | A | B | **A** |

At this point we could combine the second and fourth columns, but we're leaving them separate to show how the fourth column is voting insincerely.  But their efforts will pay off!  Now the results are
* Candidate A has 41% of the first place votes,
* Candidate B has 40+9=49% of the first place votes, and
* Candidate C has 10% of the first place votes.
B is the new winner by the plurality method!  But it doesn't stop there.  Oh no, it's only just beginning.  Because  now the A-leaning C supporters (third column) have their worst-case scenario, and they may be enticed to tactically change their votes to ACB to avoid it.  If this happens, the final vote will show no C supporters!

|\# Voters | 41 | 40 | **10** | **9** |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | **A** | **B** |
| 2nd | C | C | **C** | **C** |
| 3rd | B | A | **B** | **A** |

The tendency for third parties to get squeezed out for this and other reasons is called [Duverger's law](https://en.wikipedia.org/wiki/Duverger%27s_law).  It is not absolute, and if you read the linked article you can find a few examples of plurality-based systems that have not degenerated into two party systems.  Not all voters are willing to vote tactically after all.  Tactical voting assumes that the voters are only motivated by what the outcome of the election will be.  Some voters will have a strong party affiliation or personal commitment to honest voting and will not fill out their ballot insincerely.  A disturbing facet of this example is that the election will be entirely determined by how many C supporters defect and support one of the main party candidates.

## Learning Objectives
* Compute the ranking of candidates according to the plurality method.
* Explain which fairness criteria are satisfied and not satisfied by the plurality method.
  * The plurality method satisfies the majority criterion.
  * The plurality method does not satisfy the majority lose criterion.
  * The plurality method does not satisfy the Condorcet criterion.
* Determine how voters may vote tactically (compromise) under the plurality method. 

[Next: VT3 - Borda Count Method]({{basedir}}/vt3-borda.html)
