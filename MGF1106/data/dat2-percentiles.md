---
layout: page
title: "DAT2: Percentiles"
---	

{% assign basedir = site.url| append: "/MGF1106/data" %}
{% assign imgdir = basedir| append: "/images" %}

# Percentiles

A **percentile** is something that we all have at least some passing familiarity with.  Parents are familiar with their children's height and weight being stated in terms of percentiles, and students are used to seeing their standardized test results in terms of percentiles.  The idea of a percentile is fairly straightforward.  If we are in the 75th percentile, it means that 75% of people are as good or worse than us.  Alternately, we may think of it as meaning that we are in the top 25%.  In practice, the computation can be a little messy.

<div class="definition" text="Percentile">
The <strong>$\boldsymbol{k}$-th percentile</strong> of a data set is a value, denoted $P_k$ such that $k$ percent of the data is less than (to the left of) $P_k$ and the remaining $100-k$ percent is greater than (to the right of) $P_k$.
</div>

Because the definition talks about comparisons such as less than and greater than, we can see that the definition only applies to numerical data.  Indeed, the above definition only truly works for *continuous* data where there are infinitely-many data points and a single point makes up 0 percent of the data.  Regardless, we can see this definition as our goal.  When we try to find $P_k$, we'll be looking to cut the data to to $k$ percent on the left and $100-k$ percent on the right.

We will state the procedure for computing a percentile up front, and we will try to motivate why it works as we work through some examples.

<div class="warning">
There is no standard definition of a percentile.  If you search other sources you will find similar but likely subtly different methods.  We use this method because the computations are more straightforward than most others.
</div>

<div class="procedure" text="Finding Percentiles" markdown="1">
To follow this procedure we require a data set $X$ with data points $x_1, x_2, \dots x_N$.  We will show how to compute the $k$-th percentile.  Here $k$ is percentage, so it is a number $0<k<100$.

1. **Sort the data least to greatest if it isn't already sorted.**  Now $x_1$ will be the smallest data point and $x_N$ will be the largest.
2. **Compute $\boldsymbol{L}$, how many data points are make up $\boldsymbol{k}$ percent of the data.**  Sometimes $L$ is called the *locator*.
   * The computation is $L = N\cdot\frac{k}{100}$.  ($\frac{k}{100}$ is just converting $k$ to a decimal proportion.)
   * The interpretation oft $L$ is that ideally we want $L$ data points to be to the left of the percentile and the remaining $N-L$ to the right.
3. **The computation depends on whether $\boldsymbol{L}$ is a whole number or not.**
   * If $L$ is a whole number, $P_k$ is the average of the $L$-th and $(L+1)$-st data points.  $\displaystyle P_k = \frac{x_L+x_{L+1}}{2}$.
   * If $L$ is not a whole number, round $L$ up to the next whole number, $\lceil L \rceil$.  $\displaystyle P_k = x_{\lceil L \rceil}$.
</div>

<div class="note">
The locator $L$ is not a value itself.  It is telling you which <em>data point</em> the percentile will located nearby.  You always have to use the locator to lookup one or two data points.
</div>


To see how this might be done, we'll look at a very special percentile, called the median, first.

## The Median
The **median** is another name for the 50th percentile.  So when we find the median, we're looking for a value such that half of the data is less than that value and the other half is greater than the value.  According to the procedure above, we do the following.

<div class="procedure" text="Finding the Median" markdown="1">
This is just a repeat of the general procedure with $k=50$ because the median is the 50th percentile.
1. **Sort the data least to greatest.**
2. **Find the locator.** $L=0.50\cdot N$ ($N$ is the number of data points).
3. **Find the median depending on whether $\boldsymbol{L}$ is a whole number or not.**
    * If $L$ is a whole number, $\displaystyle P_{50} = \frac{x_L+x_{L+1}}{2}$. 
	    * This will happen when there an even number of data points.
		* Informally, the procedure averages the "middle" two data points.
	* If $L$ is not a whole number, round it up to $\lceil L\rceil$ and $P_{50} = x_{\lceil L\rceil}$.  
	    * This will happen when there is an odd number of data points. 
		* Informally, the procedure just takes the "middle" data point as the median.
</div>

Take for example a very simple data set with just two values: 0 and 4.  This data is illustrated below.

<img class="center" src="{{imgdir}}/numline1.svg" alt="A data set with only the values 0 and 4.">

