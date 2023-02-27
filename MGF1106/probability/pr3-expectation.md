---
layout: page
title: "PR3: Expectation"
---

{% assign basedir = site.url| append: "/MGF1106/probability" %}
{% assign imgdir = basedir| append: "/images" %}

# Expectation

Expectation (or expected value) is the mathematical name for the the average result of a random process.  In order for this to make sense we need either a way to assign a numerical value to each outcome.  Sometimes the outcomes are already numerical (for example the faces of a standard die) and no additional assignment is needed.  Just as with probability itself, our point of view if you were to repeat the random process many times, and take the average of all results, then the expected value is what you ought to end up with.

Take for example the situation of flipping an unfair coin which will come up heads 70% of the time and tails the remaining 30% of the time.  The outcomes (H and T) are not numbers, so it makes no sense to talk about the value of a single coin flip.  We'll have to add some more information.  Let's say that we'll value a H at 1 and a T at 2.  The units of 1 and 2 are not important, but you can imagine that we are playing some strange game and they are dollars.  If we flipped the coin 100 times, we would expect 50 H and 50 T.
* The 70 H's each give a value of 1 for a total value of 70&times;1=70.
* The 30 T's each give a value of 1 for a total value of 30&times;2=60.
* So the total value is (70&times;1) + (30&times;2) = 130.
* The average value is the total value divided by the number of trials or 130/100=1.3.

Let's look at the computation another way.  To find the average value we compute<br><br>
$$\begin{align*}
\text{Average} &= \frac{\text{Total}}{\text{Number of Trials}}
= \frac{(70\times 1) + (30\times 2)}{100} \\[1em]
&= \frac{(70\times 1)}{100} + \frac{(30\times 2)}{100} = \left({\color{red}\frac{70}{100}}\times 1\right) + \left({\color{red}\frac{30}{100}}\times 2\right)\\\\
\end{align*}$$

We've manipulated this in a particular way to illustrate what's going on.  The red numbers are the proportions of outcomes, in other words the probabilities, and the black numbers are the values of the outcomes.  We'll introduce the notation of $V(E)$ to stand for the value of an event.  Just with probability, we'll happily plug outcomes into $V$ and understand that we're talking about simple events.  With this notation, the average value becomes.

$$\text{Average} = \left({\color{red}P(H)}\times V(H)\right) + \left({\color{red}P(T)}\times V(T)\right)$$

We see this happen regardless of the random experiment chosen.  As we simulate some number of trials, the average value is the sum of probabilities times values.

<div class="definition" text="Expectation">
Suppose a random process $X$ has outcomes $o_1, o_2, \dots, o_m$ and that each outcome, $o_i$ has a value given by $V(o_i)$.  The the expectation (or expected value) of the random process is given by

$$ E(X) = P(o_1)\cdot V(o_1) + P(o_2)\cdot V(o_2)+\cdots+P(o_m)\cdot V(o_m).$$

Often times, we will not name the process and will just write $E$ instead of $E(X)$.
</div>

<details class="example" markdown="1">
<summary>Fair Four-Sided Die</summary>
We'll find the expectation of a fair standard four-sided die.  First, we write down all of the outcomes and values.  For the die, the faces already have values (i.e. $V(3) = 3$).  So we can immediately apply the formula.

$$\begin{align*}
E &= P(1)\cdot V(1)+P(2)\cdot V(2)+P(3)\cdot V(3)+P(4)\cdot V(4) \\[0.5em]
&= \frac14\cdot1 + \frac14\cdot2 + \frac14\cdot3 + \frac14\cdot4 \\[0.5em]
	&= \frac14\cdot(1+2+3+4) = \frac14\cdot 10 \\[0.5em]
&= \frac{10}{4} = 2.5
\end{align*}$$

Note that the actual value of 2.5 is impossible for the die to achieve.  The expectation is the average result of the die.
</details>

### Combining Outcomes

As the number of outcomes grows, this procedure becomes unwieldy.  If we were to roll two four-sided dice, there would be 16 outcomes to multiply.  It can simplify by grouping out the outcomes with the same value.  Let's say that a process has exactly three outcomes ($o_1$, $o_2$, and $o_3$) which have a value of 2.  We could call $E_2$ the event where the value is exactly 2, and it will consist of exactly those outcomes.  As we did the expectation calcluation we would compute (among other things)

