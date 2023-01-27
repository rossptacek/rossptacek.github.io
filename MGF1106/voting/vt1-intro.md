---
layout: page
usemathjax: true
title: "VT1: Introduction to Elections"
---

{% assign basedir = site.url| append: "/MGF1106/voting" %}
{% assign imgdir = basedir| append: "/images" %}

## What Is an Election
An **election** occurs any time a group needs to make a collective decision based upon its members' preferences.  Elections happen everywhere.  Of course, they happen when we go to the polls and vote for who will hold political offices, but they appear frequently in other contexts.  Any judged competition is a type of election, be it determining who wins the Cy Young award or who wins American Idol.  Competitions at the Olympics which are determined by a panel of judges such as figure skating, gymnastics, and diving count too.  The judges' preferences are used to determine the winner and perhaps a number of runner-ups.  Even more informally, any time you and your friends decide what restaurant to eat at or what movie to watch you are technically holding an election because you are making a collective decision.

You can see from the list of examples that our concept of voting is a little bit more broad than the ballots you may be used to casting.  In political contests, we just indicate who our top choice for the job is when we vote.  The judges in the olympics "vote" with their score cards.  When you and your friends decide on where to go eat you "vote" a little bit differently.  If you were choosing where to eat lunch around town with your friends you might say something like "I could really go for Bento right now, but Chipotle would be OK as a backup.  Let's just avoid Arby's.  It always gives me indigestion."  Roughly speaking, what you're doing is giving a ranking of your preferences.  You're saying Bento is your first choice, Chipotle is second, and Arby's is third/last.  Typically  Giving this ranking of the options is much more expressive than just giving your top choice.  if you and all of your friends give your rankings, then you all should find a place suitable for the whole group.  If all you did was specify your top choice, you'd probably never come to a mutually agreeable solution.

The general principle is that if we give more information then the group should be able to make decisions that better serve its members.  This is true for your friends getting lunch, and it's true for politics too.

## Ballots
The way that a voter indicates their choice is called a **ballot**.  **Single choice ballots** are what you are most familiar with.  In these ballots you simply list your top choice for the winner.  A **(full) preference ballot** has voters rank all of the candidates from first to last.  A **truncated preference ballot** has voters rank some but possibly not all of the candidates.  A single choice ballot can be thought of as a (very) truncated preference ballot.

<figure>
    <img src="{{imgdir}}/Ballots.svg" alt="Various Ballot Types"/>
    <figcaption> A single choice ballot (left), preference ballot (mid) and truncated preference ballot (right)</figcaption>
</figure>
The image above shows how a single choice (left), full preference (center), and truncated preferece (right) ballot might look for an election with the four candidates A,B,C, and D.  In the truncated ballot, the voter has chosen not to rank candidate C.

Truncated preference ballots are useful when there is a large field of candidates.  For example, a judge in a talent show may only list their top three choices out of a large pool of performers rather than rank the whole field.  Or when choosing a restaurant to eat at you need not rank every restaurant in the city.  Truncated ballots are useful when there are a large number of candidates.

<figure>
    <img src="{{imgdir}}/maine_irv_ballot.png" alt="Various Ballot Types"/>
    <figcaption> A real preference ballot from Portland, Maine.</figcaption>
</figure>
This mayoral election in Portland Maine had 15 candidates, and in such elections it is unlikely for voters to be familiar enough with all of them to give a full ranking.  The ballot above is a type of truncated ballot as you can see in the instructions that you "rank as many or as few candidates as you wish."

When we looked at the example of choosing where to go to eat, this was also a truncated ballot.  There are way more than three restaurants in town, but the ranking only specified three.  This example also hints at a potential pitfall with truncated ballots.  It's important to know how unlisted choices are treated.  The hypothetical person in the example wanted to avoid Arby's.  Should they list Arbys last among their preferences?  Or should they just leave Arby's off the ballot entirely?  Typically we take the point of view that only desirable choices are placed on the truncated ballot.  Unlisted  choices are usually treated as worse than any listed choice, as if they are all tied for last.  So Arby's should just be left off entirely if a voter wants to avoid it.


There are other types of ballots, but we will not really study them much.  Here are two examples.

