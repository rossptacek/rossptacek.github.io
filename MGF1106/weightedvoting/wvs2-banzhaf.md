---
layout: page
usemathjax: true
title: "WVS2: Banzhaf Power"
---

{% assign basedir = site.url| append: "/MGF1106/weightedvoting" %}
{% assign imgdir = basedir| append: "/images" %}


# Banzhaf Power
[John Banzhaf](https://en.wikipedia.org/wiki/John_Banzhaf) is an engineer-turned-lawyer who invented Banzhaf power to win a court case.  Banzhaf power determines power based on how easily a player can join with other players to pass a motion.  

## Banzhaf's Original Problem
Banzhaf argued that Nassau County (NY) Board's voting system was unfair.  The setup is this scenario is that each municipality of Nassau County is awarded some number of votes proportionally to its population.  Then, a majority of votes is required to make a decision.  This is identical to how the US Electoral College operates but at a much smaller scale. Here's how the votes were distributed at the time of the case.

| **Municipality** | **\# Votes** |
| :---:        | :---:    |
| Hempstead \#1 | 31 |
| Hempstead \#2 | 31 |
| Oyster Bay | 28 |
| North Hempstead | 21 |
| Long Beach | 2 |
| Glen Cove | 2 |

We see there are $$31+31+28+21+2+2 = 115$$ total votes.  So a simple majority requires $$58$$ or more votes.  Banzhaf argued that the three smaller municipalities essentially had no power despite totalling about a sixth of the total population of the county.  Here's how he argued.  First, the three smaller municipalities have a combined weight of $$25$$.  In order to pass a motion, they still need $$33$$ more votes.  This requires convincing two of the larger municipalities to join with them.  But two of the larger municipalities have enough votes to pass a motion without any help!  So the three smaller municipalities had essentially no power at all in the situation.  

This should be shocking because 21 votes for North Hempstead isn't *that* much smaller than the 28 of Oyster bay, but it's the difference between some power and no power at all.  It bears repeating that there was nothing nefarious about the vote distribution.  It is just that the relationship between number of votes (weight) and actual power in a weighted voting system is difficult to determine.  This is why we're studying these things!  In order to identify, and hopefully fix, systems that do not serve their supposed purpose we need an informed population.

## Power and Coalitions
To summarize tha above discussion, Banzhaf's notion of power (called Banzhaf power from here on) measured by a player can join with other players to pass a motion.  A **coalition** is a nonempty subset of the set of players.  We imagine that a coalition has formed to all vote for a motion to pass.  If the coalition has enough combined weight for to pass a motion, the coalition is said to be a **winning coalition**.  The coalition consisting of all players is called the **grand coalition**.  In any reasonable system the grand coalition will be winning because we have stipulated that the quota cannot exceed the total weight of the system.  When we write coalitions, we use set notation.  To review, with set notation we write the objects in the set between curly braces.  Here are some coalitions from the previous section's examples.

### Examples of Winning Coalitions
For the following we'll use the system \[10 : 5, 4, 3, 1\].
* $$\{P_1, P_2, P_3\}$$ is a winning coalition.  It has a total weight of $$5+4+3=12$$, which meets (and exceeds) the quota.
* $$\{P_1, P_2, P_4\}$$ is a winning coalition.  It has a total weight of $$5+4+1=10$$ which is exactly the quota.  Remember, it is sufficient to meet the quota.  Exceeding the quota is not required.
* $$\{P_2, P_3, P_4\}$$ is **not** a winning coalition (is a **losing coalition**).  Its total weight is $$4+3+1=8$$ which falls short of the quota.

### Examples
First, here are some examples from the previous section in the language of coalitions.
* \[51 : 49, 49, 2\] was an example of a deeply divided US Senate.  The first two players represent the major parties while the third represents independents.  The coalitions $$\{P_1,P_2\}, \{P_1,P_3\}, \{P_2,P_3\},$$ and $$\{P_1,P_2,P_3\}$$ are winning coalitions.  The other coalitions $$\{P_1\}, \{P_2\},$$ and $$\{P_3\}$$ are not winning.
  * Note that this is a full listing of all winning coalitions.  All three players are involved in winning coalitions in the same way:  Each must convince at least one other player to join in order to win.  We intuit that this will result in the same power for all players,
* In \[21 : 11, 10, 9\] the coalitions $$\{P_1,P_2,P_3\}$$ and $$\{P_1,P_2\}$$ are winning and the rest are not.
  * $$P_3$$ functions similarly to the three small municipalities from Banzhaf's example.  $$P_3$$ is only a part of one winning coalition, but the coalition will still win without $$P_3$$.
  
### Apriori Power Determination
This is a technical note, but it is vitally important.  When we make a power determination we are doing so without assuming anything at all about the players' preferences.  In reality, when doing a detailed analysis of the UN Security council we would need to include data such as "The US is more likely to form a coalition with the UK and France than it is with either China or Russia."  However, our analysis is of the system, not of the particular players who use the system.  Analyses such as these are called apriori analyses.

## Critical Players
At the heart of Banzhaf power is the idea of **critical players**.  The three smaller municipalities were part of winning coalitions, but those coalitions could still win without them so their inclusion was meaningless.  A player is **critical in a winning coalition** if their removal causes the coalition to no longer win.  We denote critical players by underlining them in a coalition.  For example $$\newcommand{\ul}{\underline} \{\ul{P_1}, P_2, P_4\}$$ is saying that (1) the coalition $$\{P_1, P_2, P_4\}$$ is winning and that $$P_1$$ is its only critical player.


### Critical Player Examples
* In the system \[10: 7, 6, 5, 2\] the coalition $$\{P_1, P_2, P_3\}$$ is a winning coalition.  It has weight 7+6+2=15 which meets (exceeds even) the quota of 10.  Since it exceeds the quota by 5 votes, the coalition can afford to lose any player with 5 or fewer votes.  This means that $$P_3$$ with a weight of 2 is not critical.  However, $$P_1$$ and $$P_2$$ are critical.  The coalition would no longer win if one of them were to leave.  As a shorthand, we underline the critical players so we write $$\{\underline{P_1}, \underline{P_2}, P_3\}$$.
* In the system \[20: 9,8,7,6\] the grand coalition $$\{P_1,P_2, P_3, P_4\}$$ is winning with a weight of 30.  This means that it can lose 10 weight and still win.  Since all players have less than 10 weight, none of them is critical.

### Dictators and Dummies
Note that a dictator (if one exists) will be the only player to possibly be critical in any winning coalition in the system.  When a dictator exists in a WVS, their presence is the only thing that determines whether a coalition wins or loses. So
1. The dictator will be present in every winning coalition,
2. Removal of any non-dictator from a winning coalition will not change the fact that it's a winning coalition because the dictator is still present (**nobody else can be critical**), and
3. Removal of the dictator from the winning coalition will make the coalition no longer win (**the dictator is critical**)

On the other end of the power spectrum, a **dummy** is a player whose presence of absence has no bearing on whether a coalition wins or not.  In the language of Banzhaf power, this means that the player is never critical.  We've seen examples of dummies prior to this but have not used this name
* In \[22: 11, 10, 9\] we saw that $$\{P_1, P_2, P_3\}$$ is the *only* winning coalition that $$P_3$$ is a part of.  However, the removal of $$P_3$$ yields $$\{P_1, P_2\}$$ which still wins!  
* Any player with 0 weight is a dummy.  As the above example shows, not every dummy has 0 weight.

## Banzhaf Power
The fundamental idea of Banzhaf power is that players which are critical are the ones which have power.  The more ways that you can be critical, the more power you have.  More precisely, we will look at all possible winning coalitions and mark all crtical players in each.  From this, we will count the total number of critical players across all coalitions and mark each player's power as their proportion of the critical count that corresponds to that player.  In more detail:

1. **Make a list of all winning coalitions.**
2. **Mark (underline) the critical players in each winning coalition.**
3. **Count the total number of underlines and the number of times each player is underlined (critical counts).**  The total number of underlines is denoted as $$C_T$$ and is called the total crtical count.  The number of times each player is underlined, called that player's critical count, is denoted as $$C_i$$ for player $$P_i$$.
4. **Each player's power is their proportion of the total critical count.**  The power of $$P_i$$ is computed as $$\displaystyle B_i=\frac{C_i}{C_T}$$.

Note that we have successfully defined a  power distribution!
1. **Each power is a non-negative number.**  Each power is a fraction of non-negative numbers, and $$C_T \ne 0$$.  It's a little tricky to verify that $$C_T$$ is not zero to make sure that the division is valid, but this will be the case.  If no player were ever critical, we'd be forced to accept a coalition with no players as winning and this would cause anarchy.
2. **The powers sum up to 1**.  This should be clear because the powers are all proportions of $$C_T$$.  Putting it into algebra we have:

$$\begin{align*}
 B_1+B_2+\cdots+B_n & =\frac{C_1}{C_T}+\frac{C_2}{C_T}+\cdots+\frac{C_N}{C_T} && \text{(Definition of $B_i$)} \\
 &=\frac{C_1+C_2+\cdots C_N}{C_T} && \text{(Fractions with same denominator)} \\
 &= \frac{C_T}{C_T} = 1 && \text{(Definition of $C_T$)}
\end{align*}$$

As we work examples with Banzhaf power, we are going to go slowly. Steps 1 and 2 (finding winning coalitions and marking critical players) can be very tedious and error-prone depending on how you go about it.  A nice procedure will be provided, but first we'll look at some examples where some or all of these steps have been done for us.

### Example with Critical Players Marked
Suppose that we are already given a list of winning coalitions with the critical players marked.  In the numbered steps above, this means that steps 1 and 2 have already been accomplished.
$$\begin{align*}
&\lbrace P_1, P_2, P_3, P_4\rbrace &\, &\lbrace \ul{P_1}, P_2, P_3\rbrace &\, &\lbrace \ul{P_1}, P_2, P_4\rbrace &\, &\lbrace \ul{P_1}, P_3, P_4\rbrace \\
&\lbrace \ul{P_2}, \ul{P_3}, \ul{P_4}\rbrace &\,  &\lbrace \ul{P_1}, \ul{P_2}\rbrace &\, &\lbrace \ul{P_1}, \ul{P_3}\rbrace &\, &\lbrace \ul{P_1}, \ul{P_4}\rbrace \\
\end{align*}$$

**3. Count the total number of underlines and the number of times each player is underlined (critical counts).**  

We see that
* $$P_1$$ is underlined 6 times ($$C_1 = 6$$)
* $$P_2$$ is underlined 2 times ($$C_2 = 2$$)
* $$P_3$$ is underlined 2 times ($$C_3 = 2$$)
* $$P_4$$ is underlined 2 times ($$C_4 = 2$$)

Now we add up each player's critcal count to find the total critical count.

$$C_T = C_1+C_2+C_3+C_4 = 6+2+2+2 = 12.$$

**Each player’s power is their proportion of the total critical count.**
* For $$P_1$$ we have $$\displaystyle B_1 = \frac{C_1}{C_T} = \frac{6}{12} = \frac12$$.
* For $$P_2$$ we have $$\displaystyle B_2 = \frac{C_2}{C_T} = \frac{2}{12} = \frac16$$.
* For $$P_3$$ we have $$\displaystyle B_3 = \frac{C_3}{C_T} = \frac{2}{12} = \frac16$$.
* For $$P_4$$ we have $$\displaystyle B_4 = \frac{C_4}{C_T} = \frac{2}{12} = \frac16$$.

When writing the power distribution, it is often better to leave fractions unreduced.  This way it is easier to compare powers at a glance.  With this point of view, the power distribution is

$$ \left(\frac{6}{12}, \frac{2}{12}, \frac{2}{12}, \frac{2}{12} \right). $$

### Full Example
Now we'll look at the same example but we'll start with the usual WVS notation.  It turns out that a representation for the system we just studied is \[6: 4,3,2,2\].  We'll see later in this course that with four players there are fifteen possible coalitions.  However, only about half of these turn out to be winning coalitions.  So instead of listing out all possible coalitions and checking each one, we will start with the grand coalition (known to be winning) and work our way down.

| Coalition | Weight ($$w$$) | Weight to lose ($$w-q$$) |
| :---: | :---: | :---: |
| $$\{P_1,P_2,P_3,P_4\}$$| 11 | 5 |

In the table above, we will track
1. Each winning coalition
2. The total weight of that coalition ($$w$$), and
3. The amount of weight that coalition can lose and still be a winning coalition ($$w-q$$).

The key observation is that any player whose weight is less than or equal to $$w-q$$ is **not crtitical**.  In the table above, we see that the grand coalition can lose 5 weight and still be winning.  Since no player's weight exceeds 5, no player is critical.  This means that removal of any player makes a new winning coalition.
* Removal of $$P_4$$ produces $$\{P_1, P_2, P_3\}$$
* Removal of $$P_3$$ produces $$\{P_1, P_2, P_4\}$$
* Removal of $$P_2$$ produces $$\{P_1, P_3, P_4\}$$
* Removal of $$P_1$$ produces $$\{P_2, P_3, P_4\}$$

We can add these new winning coalitions to the table.  Note that the $$w$$ and $$w-q$$ columns **go down by the removed player's weight**.

| Coalition | Weight ($$w$$) | Weight to lose ($$w-q$$) |
| :---: | :---: | :---: |
| $$\{P_1,P_2,P_3,P_4\}$$| 11 | 5 |
| $$\{\ul{P_1}, P_2, P_3\}$$ (remove $$P_4$$) | 11-2=9 | 5-2=3 |
| $$\{\ul{P_1}, P_2, P_4\}$$ (remove $$P_3$$) | 11-2=9 | 5-2=3 |
| $$\{\ul{P_1}, P_3, P_4\}$$ (remove $$P_2$$) | 11-3=8 | 5-3=2 |
| $$\{\ul{P_2}, \ul{P_3}, \ul{P_4}\}$$ (remove $$P_1$$) | 11-4=7 | 5-4=1 |

For each newly-added row, we can also compute critical players (already shown above).
* $$\{\ul{P_1}, P_2, P_3\}$$ can lose 3 weight, which means only $$P_1$$ with 4 weight is critical.
* $$\{\ul{P_1}, P_2, P_4\}$$ can lose 3 weight, which means only $$P_1$$ with 4 weight is critical.
* $$\{\ul{P_1}, P_3, P_4\}$$ can lose 2 weight, which means only $$P_1$$ with 4 weight is critical.
* $$\{\ul{P_2}, \ul{P_3}, \ul{P_4}\}$$ can lose 1 weight.  The players all have 2 or more weight, so they all are critical.

Now we repeat this process with each of the added rows.
* $$\{\ul{P_1}, P_2, P_3\}$$ produces $$\{P_1, P_2\}$$ and $$\{P_1, P_3\}$$ by removing the non-critical players $$P_2$$ and $$P_3$$ respectively.
* $$\{\ul{P_1}, P_2, P_4\}$$ produces $$\{P_1, P_2\}$$ and $$\{P_1, P_4\}$$ by removing the non-critical players $$P_2$$ and $$P_4$$ respectively.
  * Note that this duplicates $$\{P_1, P_2\}$$.  Make sure to only count each coalition once!
* $$\{\ul{P_1}, P_3, P_4\}$$ produces $$\{P_1, P_3\}$$ and $$\{P_1, P_4\}$$ by removing the non-critical players $$P_2$$ and $$P_3$$ respectively.
  * Note that both of these are duplicates of previously found winning coalitions.
* $$\{\ul{P_2}, \ul{P_3}, \ul{P_4}\}$$ has no non-critical players and so nothing further can be removed.  No new winning coalitions are produced.

The table now looks as follows

| Coalition | Weight ($$w$$) | Weight to lose ($$w-q$$) |
| :---: | :---: | :---: |
| $$\{P_1,P_2,P_3,P_4\}$$| 11 | 5 |
| $$\{\ul{P_1}, P_2, P_3\}$$ | 9 | 3 |
| $$\{\ul{P_1}, P_2, P_4\}$$ | 9 | 3 |
| $$\{\ul{P_1}, P_3, P_4\}$$ | 8 | 2 |
| $$\{\ul{P_2}, \ul{P_3}, \ul{P_4}\}$$ | 7 | 1 |
| $$\{\ul{P_1}, \ul{P_2}\}$$ | 7 | 1 |
| $$\{\ul{P_1}, \ul{P_3}\}$$ | 6 | 0 |
| $$\{\ul{P_1}, \ul{P_4}\}$$ | 6 | 0 |

We see that all newly added coalitions have all players critical.  So there are no more removals to do and our table is done.  This gives the same list of winning coalitions and critical players as before.  Following the work from the previous example, we get the same power distribution of $$ \left(\frac{6}{12}, \frac{2}{12}, \frac{2}{12}, \frac{2}{12} \right). $$

### Example with Just Winning Coalitions
There are some examples of weighted voting systems where weights are not given explicitly.  Most systems which have a form of veto power fall into this category.  Consider, for example, the UN Security Council in which all members have one vote but the five permanent members have veto power.  It is not obvious how to turn that into the usual notation, but we can still determine whether coalitions are winning from the rules of the system.

So here is the list of winning coalitions from before, this time without the critical players underlined.  We'll see that we can recover the critical players with no additional information.

$$\begin{align*}
&\lbrace P_1, P_2, P_3, P_4\rbrace &\, &\lbrace P_1, P_2, P_3\rbrace &\, &\lbrace P_1, P_2, P_4\rbrace &\, &\lbrace P_1, P_3, P_4\rbrace \\
&\lbrace P_2, P_3, P_4\rbrace &\,  &\lbrace P_1, P_2\rbrace &\, &\lbrace P_1, P_3\rbrace &\, &\lbrace P_1, P_4\rbrace \\
\end{align*}$$

The idea is to remove a player one at a time from each coalition.  If the remaining coalition is still in the list of winning coalitions, then the removed player is not critical.  Otherwise, the removed player is critical.
* \\(\lbrace P_1, P_2, P_3, P_4\rbrace\\)
  * Removing $$P_4$$ gives $$\lbrace P_1, P_2, P_3\rbrace $$ (in the list, not critical)
  * Removing $$P_3$$ gives $$\lbrace P_1, P_2, P_4\rbrace $$ (in the list, not critical)
  * Removing $$P_2$$ gives $$\lbrace P_1, P_3, P_4\rbrace $$ (in the list, not critical)
  * Removing $$P_1$$ gives $$\lbrace P_2, P_3, P_4\rbrace $$ (in the list, not critical)
* \\(\lbrace \ul{P_1}, P_2, P_3 \rbrace\\)
  * Removing $$P_3$$ gives $$\lbrace P_1, P_2\rbrace $$ (in the list, not critical)
  * Removing $$P_2$$ gives $$\lbrace P_1, P_3\rbrace $$ (in the list, not critical)
  * Removing $$P_1$$ gives $$\lbrace P_2, P_3\rbrace $$ (**not** in the list, **critical**)

This procedure can be repeated for all winning coalitions, but we'll cut the computation off here.

## Learning Objectives
* Determine whether a coalition in a WVS is winning or not.
* Determine which players are critical in a winning coalition.
* Find all winning coalitions in a WVS.
* Determine the Banzhaf power distribution for a WVS
  * Usually when explicitly weights are given, but
  * Also when only the winning coalitions can be determined.