$$\begin{align*}
E &= \cdots + P(o_1)\cdot 2 + P(o_2)\cdot 2 + P(o_3)\cdot 2 + \cdots \\
  &= \cdots + \left(P(o_1)+P(o_2)+P(o_3)\right)\cdot 2 + \cdots \\
  &= \cdots + \left(P(E_2)\cdot 2\right) + \cdots \\
\end{align*}$$

We could group up all outcomes by their events to simplify the computation.

<div class="theorem">
Suppose that a random process has outcomes which only take the values $v_1,\dots v_k$.  Denote by $E_k$ the event consisting of outcomes with exactly value $v_k$.  Then another formula for the expectation is.

$$E = P(E_1)\cdot v_1 + \cdots P(E_k)\cdot v_k$$
</div>

This theorem suggests the following procedure for solving expected value problems.
1. Enumerate all possible values,  (find $v_1, ..., v_k$)
2. Compute the probability that each value occurs (find $P(E_1),... P(E_k)$), and
3. Find the expectation by adding probabilities times values.

<details class="example" markdown="1">
<summary>Two Fair Dice</summary>
The sample space of two fair dice is given by.

|2<sup>nd</sup> Roll \ 1<sup>st</sup> Roll| 1 | 2 | 3 | 4 |
| :---: | :---: | :---: | :---: | :---: |
| 1 | $(1,1)$| $(2,1)$ | $(3,1)$ | $(4,1)$ |
| 2 | $(1,2)$| $(2,2)$ | $(3,2)$ | $(4,2)$ |
| 3 | $(1,3)$| $(2,3)$ | $(3,3)$ | $(4,3)$ |
| 4 | $(1,4)$| $(2,4)$ | $(3,4)$ | $(4,4)$ |

Let's say that a certain game has you use the **product** of the two die rolls as your score.  So $(2,3)$ would give a value of $6$ because $2\times3=6$.
We will compute the expectation using the rule just established.  Below we'll make a table with all possible values and the probability of that value occurring.

| value ($v$) | $E = \lbrace\text{ Outcomes with value of } v\rbrace$ | $P(E)$ |
| :---: | :---: | :---: |
| 1 | $\lbrace(1,1)\rbrace$ | $\frac{1}{16}$|
| 2 | $\lbrace(1,2), (2,1)\rbrace$ | $\frac{2}{16}$ |
| 3 | $\lbrace(1,3), (3,1)\rbrace$ | $\frac{2}{16}$
| 4 | $\lbrace(2,2), (1,4), (4,1) \rbrace$ | $\frac{3}{16}$ |
| 6 | $\lbrace(2,3), (3,2)\rbrace$ | $\frac{2}{16}$ |
| 8 | $\lbrace(2,4), (4,2)\rbrace$ | $\frac{2}{16}$ |
| 9 | $\lbrace(3,3)\rbrace$ | $\frac{1}{16}$ |
| 12 | $\lbrace(3,4), (4,3)\rbrace$ | $\frac{2}{16}$ |
| 16 | $\lbrace(4,4)\rbrace$ | $\frac{1}{16}$ |

<div class="note">
Since this is a uniform space, the probabilities are just the number of outcomes in the event divided by 16, the size of the sample space.
</div>

Then the expectation is given by probabilities times values.

$$\begin{align*}
E ={}& P(\text{value } = 1)\cdot 1 + \cdots + P(\text{value } = 16)\cdot 16 \\
={}& \frac1{16}\cdot 1 + \frac{2}{16}\cdot 2 + \frac{2}{16}\cdot 3 + \frac{3}{16}\cdot 4 + \frac{2}{16}\cdot 6 + \frac{2}{16}\cdot 8 + \\ &+\frac{1}{16}\cdot 9 + \frac{2}{16}\cdot 12 + \frac{1}{16}\cdot 16 \\
={}& \frac{1}{16}\left(1+4+6+12+12+16+9+24+16\right) \\[0.5em]
={}& \frac{100}{16} = 6.25
\end{align*}$$