1. **Sort the data.** Note that we have already sorted the data points by plotting them on a number line and labeling them according to their order on the number line.
2. **Compute the locator, $\boldsymbol{L}$.**  Since there are two data points $N=2$ and $L=0.50*2=1$.  Remember the interpretation of the locator is that we want $L=1$ data point to be left of the percentile and the remaining $N-L=1$ to be to the right.  Technically, any value between $x_1=0$ and $x_2=4$ would work for this purpose, but we need to make a definite choice.
3. **Compute the percentile from $\boldsymbol{L}$.**  Because $L=1$ is whole, we average $x_1$ and $x_2$.  $\frac{x_1+x_2}{2} = \frac{0+4}{2} = 2$.

<img class="center" src="{{imgdir}}/numline1p50.svg" alt="A data set with only the values 0 and 4.">

The situation above will hold whenever there are an even number of data points.  In this case $L=0.50\cdot N$ will be a whole number.  The data points $x_L$ and $x_{L+1}$ will be the two "middle" points of the data set, and the median will be chosen right between them.

<details class="example" markdown="1">
<summary>Even Sized Data Set</summary>
Suppose we have the following data set with $N=10$ numbers.  

$$\begin{array}{rrrrr}
3 & 3 & 8 & -1 & 1  \\
0 & -2 & -4 & -1 & -4 \\ 
\end{array}$$

1. **Sort the data.** In sorted order the data is

$$\begin{array}{rrrrr}
-4 & -4 & -2 & -1 & -1 \\
0 & 1 & 3 & 3 & 8 \\
\end{array}$$

<div class="warning">
When sorting data it's easy to miss a point.  Be sure to at least count the numbers in your sorted list and make sure it matches the original.
</div>

{:start="2"}
2. **Compute the locator, $\boldsymbol{L}$.**  Since there are $N=10$ data points, $L=0.50*10=5$.  So we want five points to the left of $P_{50}$ and the remaining five to the right.
3. **Compute the percentile from $\boldsymbol{L}$.**  Because $L=5$ is whole, we average $x_5$ and $x_6$.  Looking back at our sorted data, we can see that $x_5=-1$ and $x_6=0$.  So $\frac{x_5+x_6}{2} = \frac{-1+0}{2} = -0.5$.

As before, the median was between the two "middle" numbers of the data set.
</details>

If there were three data points then there's no way this can work exactly.  50% of three is $0.50\times 3 = 1.5$, and since data points are not divisible, there's no way to do the split exactly.  Take for example the data set below with values -1, 0, and 4.

<img class="center" src="{{imgdir}}/numline2.svg" alt="A data set with only the values -1, 0, and 4.">

1. **Sort the data.** Note that we have already sorted the data points by plotting them on a number line and labeling them according to their order on the number line.
2. **Compute the locator, $\boldsymbol{L}$.**  Since there are three data points $N=3$ and $L=0.50*2=1.5$.  Remember the interpretation of the locator is that we want $L=1.5$ data point to be left of the percentile and the remaining $N-L=1.5$ to be to the right.  Of course this is impossible because data points are not divisible.
3. **Compute the percentile from $\boldsymbol{L}$.**  Because $L=1.5$ is whole, we round up to $\lceil 1.5\rceil = 2$ and find $P_{50} = x_2 = 0$.  We see that this procedure ends up picking out the "middle" data point as the median.

<img class="center" src="{{imgdir}}/numline2p50.svg" alt="A data set with only the values -1, 0, and 4.  The median is 0.">

### Resistance to Change

One interesting feature about the median (and percentiles in general) is that extreme data does not change it.  If in the above example we had the points -10000, 0, 4 instead, the median would still be 0 because we do not change the locator or the value of the data point selected by the locator.

## Quartiles

The **first quartile**, denoted $Q_1$ is another name for the 25th percentile ($P_{25}$) and the **third quartile**, denoted $Q_3$ is another name for the 75th percentile ($P_{75}$).  The median could be called the second quartile.  The quartiles divide a data set up into four regions which each are approximately 25% of the data.
* 25% of the data is between the minimum value and $Q_1$,
* 25% of the data is between $Q_2$ and the median,
* 25% of the data is between the median and $Q_3$, and
* 25% of the data is betweeen $Q_3$ and the maximum value.

The middle 50% of the data lies between $Q_1$ and $Q_3$ and is called the **interquartile range** or IQR.

<div class="warning">
In other sources, you may see special procedures for computing quartiles such as taking the median of the upper or lower half of the data.  In our treatment of this material, <strong>quartiles are not treated specially compared to any other percentiles.</strong>
</div>

