---
layout: page
title: "NRM1: Introduction"
---	

{% assign basedir = site.url| append: "/MGF1106/normality" %}
{% assign imgdir = basedir| append: "/images" %}

# Statistics

Statistics is the study of how patterns in data can be used to infer broader trends.  In a very broad sense, this is the inverse of probability theory.  When we studied probability theory, we saw how to use the distribution to predict the results of a random process.  Now we wonder to what extent we can use the results of a random experiment to determine information about the underlying distributuion of the random experiment.

Here's a motivating example.  Let's say we have a fair coin and our random process is going to be to flip the coin 10 times.  Probability theory can tell us information such as:
* The probability of flipping all heads (or all tails) is $\frac{1}{2^{10}}$ or aproximately 0.00097
* The probability of flipping exactly five heads is $\frac{ {}_{10}C_5}{2^{10}}=\frac{252}{1024}$ or approximately 0.2461.

This means that if we were to run the random process 10000 times we would expect that
* $10000\cdot0.00097 = 9.7\approx 10$ of the trials should have all heads, and another approximately 10 should have no heads.
* Approximately $10000\cdot0.2461 = 2461$ of the trials should have exactly 5 heads.

Below you can see the results of actually running this process 10000 times.

<figure>
<img src="{{imgdir}}/FlipTrials.svg" alt="Histogram of trials when a coin is flipped 10 times" class="center">
<figcaption> A simulation of an 10000 trials of an experiment where a coin is flipped 10 times.
</figcaption>
</figure>

We can see that the data more or less matches the predictions of probability theory.  This is more than just coincidence.  The **law or large numbers** guarantees that as the number of trials grows that the proportion of trials with a given outcome will match the probability of that outcome more closely.  Statistics comes from the other direction.  If all we have is data from a random process, what can we say about the distribution that generated that data?  For example, if we were only given the data in the above chart, could we work out that the coin used was fair?  In general, we may settle for figuring out the expectation, variance or some other property of the distributiion.

There is inherent uncertainty in statistical questions.  It is unlikely that we could distinguish between a coin that is fair and one that comes up heads 51% of the time. (TODO: Figure out where this discussion goes).

## Normal Distributions
Many data sets follow what is called a **normal distribution**.  A normal distribution has the following properties.
* **Bell-shaped**.  A normal distribution will have a single peak and will taper off as you move away from the peak.
* **Symmetric.**  The distribution should look the same on the left and the right of the peak.  If the distribution is not symmetric it is called **skewed**.

TODO: Example distributuions that are/are not normal.

Not every bell-shaped symmetric distributuion will be a normal distributuion, but more often than not it will be.  In fact, there's a theorem called the **central limit theorem** which says that quantities that are the sum of many smaller random factors will typically be normal.  So being able to analyze normally distributed data is an important skill to have.