</details>

While the above example is a nice illustration of the improved formula, you may be wondering whether there is a faster way.  We already computed previously that the expectation of a single four-sided die was 2.5.  It would make sense that if the first die is on average 2.5, and so is the second die, then their product should on average be $2.5\times 2.5 = 6.25$.  And indeed it is!  However, this relies on the fact that the two rolls are **independent**.  By independent we mean that the result of one has no bearing on the result of the other.

As we start combining random processes, it is convenient to adopt some simplifying notation.  For two processes $X$ and $Y$ we will use arithmetic operations to denote how we will combine the values of the processes.
* $X+Y$ denotes the process that performs $X$ and $Y$ and sums the results,
* $X\cdot Y$ denotes the process that performs $X$ and $Y$ and multiplies the results, and

<div class="theorem">
If $X$ and $Y$ are independent processes, then
<div markdown="1">
* $E(X+Y) = E(X)+E(Y)$.
* $E(X\cdot Y) = E(X)\cdot E(Y)$
</div>
</div>

<details class="example" markdown="1">
<summary> Expectation Using Independence </summary>
Let us call $X$ the process of rolling a four-sided die.
* The expectation of rolling two four-sided dice and adding their results is is $2.5 + 2.5=6.25$ and the expectation of rolling ten of them is $10\cdot 2.5 = 25$.
* If we roll a fair six-sided die and a fair four-sided die and add the results, we get an expectation of $\frac72+\frac52 = 6$
  * Check that the expectation of a standard six-sided die is $\frac72$
* If we roll a fair six-sided die and a fair four-sided die and multiply the results, we get an expectation of $\frac72\cdot\frac52 = \frac{35}{4}$

</details>


While many repeat processes will be independent, it won't always be so easy. Consider for instance a runner in the 100m dash.  Racing two back-to-back 100m races (a 200m race) will *not* have twice the time of a single 100m race.  The racer gets exhausted from the first and can not perform at their peak in the second.  More simple examples of non-independent processes come from decks of cards where dealing a card changes the makeup of the deck.

<details class="example" markdown="1">
<summary> Simple Deck of Cards</summary>
Suppose we have a very simple deck of cards with only four cards.  The cards have the numbers 1, 2, 3, and 4 on them.  If a card is dealt randomly from the deck, the expectation is.

$$E = \frac14\cdot 1 + \frac14\cdot2 + \frac14\cdot3 +\frac14\cdot 4 = 2.5.$$

Note that this is *exactly* the same as our four-sided die.  There are four equally likely outcomes with the values 1, 2, 3, and 4.  but now if we want to deal two cards from the deck, everything changes.  This will still have a uniform distributuion.  The multiplication rule says that since there are four options for the first card and three for the second that there are 3&times;4=12 outcomes in the sample space.  We can put them in a table.

|2<sup>nd</sup> Card \ 1<sup>st</sup> Card | 1 | 2 | 3 | 4 |
| :---: | :---: | :---: | :---: | :---: |
| 1 | **X** | $(2,1)$ | $(3,1)$ | $(4,1)$ |
| 2 | $(1,2)$| **X** | $(3,2)$ | $(4,2)$ |
| 3 | $(1,3)$| $(2,3)$ | **X** | $(4,3)$ |
| 4 | $(1,4)$| $(2,4)$ | $(3,4)$ | **X** |

Unlike the two die situation, it is impossible to get the same number twice because once a card has been dealt it can not be dealt again.  To mimic the two die example, we will again take the product of the cards dealt as the outcome's value.  The table of outcomes and values is below.

| value ($v$) | $E = \lbrace\text{ Outcomes with value of } v\rbrace$ | $P(E)$ |
| :---: | :---: | :---: |
| 2 | $\lbrace(1,2), (2,1)\rbrace$ | $\frac{2}{12}$ |
| 3 | $\lbrace(1,3), (3,1)\rbrace$ | $\frac{2}{12}$ |
| 4 | $\lbrace(1,4), (4,1)\rbrace$ | $\frac{2}{12}$ |
| 6 | $\lbrace(2,3), (3,2)\rbrace$ | $\frac{2}{12}$ |
| 8 | $\lbrace(2,4)  (4,2)\rbrace$ | $\frac{2}{12}$ |
| 12 | $\lbrace(3,4), (4,3)\rbrace$ | $\frac{2}{12}$ |