* Approval ballots have voters select all candidates who they find acceptable.  There is no ranking among the acceptable candidates.  Approval ballots sit somewhere between single choice ballots and preference ballots for expressing voter preferences.
* Scored ballots have voters assign a score to each candidate.  The score can be a numerical ranking like 0 to 99.  The voter may also choose on a scale like "strongly disapprove" to "strongly approve," but these are usually translated to numerical values before evaluation.  Scored ballots are significantly more complicated to analyze than preference ballots.
<figure>
    <img src="{{imgdir}}/Other-Ballots-Labeled.svg" alt="Other Ballot Types"/>
    <figcaption> How approval or scored ballots might look.</figcaption>
</figure>

## Mathematically, What is an Election?
Whenever we study something mathematically, we must be very precise about the kind of thing we're studying.  If you look at all of the examples of elections previously given, they all have the following ingredients.

* **Voters.**  These people (or similar entities) are the ones who are making the decision.  You can assume that the voters are always people, but we'll see some interesting examples where they are not.
* **Candidates.**  These are the options which the voters must decide among.  As we saw in the previous examples, candidates definitely do not need to be people.
* **Ballot.**  This is the way in which the voters indicate their preferences for the candidate.  We discussed this previously.  In our course we will primarily consider full preference ballots but will occasionally look at truncated preference ballots.
* **Outcome.**  This is what kind of choice needs to be made.  We saw that some elections only require selection of a winner.  These are called winner-only outcomes.  The Olympics require only that the first, second, and third place are determined.  This is called a partial ranking outcome.  If all of the candidates are ranked from first all the way to last, then it is called a full ranking outcome.
* **Voting Method.**  This is the part that ties the rest together.  The voting method describes how the ballots which were cast by the voters produce the outcome.  The majority of this part of the course will be devoted to describing different voting methods.

Anything that can be described in terms of these five factors is mathematically considered to be an election.

### Example: Cy Young Award
In Major League Baseball (MLB), the Cy Young Award is given to the top pitchers.  A quirk of MLB is that there are two leagues which rarely play one another, so one award is given to the top pitcher in each league.  We'll focus on just a single league for now.  Every member of the Baseball Writers' Association of America is allowed to cast a ballot.  On the ballot they indicate their choices for the top five pitchers in each league (first, second, third, fourth, and fifth.)  The votes are tallied according to what is called a Borda count.  We'll devote an entire section to the Borda count, so we'll ignore the details for now.
* The **voters** are the members of the Baseball Writers' Association.
* The **candidates** are all of the pitchers in the MLB.
* The **ballot** is a truncated preference ballot.  Of all of the candidates, only the top five are placed on the ballot.
* The **outcome** is a little less straightforward.  The Cy Young voting procedure does produce a ranking of every candidate, but only the winner is required.  So the outcome is best described as winner-only.
* The **voting method** is something called a Borda count, but again this will wait for later for full details.

### Example: American Idol
American Idol is a long-running American television show where amateur singers compete with the eventual winner receiving a recording contract.  A main feature of this show is that the contestants are eliminated episode-by-episode according to the audience's vote.  The audience members indicate who their favorite singer is.  The contestant who receives the fewest votes on a given episode is eliminated.

* **Voters:** Just about anyone can vote on American Idol.  Multiple times even!
* **Candidates:**  The candidates are the amateur singers who compete on the show.
* **Ballot:** The ballot is a single-choice ballot.  Ballots are cast in each episode, and a voter may cast multiple ballots for a single episode.
* **Outcome:**  The show ends with a single winner, but it's easy to imagine that it produces a ranking of the candidates.  The first singer who is eliminated is in last place, the next singer who is eliminated is in second-to-last place, and so on until the last one standing is the winner.
* **Voting Method:**  There are a few interesting features of this.  As already mentioned, American Idol does not use the "one person one vote" standard that most elections follow.  The second is that voting proceeds by rounds.  Typically, elections with multiple rounds are called runoff elections.  We'll study voting methods called elimination methods which are similar to what is done for American Idol.

## Aggregating Ballots
First let's look at how single choice ballots are aggregated.  Let's say for example that the following 19 ballots were cast.
<img src="{{imgdir}}/Single-Choice-Ballot-Many.svg" alt="Many Preference Ballots"/>
The key observation is that many of the ballots are identical.  In fact, there are only four possible ballots that can be cast (vote for A, B, C or D), so there must be duplicates.  Then all that we need to report is how many of each type of ballot there is.

