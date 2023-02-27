---
layout: page
title: "PR4: Variance and Standard Deviation"
---

{% assign basedir = site.url| append: "/MGF1106/probability" %}
{% assign imgdir = basedir| append: "/images" %}

# Measuring Dispersion

In the previous section, we looked at an example of a game where the expectation didn't tell the whole story.

| Result | Probability | Value (Net) |
| :---: | :---: | :---: |
| Win | $\frac1{1000}$ | \\$100,000,000,000 |
| Lose | $\frac{999}{1000}$ | -\\$1,000,000,000 |

The expectation worked out to earning a million dollars per game, but the game is essentially unplayable because nine hundred ninety-nine times out of a thousand, a player will be millions in debt.  The problem is that the possible values are very far away from the expected (average) value.  The distance of values from the average is sometimes called *dispersion*.  There are many measures of dispersion, but we will focus on those with the most theoretical value.  The notion that we're really after is called *standard deviation*, but to get there, we'll need to go through *variance*.

<div class="note">
Like with expected value, we are still only considering random processes whose outcomes are assigned values.  Otherwise, the operations we perform will make no sense.
</div>

## Variance

One measure of dispersion is called variance.  One nice way to think about variance is that we're just going to be doing another expectation, but we are going to redefine the value of each outcome based on distance from the usual expected value.  Note that we say *based on* the distance.  Rather than use the exact distance, we will use the square distance.  If we compute that a random process $X$ has an expectation of $E(X)$, then we will use

$$ D(v) = (v-\text{E}(X))^2 $$

as our measure of how far away from the expected value we are.  Note that the normal distance would be just $\|v-\text{E}(X)\|$.  Sometimes this quantity $D(v)$ is called the *squared deviation from the mean*.  There are deep theoretical reasons for using this instead of the normal distance which we will not delve into.

To be definite, let's say that we have a random process $X$ with outcomes $o_1, o_2, \dots, o_N$.  The following procedure will compute the variance of $X$.

1. Compute the expected value of the proccess, $E(X)$.
2. For each outcome $o$, the new value for $o$ will be $D(V(o))=(V(o)-\text{E}(x))^2$.  
    * This is just plugging the original value of $o$ into the square deviation function discussed above.
3. Compute $\text{Var}(X) = P(o_1)\cdot D(V(o_1))+P(o_2)\cdot D(V(o_2))+\cdots+p(o_N)\cdot D(V(o_N))$.  
This is just the expectation with the new values based on deviation.

Because this is an expectation calculation, we can and will typically group outcomes with the same value and use the grouped form

$$ \text{Var}(X) = P(\text{value} = v_1)D(v_1)+\cdots+P(\text{value=} v_k)D(v_k) $$

where $v_1,\dots,v_k$ are the possible values taken by $X$.

We'll look at a simple example to see how a procedure for this can be implemented.  Let's take the familiar example of the fair four-sided die.  In the past, we have computed its expectation is $E = 2.5=\frac52$.

| Value (v) | $P(\text{value } = v)$ | $D(v) = (v-\text{E})^2$ |
| :---: | :---: | :---: |
| 1 | $\frac14$ | $(1-2.5)^2 = 2.25$ | 
| 2 | $\frac14$ | $(2-2.5)^2 = 0.25$ | 
| 3 | $\frac14$ | $(3-2.5)^2 = 0.25$ | 
| 4 | $\frac14$ | $(4-2.5)^2 = 2.25$ |

Some things to pay attention to here:
1. The values closer to the mean (2 and 3) have low dispersion, while the farther away ones (1 and 4) have higher dispersion, and
2. It does not matter whether the values are above or below the mean, the dispersion will be positive.  This is one reason that we square the quantity.

Now we can compute the variance as

$$\begin{align*}
\text{Var}(x) =&{} P(\text{value} = 1)\cdot D(1)+P(\text{value} = 2)\cdot D(2) \\
 &+P(\text{value} = 3)\cdot D(3)+P(\text{value} = 4)\cdot D(4) \\[0.5em]
=&{} \frac14\cdot2.25+\frac14\cdot0.25+\frac14\cdot0.25+\frac14\cdot2.25 \\[0.5em]
=&{}1.25
\end{align*}$$

<details class="example" markdown="1" open>
<summary>Two Four-Sided Dice</summary>
Recall from [PR3-Expectation]({{basedir}}/pr3-expectation.html) that the expected value of two four-sided dice is twice the expectation of one die.  So we can use $E(X+X) = 2.5+2.5 = 5$.