Then the expectation is given by probabilities times values as usual.

$$\begin{align*}
E ={}& P(\text{value } = 2)\cdot 2 + \cdots + P(\text{value } = 12)\cdot 7 \\
={}& \frac2{12}\cdot 2 + \frac{2}{12}\cdot 3 + \frac{2}{12}\cdot 4 + \frac{2}{12}\cdot 6 + \frac{2}{12}\cdot 8 + \frac{2}{12}\cdot 12 \\
={}& \frac{2}{12}\left(2+3+4+6+8+12\right) \\[0.5em]
={}& \frac{2}{12}\cdot 35 = \frac{35}{6} = 5.8\overline{3}
\end{align*}$$

</details>


### Weighted Averages

Another way to think of expectation is as a **weighted average**.  Almost every student is familiar with weighted averages from grade school.  A typical course grading scheme would be to assign 10% of the final grade from homework, 30% of the final grade from quizzes, and 60% of the final grade from exams.  Then the student's final grade would be found by

$$ {\color{red} 0.1}\cdot(\text{HW Average})  + {\color{red} 0.3}\cdot(\text{Quiz Average}) + {\color{red}0.6}\cdot(\text{Exam Average}).$$

The numbers in red are called *weights*.  They determine how much each value contributes to the average.  In a normal (non-weighted) average, each value contributes equally, so the weights would be $1/N$ if there are $N$ values to average. Expectation is exactly a weighted average where the weights are probabilities.  This relationship is brought up only to help get a feeling for what the expectation is accomplishing.

## Games of Chance

Games of chance all fit the same general pattern.  Some fee is paid in order to play the game, some random process occurs, and then the player is paid out according to the result of the random process.  Some specific examples include
* **Lotteries.**  Players pay some amount for a lottery ticket.  On the ticket, they try to predict which numbers will be chosen.  When the numbers are chosen, the ticket pays out depending on how close it was to being correct.  There is a grand prize for getting all of the numbers correct but also many smaller prizes for matching some but not all of the numbers.
* **Roulette.**  A roulette wheel is a disk with various numbered and colored spaces on it.  A round of play consists of a small ball being dropped on the table as the table spins.  The ball will fall on a randomly chosen space.  When paying to play, players can place a variety of different types of bets.  They may bet on the exact number, the color, or a variety of other events.  The payout depends on the type of bet made.
<figure>
<img src="{{imgdir}}/roulette.jpg" alt="A typical roulette table." class="center">
<figcaption>A typical roulette table.  Each space on the wheel has both a color and a number.</figcaption>
</figure>
* **Craps.**  Craps is similar to roulette in that players are allowed to make various types of bets.  Indeed the betting rules for craps are quite complicated.  Instead of the roulette wheel determining the out, a pair of (presumably) fair six-sided dice are rolled.
* **Warranties and Insurance Policies.**  Even though these are not strictly considered games, they follow the same pattern.  You pay for the policy, and then the passage of time is the random process.  If your product suffers damage over the warranty period, then you don't have to pay for the repair!

<details class="example" markdown="1">
<summary>Roulette Number Bet</summary>
A standard roulette wheel has 37 numbered spots on it
* The numbers 1 through 36 are colored in red and black.  The precise description of which are red and black is not important, but there are 18 red and 18 black numbers.
* The number 0 is marked green.

We'll look at the expected value of a bet on a particular number.  This kind o bet pays "35 to 1".  This phrasing means that you will get 35 times your bet back as *profit* (net value).  Equivalently, you are paid 36 times your bet (gross value), but since you already paid your bet, you only walk away with 35 times your bet in profit.

To make this precise, let's say a player put a \\$10 bet on a number.  The casino takes the \\$10 at that moment, so the player is out \\$10 at the point that the game begins.  If the player wins the bet, the casino will pay the player \\$36&times;10=\\$360.  Subtracting the \\$10 the player started with, this is \\$360-\\$10 = \\$350 of profit.