<img src="{{imgdir}}/Single-Choice-Ballot-Many-Agg.svg" alt="Many Preference Ballots Aggregated"/>

This can be summarized in the following table.

|Candidate | Votes |
| :---: | :---: |
| A | 4 |
| B | 6 |
| C | 5 |
| D | 4 |

## Preference Schedules
We'll go through the same procedure with preference ballots.  Our discussion will be for full preference ballots, but the abstraction to truncated preference ballots is straightforward.  A preference ballot for four candidates (A, B, C, and D) may look like the following.

<img src="{{imgdir}}/Full-Ballot-Versions.svg" alt="Two forms of preference ballots"/>

In the above picture, the red text indicates what was filled in by the voter.  In future figures we won't use the red text, but for now note that there is a slight difference.  The ballot on the left has empty boxes for each rank, and the voter must fill in the candidate's name in the appropriate box.  This is how we'll typically write ballots because we want to quickly see who is in which position.  The ballot on the right is called the printed names ballot for obvious reasons.  This is a more likely setting on a real ballot.  The list of candidates is printed on the ballot and the voter must select a rank for each candidate.  Again, it's harder at a glance to see who is first or last on a printed names ballot so we'll typically use the version on the left.

Let's take a sample of 19 preference ballots.

<img src="{{imgdir}}/PreferenceSchedule-New.svg" alt="19 Preference Ballots"/>

Just like before, we can recognize that some of these ballots (for example the first two) are identical.  It turns out we're a little lucky here because there are 24 possible ways to fill out a ballot so there was a chance that all 19 of these were different.  How we determined this number is left to the end of the section.

<img src="{{imgdir}}/PreferenceSchedule-New-Agg.svg" alt="19 Preference Ballots Aggregated"/>

And here we see the aggregated ballots.  Once again, these can be put into a tabular form.  This tabular form is called a **preference schedule**.

|\# Voters | 10 | 5 | 2 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | B | D |
| 2nd | B | B | D | C |
| 3rd | C | D | C | B |
| 4th | D | A | A | A |

Just like a single preference ballot can be put in printed names format, a preference schedule can also be in printed names format as shown below.

|\# Voters | 10 | 5 | 2 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| A |  1st | 4th | 4th | 4th |
| B | 2nd | 2nd |  1st | 3rd |
| C | 3rd |  1st | 3rd | 2nd |
| D | 4th | 3rd | 2nd |  1st |

The same information is present in each table, but we will prefer the first version, not the printed names version, for this class.  

### Example: Reading Information From Preference Schedules
We'll use the preference schedule from above: 

|\# Voters | 10 | 5 | 2 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | C | B | D |
| 2nd | B | B | D | C |
| 3rd | C | D | C | B |
| 4th | D | A | A | A |

* We can count the number of ballots cast by summing up the numbers in the first row.  We know from the example before that 19 ballots were cast in this election, and indeed we can recover this by computing $$10+5+2+2=19$$.
* We can count the number of second place ballots that candidate B has by looking in the "2nd" row and adding the vote count of the columns which have B present.  In this example, that would be the first and second columns with $$10+5=15$$ total second place votes.

## Pairwise Comparisons
An important bit of information we can compute from a preference schedule is a **pairwise comparison** or **head-to-head matchup**.  In a pairwise comparison we imagine what would happen if two of the candidates faced off, ignoring the rest.  Because the preference schedules hold complete preference information, we can play "what if" and block out the other candidates.

Let's compare candidates A and B in the following election.

|\# Voters | 10 | 6 | 4 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | C | D |
| 2nd | B | D | D | B |
| 3rd | C | C | B | C |
| 4th | D | A | A | A |

If we want to just compare A and B, we can pretend the other candidates do not exist (strike them out).

|\# Voters | 10 | 6 | 4 | 2 |
| :---: | :---: | :---: | :---: | :---: |
| 1st | A | B | ~~C~~ | ~~D~~ |
| 2nd | B | ~~D~~ | ~~D~~ | B |
| 3rd | ~~C~~ | ~~C~~ | B | ~~C~~ |
| 4th | ~~D~~ | A | A | A |
| **Winner** | **A** | **B** | **B** | **B** |

