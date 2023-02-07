---
layout: page
usemathjax: true
title: "WVS2: Banzhaf Power"
---

{% assign basedir = site.url| append: "/MGF1106/weightedvoting" %}
{% assign imgdir = basedir| append: "/images" %}


Informally, **power** in a WVS measures how easily a player can get their preference adopted.  Consider the WVS \[6: 4, 3, 2, 2\].
* $$P_1$$ can pass a motion with the support of any other player.
* The other players require either convincing $$P_1$$ or convincing *all* of the non-$$P_1$$ players.

This indicates (informally) that $$P_1$$ is more powerful than the other players.  It also strongly suggests that the other players are equally powerful since they have exactly the same burden to pass a motion.  It's worth repeating that even though $$P_2$$ has more weight than $$P_3$ and $$P_4$$, it appears that all three of them have the same power.

## Power and Coalitions
From the above discussion, we are starting to get the idea that a player's power should be measured by how that player can join with the other players to pass a motion.  A **coalition** is a nonempty subset of the set of players.  We imagine that a coalition has formed to all vote for a motion to pass.  If the coalition has enough combined weight for to pass a motion, the coalition is said to be a **winning coalition**.  The coalition consisting of all players is called the **grand coalition**.  When we write coalitions, we use set notation.  To review, with set notation we write the objects between curly braces.  Here are some coalitions from the previous section's examples.

* In \[51 : 49, 49, 2\] the coalitions $$\{P_1,P_2\}, \{P_1,P_3\}, \{P_2,P_3\},$$ and $$\{P_1,P_2,P_3\}$$ are winning coalitions.  The other coalitions $$\{P_1\}, \{P_2\},$$ and $$\{P_3\}$$ are not winning.
* In \[21 : 11, 10, 9\] the coalitions $$\{P_1,P_2,P_3\}$$ and $$\{P_1,P_2\}$$ are winning and the rest are not.
* In any system the grand coalition will be winning.  This is because we have stipulated that the quota cannot exceed the total weight of the system.

### Examples
For the following we'll use the system \[10 : 5, 4, 3, 1\].
* $$\{P_1, P_2, P_3\}$$ is a winning coalition.  It has a total weight of $$5+4+3=12$$, which meets (and exceeds) the quota.
* $$\{P_1, P_2, P_4\}$$ is a winning coalition.  It has a total weight of $$5+4+1=10$$ which is exactly the quota.  Remember, it is sufficient to meet the quota.  Exceeding the quota is not required.
* $$\{P_2, P_3, P_4\}$$ is **not** a winning coalition (is a **losing coalition**.)  Its total weight is $$4+3+1=8$$ which falls short of the quota.
  * This is an alternate way to think about **veto power**.  A player has veto power if the other players combined to not make a winning coalition.

## Power Distributions
Before proceeding, we need to figure out how power will be measured.  So far we've been able to vaguely refer to one player having more or less power than another, but we'd like to be more precise.  As we've seen before, the players' weights **do not** make for a good measurement.  It is possible for players with different weights to have the same power, and it is possible for players with very similar weights to have greatly differing power.  Recall that in \[21:11,10,9\] that the player with 9 weight had no power at all.

Our point of view will be to envision each 