When computing expected values, we can either take the cost into account when we determine the value of each result, or we can take the cost into account at the end.  Both methods are equivalent.

| Result | Probability | Value (Net) |
| :---: | :---: | :---: |
| Win | $\frac{1}{37}$ | \\$35 |
| Lose | $\frac{36}{37}$ | -\\$1 |

It bears repeating: The Value column here is the *net* value to the player.  The value column is taking into account the fixe \\$1 cost to play.  We see then that the expection is

$$\begin{align*}
E &= P(\text{Win})\cdot V(\text{Win}) + P(\text{Lose})\cdot V(\text{Lose}) \\
	&= \frac{1}{37}\cdot(\$35) + \frac{36}{37}\cdot (-\$1) \\[0.5em]
&= \frac{\$35-\$36}{37} = -\frac{\$1}{37} \approx -\$0.027 
\end{align*}$$

So the expectation indicates that with each spin of the roulette wheel a player should expect to lose about three cents.  Another strategy which will get us the same answer but is sometimes easier to compute is to compute the *gross* value (the value without including cost to play) and then subtracting the cost to play at the end.

| Result | Probability | Value (Gross) |
| :---: | :---: | :---: |
| Win | $\frac{1}{37}$ | \\$36 |
| Lose | $\frac{36}{37}$ | 0 |

$$\begin{align*}
E &= P(\text{Win})\cdot V(\text{Win}) + P(\text{Lose})\cdot V(\text{Lose}) \\
	&= \frac{1}{37}\cdot(\$36) + \frac{36}{37}\cdot (0) \approx \$0.973 \\[0.5em] 
\end{align*}$$

Now we subtract the fixed-cost \\$1 bet to get a value of \\($0.973-1 = \$0.027\\), the same as before.  The benefit is that we get to use a value of 0 for a loss, which zeroes out half of the calculation.  Both methods are equivalent.
</details>

Note that when computing the expectation, it is important to think about whose perspective you are doing the computation from.  In the above example, we did the computation from the point of view of a player and found an expected value of -\\$0.027.  From the point of view of the casino (the house) the expected value is a positive \\$0.027 because all of the values would flip sign.

<details class="example" markdown="1">
<summary>Roulette Color Bet</summary>
Next we'll look at a $1 bet placed on a red or black.  Now there are 18 squares on which we the bet will pay out.  The casino pays "even money" or "1 to 1" on such bets.  This means that a successful \\$1 bet will result in \\$1 of profit.  Equivalently, the gross payoff is \\$2.  We'll use the gross value version of the table.

| Result | Probability | Value (Gross) |
| :---: | :---: | :---: |
| Win | $\frac{18}{37}$ | \\$2 |
| Lose | $\frac{19}{37}$ | 0 |

$$\begin{align*}
E &= P(\text{Win})\cdot V(\text{Win}) + P(\text{Lose})\cdot V(\text{Lose}) \\
&= \frac{18}{37}\cdot(\$2) + \frac{19}{37}\cdot (0) \approx \$0.973 \\[0.5em] 
\end{align*}$$

Just as before, subtracting out our fixed cost of the bet from the gross value gets \\($0.973-1 = \$0.027\\).  Unsurprisingly, the expected value for the number bet and the color bet are identical.  All roulette bets are designed so that they all have the same (negative) expected value.
</details>

### Gross vs. Net
We've seen in the previous two examples that there are two points of view to take when calculating expected values of games which we pay to play.

1. Take the value of each outcome to be the *net* value.  When we compute the expectation this way we are done because we have factored the cost to play into the values.
2. Take the values of each outcome to be the *gross* value.  When we compute the expectation this way, we need to subtract the cost to play from the result to get the real value.  

These two strategies are guaranteed to have the same result.  Because paying for the game and playing the game are independent, their expected values can be added together.

### Shortcomcings of Expectation

Expectation is a powerful tool in analyzing games of chance.  The higher the expection, the better it is to play the game, right?  In general, this is true, but remember that expectation is based on the ability to *repeatedly* play a game.  Let's look at very silly, contrived example to see what can go wrong.

| Result | Probability | Value (Net) |
| :---: | :---: | :---: |
| Win | $\frac1{100}$ | \\$100,000,000,000 |
| Lose | $\frac{99}{100}$ | -\\$1,000,000,000 |