We see that A wins in the first column (10 votes) while B wins in the other three columns ($$6+4+2=12$$ votes). So B is the winner of the head-to-head matchup.  This type of comparison will be vital for a type of voting method called an elimination method.

## Fairness in Elections

Fairness In Elections
Overwhelmingly, people are interested in whether an election is fair.  Just like we had to come up with a precise definition of an election, we need to come up with a precise definition of fairness in order to determine whether an election is fair.  It's important to say that we also can only study sources of fairness intrinsic to the voting method itself.  There are plenty of ways that a voting system can fail to be fair due to how it is implemented that we won't consider.  Here are some examples of the type of thing we will not be treating:

* Underfunded, and hence understaffed, polling places have long lines which discourages voting in some districts.
* Voters do not accurately update their residence so that they can vote in a swing state (say Florida) instead of a less contested state (say New York.)
* A voter may try to register in multiple districts with the intention of voting multiple times in the same election.

These are examples of what is called voter fraud.  They are problems with the implementation of the voting system or problems with voters abiding by the rules of the election.  They are not intrinsic flaws with a given voting system.  The kind of flaws we want to study are ones where the ballots seem to suggest an "obvious" result but the voting system produces a strange outcome.  Another example would be if voting has seemingly illogical effects.  For example, it would be a significant problem if the best way to support your first place candidate would be to vote for a different candidate

Coming up with a precise definition of this kind of fairness turns out to be too hard.  There are too many different ways that an election could be unfair to list them all.  Instead, our approach will be to look at what are called fairness criteria.  Perhaps it would be better to call them unfairness criteria because each fairness criterion lists a way that an election can fail to be fair.  If a voting system fails a fairness criterion, then we deem it unfair.  A voting system would have to pass every possible fairness criterion in order to be fair, but it needs only to fail one to be considered unfair.  For concreteness we'll look at one such criterion now called the majority criterion.

### Majority Criterion

The majority criterion says that if a **majority** (more than 50%) of the voters have the same first place candidate, then that candidate should win the election.  So if it is possible for a voting system to fail to elect a majority winner, then the voting system is unfair.  Again, this is a way of detecting unfairness, not determining fairness.  It is very possible that a voting system which passes the test of the majority criterion can fail to be fair in some other way, but the moment a voting system fails the majority criterion, we can call it unfair.

Here's an example of a silly voting system that fails the majority criterion.  Suppose that our voting system says to elect the candidate with the fewest last place votes.  Consider the following election.

|\# Voters | 10 | 5 | 2 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | B | A |
| 3rd | C | A | C |

* There are $$10+5+2=17$$ total voters.  Half of the voters would be $$\frac{17}{2} = 8.5$$.  Since a majority needs more than half of the voters, a majority winner must get 9 or more first place votes.
* Candidate A has 10 first place votes, and so is a majority candidate.
* However, this voting method says to elect the candidate with the fewest last place votes.  In this case, that would be candidate B with 0 last place votes.
* Since this voting method failed to elect the majority candidate, it does **not** satisfy the majority criterion.

Candidate A (and the supporters of candidate A) would rightfully feel that the election was unfair.  As we proceed through the class, we will consider other fairness criteria and discuss which methods fail to satisfy them.

One important note about the majority criterion which will also apply to every other fairness criterion we study is that while a single example of an election is enough to determine that a voting method fails to satisfy a fairness criterion, one would have to look at _every_ possible election to determine that the method does satisfy the criterion.  As a concrete example, we can concoct elections where the "fewest last place" method will elect a majority candidate.

|\# Voters | 10 | 5 | 2 |
| :---: | :---: | :---: | :---: |
| 1st | A | C | B |
| 2nd | B | **A** | A |
| 3rd | C | **B** | C |

In the above election, we just flipped the rank of A and B in the second column (bolded).  Now A wins the election because they have the fewest last place votes (0).  This is **not** evidence that the method satisfies the criterion because we have an example of another election where it fails!

## Learning Objectives
* Identify the elements of an election (voters, candidates, ballot, outcome, method)
* Construct preference schedules from ballot data
* Compute information from preference schedules (number of votes, pairwise comparison)
* Identify when a voting system fails to meet the majority criterion

[Next: VT2 - Plurality Method]({{basedir}}/vt2-plurality.html)