| value ($v$) | $E = \lbrace\text{Has value = } v\rbrace$ | $P(E)$ | D(V) |
| :---: | :---: | :---: | :---: |
| 2 | $\lbrace(1,1)\rbrace$ | $\frac{1}{16}$| $(2-5)^2 = 9$ |
| 3 | $\lbrace(1,2), (2,1)\rbrace$ | $\frac{2}{16}$ | $(3-5)^2 = 4$|
| 4 | $\lbrace(1,3), (2,2), (3,1)\rbrace$ | $\frac{3}{16}$| $(4-5)^2 = 1$ |
| 5 | $\lbrace(1,4), (2,3), (3,2), (4,1) \rbrace$ | $\frac{4}{16}$ | $(5-5)^2 = 0$ |
| 6 | $\lbrace(2,4), (3,3), (4,2)\rbrace$ | $\frac{3}{16}$ | $(6-5)^2 = 1 $  |
| 7 | $\lbrace(3,4), (4,3)\rbrace$ | $\frac{2}{16}$ | $(7-5)^2=4$ |
| 8 | $\lbrace(4,4)\rbrace$ | $\frac{1}{16}$ | $(8-5)^2=9$ |

And so 

$$\begin{align*}
\text{Var} =&{} \frac1{16}\cdot 9 + \frac{2}{16}\cdot 4 + \frac{3}{16}\cdot 1 + \frac{4}{16}\cdot 0 + \frac{3}{16}\cdot 1 + \frac{2}{16}\cdot 4 + \frac{1}{16}\cdot 9 \\[0.5em]
=&{} 2.5
\end{align*}$$

</details>

In the above example, we found that the variance of two dice was twice the variance of one die.  This is identical what we obsereved with expecation.

<div class="theorem">Suppose that $X$ and $Y$ are <strong>independent</strong> random processes.  Then 

$$\text{Var}(X+Y) = \text{Var}(X)+\text{Var}(Y).$$

</div>

Recall that $X+Y$ is the shorthand for performing $X$ and $Y$ and adding the results.

<div class="warning">
From the above, if $X$ is performed $k$ times and the results of all of the trials are added together, the variance will be $k\cdot\text{Var}(X)$ so long as trials of $X$ are independent.  It would be tempting to use $k\cdot X$ as a shorthand for this, but in most books this means to multiply the values of $X$ by $k$, and this will have a variance of $k^2\cdot \text{Var}(x)$.
</div>

This theoretical result, that the variance of a step-by-step process is the main reason that we're discussing it.  Variance provides a building block for other, more useful measures of dispersion such as standard deviation.

## Standard Deviation

One large issue with variance is that its units (dimension) is confusing.  Say for example we have a game whose outcome can be measured in dollars.  A typical term in the variance computation is

$$ P(o)(V(o)-\text{E})^2.$$

Both $V(o)$ and the expected value, $E$ are measured in dollars, so $V(o)-\text{E}$ can also be mesaured in dollars.  So then $(V(o)-\text{E})^2$ is measured in dollars squared?  Probability is unitless, so it does not change the units.  It's difficult to understand what square dollars are and how to interpret that.  If square units are hard to deal with, then take the square root!

<div class="definition">
Given a random process $X$, the <strong>standard deviation</strong> of $X$, denoted $\text{SD}(x)$.  It is calculated by

$$ \text{SD}(X) = \sqrt{\text{Var}(x)}. $$
</div>

The standard deviation will have the same units as the random process, $X$.  In some sense, the standard deviation is representing the typical distance between the value of a random process and its expected value.  We'll fill in more details in the unit on statistics, but a good rule of thumb for games of chance is that if you can't afford a standard deviation (some would say two) then don't play the game!

<!--- 
<details class="example" markdown="1" open>
<summary>Expensive Game</summary>

Let's return to our too-expensive-to-play game.

| Result | Probability | Value (Net) |
| :---: | :---: | :---: |
| Win | $\frac1{100}$ | \\$100,000,000,000 |
| Lose | $\frac{99}{100}$ | -\\$1,000,000,000 |

We found the expectation was

$$ \text{E} = \frac1{100}\cdot (\$100,000,000,000) + \frac{99}{100}\cdot(-\$1,000,000,000) = \$10,000,000 $$