The expectation is

$$ E = \frac1{100}\cdot(\$100,000,000,000) + \frac{99}{100}\cdot(-\$1,000,000,000) 
= 10,000,000.$$

According to expectation, we gain on average ten million dollars for playing this game.  One should play this game as often as possible, right?  Not exactly.  We see that 99 times out of 100 we will lose and be on the hook for one billion dollars.  We can not afford to play this game!

This is related to a common fallacious gambling strategy called a [Martingale](https://en.wikipedia.org/wiki/Martingale_(betting_system)).  In this system, a player increases their bet each time the play in order to cover all of their previous losses if they win.  Once they win, which will happen eventually, they'll have earned money.  The problem with the Martingale system, just like the game above, is that in order to cover previous losses the bet will grow very large.  Eventually, the gambler will encounter a string of losses which will bankrupt them before they are bailed out by a win.

We'll look at one more (rather complicated) game of chance.  This example combines some challenging probability computations with the expected value computation.
<details class="example" markdown="1">
<summary>Dice Game</summary>
A game is played with four fair standard six-sided dice.  The dice are rolled and the player is paid out based on how many sixes are rolled.

|Number of 6's| Value |
| :---: | :---: |
| 0 | \\$0 |
| 1 | \\$1 |
| 2 | \\$2 |
| 3 | \\$4 |
| 4 | \\$8 |

We need to compute the probability of each value occuring.  Since all dice are fair, we can use the formula

$$ P(E) = \frac{\text{Number of outcomes in }E}{\text{Number of outcomes in Sample Space}}. $$

Since there are four dice and each has six outcomes, there are $$6^4=1296$$ possible outcomes.  Now, for each possible value, we need to compute the probability by counting how many outcomes are in the corresponding event.

**Probability of no sixes (value 0).**  By the multiplication rule, there are $5^4=625$ outcomes with no 6's, for a probability of $\frac{625}{1296}$.

**Probability of one six (value 1).**  Things get slightly more difficult  here.  We see that the outcomes can be built with the following step-by-step process.
1. Choose a die to be the six (**4 options**), and
2. Choose non-six values for the other three dice (**125 options**)
  * With five possible values for each of the three other dice, the multiplication rule gives $5^3=125$ possibilities.

So there are $4\times 125 = 500$ possible outcomes with a probability of $\frac{500}{1296}$

**Probability of two sixes (value 2).**  Like before we use the following step-by-step process.
1. Choose two dice to be sixes (**6 options**, ${}_4 C_2$), and
2. Choose non-six values for the remaining two dice (**25 options**).

So there are $25\times 6 = 150$ outcomes and a probability of $\frac{150}{1296}$.

**Probability of three sixes (value 4).**  We can make these outcomes in the same way.
1. Choose three dice to be sixes (**4 options**, ${}_4 C_3$), and
2. Choose a non-six value four the remaining die (**5 options**).

So there are 20 such outcomes and a probability of $\frac{20}{1296}$.

**Probability of four sixes (value 8).**  There is only one such outcome and so the probability is $\frac{1}{1296}.

A sanity check that we've done things correctly is that we have indeed accounted for all possible outcomes because
$$ 625+500+150+20+1 = 1296. $$

We can summarize these results with the following table.

|Number of 6's| Value | Probability |
| :---: | :---: | :---: |
| 0 | \\$0 |$\frac{625}{1296}$ |
| 1 | \\$1 |$\frac{500}{1296}$ |
| 2 | \\$2 |$\frac{150}{1296}$ |
| 3 | \\$4 |$\frac{20}{1296}$ |
| 4 | \\$8 |$\frac{1}{1296}$ |

And finally we can compute expectation with probabilities times values.

$$\begin{align*}
E &= \frac{625}{1296}\cdot 0 + \frac{500}{1296}\cdot 1 + \frac{150}{1296}\cdot 2 + \frac{20}{1296}\cdot 4 + \frac{1}{1296}\cdot 8 \\[0.5em]
&= \frac{1}{1296}\left(0 + 500 + 300 + 80 + 8\right) \\[0.5em]
&= \frac{888}{1296} \approx 0.685
\end{align*}$$

We see that without considering a cost to play, the game will earn the player about 69 cents per play.  So whoever is running this game will be sure to charge players more than that in order to guarantee a profit.
</details>

### Fair Games

In the previous example, we looked at the value of a game without considering the cost to play (gross value).  The expected value of the game needs to take the gross value and subtract the cost to play.
* If the expected value of a game is 0 then the game is called **fair**.  In this situation, the cost to play the game is equal to the expected payout.  Neither the player nor the people running the game (the house) are expected to earn any money in the long term.
* The expected value of a game is sometimes called the **house edge**.  We have to be careful to analyze the game from the house's perspective when using this term.  A positive house edge means that the casino expects to gain money on every play.  A negative house edge (which does not exist in the real world) would mean that the house would lose money on every play.

<div class="definition">
If a game of chance has an expected value of 0, then it is called a <strong>fair game</strong>.  Otherwise, the difference between the cost to play and the expected payoff is called the <strong>house edge</strong>.
</div>

As a brief example, the house edge for the roulette examples above is \\$0.027.  We computed that the player expects to *lose* \\$0.027 per play, which means that the house expects to *gain* that much.

A variety of other situations such as the purchase of warranties or insurance policies also fit the pattern of a game of chance.  Rather than paying to play for a chance to win more money, an insurance policy has one pay for a chance to not have to pay an unexpected cost later.

<div class="example" markdown="1">
Most pieces of electronics come with some manufacturer warranty which allows free replacement or repair of items which break during their initial use, typically the first year.  The store will try to sell you an *extended* warranty which provides coverage beyond the first year.

Let's suppose that Amanda just bought a \\$1,000 laptop, and the store is trying to sell her an extended warranty.  If we want to evaluate the expected value of a warranty, we'll need a bit of information.

| Result | Probability | Value (gross) |
| :---: | :---: | :---: |
| Breaks Under Warranty | ?? | ?? |
| Does not Break | ?? | 0 |

So far, all that we can say with certainty is that if that laptop does not break during the warranty period, then the warranty has no value.  To complete the analysis Amanda needs to know the following.
1. What is the probability that her laptop will break under warranty?
    * This sort of information may be found online from sources such as Consumer Reports.  The probability will depend on the manufacturer and particular model.
    * For our example, let's say that there is a **10% chance** that the item will require repair.
2. What is the value of the warranty if the laptop does break?
    * This is the same as asking how much the repairs will cost.  The warranty will cover the cost of repairs, so the money *not* spent on repairs is the value of the warranty.
        * In reality there are many ways that the laptop may break, and each will have its own associated cost.  Some may require full replacement of the laptop and others may require only minor repairs.
        * The cost will also depend other factors such as the particular shop that the laptop is taken to.
    * Since expectation is itself an average, it's ok to use the average cost of repairs, which can sometimes be researched as well.  For this example we'll suppose that the average cost of repairs is **\\$300**.
3. The probability that the laptop does not break under warranty will just be the complement of the probability that it does break.  Since we assumed a 10% failure rate, the non-failure rate is **90%**.

With her research done, now Amanda's table looks as follows:

| Result | Probability | Value (gross) |
| :---: | :---: | :---: |
| Breaks Under Warranty | 0.1 | \\$300 |
| Does not Break | 0.9 | 0 |

We see that the expected value of the warranty is 

$$\begin{align*}
E &= P(\text{Break})\cdot V(\text{Break}) + P(\text{No Break})\cdot V(\text{No Break}) \\
	&= \frac{1}{10}\cdot(\$300) + \frac{9}{10}\cdot (0) = \$30 \\[0.5em] 
\end{align*}$$

Since the warranty will pay out on average \\$30, the **fair** price for it is \\$30.  Amanda should not accept a warranty costing above \\$30.  If the store offered the warranty for \\$40, they would have a **house edge** of \\$10.
</div>

This final example shows the broad utility of expectation beyond simple games.  Many real-world processes can be analyzed in this way.

## Learning Objectives
* Compute the expectation of a random process.
* Use expectation to compute the expected value of a game of chance
* Determine whether a game of chance is fair/ what is the house edge