<details class="example" markdown="1" open>
<summary>Finding Quartiles</summary>
Suppose we have the following data set of $N=10$ numbers.

$$\begin{array}{rrrrr}
5 & 2 & -7 & -10 & 0  \\
1 & 10 & 10 & 8 & -2 \\ 
\end{array}$$

We'll compute $Q_1$ in detail.

1. **Sort the data.** In sorted order the data is

$$\begin{array}{rrrrr}
-10 & -7 & -2 & 0 & 1  \\
2 & 5 & 8 & 10 & 10 \\ 
\end{array}$$

{:start="2"}
2. **Compute the locator, $\boldsymbol{L}$.**  Since there are $N=10$ data and we are computing the $k=25$-th percentile.  The locator is, $L=0.25\cdot10=2.5$.  
3. **Compute the percentile from $\boldsymbol{L}$.**  Because $L=2.5$ is not whole, we round up to 3.  Then $Q_1= x_3$.  Looking back at the **sorted** data we see that $Q_1=x_3=-2$

$Q_3$ is computed similarly, except that the locator is $10\cdot0.75=7.5$.  As before, since the locator is not whole we round it up to 8 and find $Q_3=8$.  This means that the IQR of this data set is $Q_3-Q_1=8-(-2)=10$.
</details>

### Outliers

An **outlier** is a data that is significantly higher or lower than the rest of the points in the data set.  As seems to be standard for this section, there are multiple ways to define an outlier.  One simple but effective way is to use the IQR to find outliers.

<div class="definition">
Any data points greater than $Q_1-1.5\cdot \text{IQR}$ or less than $Q_3+1.5\cdot \text{IQR}$ are considered <strong>outliers</strong>.
</div>

In other words, all data in the interval $[Q_1-1.5\cdot\text{IQR},Q_3+1.5\cdot\text{IQR}]$ is considered to be typical, and everything else is an outlier.  We can see that the width of this interval is

$$\begin{aligned}
(Q_3+1.5\cdot\text{IQR}) - (Q_1-1.5\cdot\text{IQR}) &= Q_3+1.5\cdot\text{IQR} - Q_1+1.5\cdot\text{IQR} \\
&= Q_3-Q_1 + 3\cdot\text{IQR} \\
&= \text{IQR} + 3\cdot\text{IQR} \\
&= 4\cdot\text{IQR}
\end{aligned}$$

So essentially, the outlier rule that we are using gives a central 4 IQRs of space for typical data points to lie in.

<details class="example" markdown="1">
<summary>Outliers</summary>
Consider the following data set with $N=20$ data points.  For convenience it is already sorted.

$$\begin{array}{cccccccccc}
-5.4 & -3.1 & -2.7 & -2.2 & -1.5 & -1.2 & -0.7 & 0.1 & 1.9 & 2.7 \\
3.7 & 3.8 & 4.4 & 4.9 & 7.2 & 8.1 & 8.8 & 11.6 & 19.5 & 22.1 \\
\end{array}$$

* For $Q_1$ the locator is $20\cdot0.25=5$.  This is a whole number, so 

$$Q_1=\frac{x_5+x_6}{2} = \frac{-1.5+(-1.2)}{2} = -1.35.$$

* For $Q_3$ the locator is $20\cdot0.75=15$.  This also is a whole number, so

$$Q_3=\frac{x_{15}+x_{16}}{2} = \frac{7.2+8.1)}{2} = 7.65.$$

* So $\text{IQR} = Q_3-Q_1 = 7.65-(-1.35) = 9$.

Then according to the rule we set forth:
* Anything less than $Q_1 - \text{IQR}\cdot1.5 = -1.35-1.5\cdot9 = -14.85$ is an outlier, and
* Anything greater than than $Q_3 + \text{IQR}\cdot1.5 = 7.65+1.5\cdot9 = 21.15$ is an outlier.

The only data point which counts as an outlier is the maximum value, 22.1.

Note that when computing the quartiles and the IQR we only used $x_5, x_6, x_15$ and $x_16$.  This means that making any changes to $x_1$ through $x_4$ and $x_{17}$ through $x_{20}$ would make no difference to the outlier bounds so long as we preserve the sorted order.  So it is possible for all of those points to be outliers.
</details>

## Five Number Summary

The minimum value, $Q_1$, the median, $Q_3$, and the maximum value together comprise the **five number summary** of a data set.