| Result | Probability | Value (Net, $v$) | $D(v) = (v-\text{E})^2$ | 
| :---: | :---: | :---: | :---: |
| Win | $\frac1{100}$ | \\$100,000,000,000 | $\approx9.998\times10^{21}$|
| Lose | $\frac{99}{100}$ | -\\$1,000,000,000 | $\approx1.0201\times10^{18}$ |

$$\begin{align*}
\text{Var}(X) &= \frac{1}{100}\cdot(9.998\times10^{21}) + \frac{99}{100}(1.0201\times10^{18}) \\
 &\approx 1.0099\times10^{20} \\
\text{SD}(X) &= \sqrt{\text{Var}(X)} \approx \sqrt{1.0099\times10^{20}} \\
 &\approx 10,049,373,065
\end{align*}$$

While variance has strange units, standard deviation is again measured in dollars. The standard deviation is about 10 billion dollars.  So unless you have that kind of cash, the game is not to be played despite its positive expectation.

</details>
-->
<details class="example" markdown="1">
<summary> Unfair Coin </summary>
Suppose a coin is unfair in that it flips heads with a probability of $\frac34$ and tails with probability of $\frac14$.  We will assign a value of 1 to heads and a value of 0 to tails.

| Value ($v$) | Probability of $v$ | $D(v) = (v-\text{E})^2$ |
| :---: | :---: | :---: |
| 1 | $\frac34$ | $(1-\frac34)^2 = \frac{1}{16}$ |
| 0 | $\frac14$ | $(0-\frac34)^2 = \frac{9}{16}$ |

In the above table, we can fill out the first two columns immediately.  But we need to do the expecation calculation before filling out the third.

$$ \text{E} = \frac34\cdot 1 + \frac14\cdot 0 = \frac34. $$

Then we can fill out the third column and find 

$$\begin{align*}
\text{Var} &= \frac34\cdot\frac{1}{16} + \frac14\cdot\frac{9}{16} \\[0.5em]
 &= \frac{1}{16}(3+9) = \frac{12}{16} = \frac{3}{4} \\
\text{SD} &= \sqrt{\text{Var}} = \frac{\sqrt{3}}{2} \\
\end{align*}$$

</details>

<details class="example" markdown="1" open>
<summary> All Unfair Coins </summary>
Suppose a coin is unfair in that it flips heads with a probability of $p$ and tails with probability of $(1-p)$.  We will assign a value of 1 to heads and a value of 0 to tails.

| Value ($v$) | Probability of $v$ | $D(v) = (v-\text{E})^2$ |
| :---: | :---: | :---: |
| 1 | $p$ | $(1-p)^2$ |
| 0 | $1-p$ | $(0-p)^2 = p^2$ |

In the above table, we can fill out the first two columns immediately.  But we need to do the expecation calculation before filling out the third.

$$ \text{E} = p\cdot 1 + (1-p)\cdot 0 = p. $$

Then we can fill out the third column and find 

$$\begin{align*}
\text{Var} &= p\cdot(1-p)^2 + (1-p)\cdot p^2 \\[0.5em]
 &= p(1-p)(1-p+p) = p(1-p) \\
\text{SD} &= \sqrt{\text{Var}} = \sqrt{p(1-p)}
\end{align*}$$
</details>

The above example is a bit complicated, but it's result will prove to be useful when studying statistics.

<div class="theorem">
Suppose that $X$ is a coin which comes up heads with a probability of $p$, assigns a value of 1 to heads and a value of 0 to tails.  Then
<div markdown="1">
* $\text{E}(X) = p$,
* $\text{Var}(X) = p(1-p)$, and
* $\text{SD}(X) = \sqrt{p(1-p)}$
</div>
</div>

### Alternate Notation
When reading in other sources you will sometimes find different notation for expectation, variance, and standard deviation.  This notation comes from statistics when describing data.

| Standard | Alternate |
| :---: | :---: |
| $\text{E}$ | $\mu$ |
| $\text{Var}$ | $\sigma^2$ |
| $\text{SD}$ | $\sigma$ |

A nice features of the alternate notation is that it makes the relationship between variance and standard deviation clear.  The differences between statistics of data sets and properties of random processes can be confusion , so we will stick to $\text{E}, \text{Var},$ and $\text{SD}$ while we study probability.

## Learning Objectives
* Compute the variance and standard deviation of random processes

