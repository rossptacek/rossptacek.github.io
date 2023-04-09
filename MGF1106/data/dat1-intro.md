---
layout: page
title: "DAT1: Types of Data"
---	

{% assign basedir = site.url| append: "/MGF1106/data" %}
{% assign imgdir = basedir| append: "/images" %}

# What is Data

Any time we record information we make **data**.  This can be practically anything.  If we were recording information about people we could record their age, height, weight, gender, place of birth, current zip code, shoe size, or really anything imaginable.  There is much that can be said on the right way to to go about collecting data, but in this part of the course we will focus on what we can do with data that has already been collected.  And much of this depends on the type of data we have.

A single bit of information is called a **data point** whereas the collection of all information we have is called a **data set**.  Be careful though!  The values in  data set do not make a set as the same value (data point) can occur multiple times in a data set.

<div class="example" markdown="1">
As a simple example, suppose that we were studying the prevalence of various eye colors.  We may have the following data.

| Subject ID | Eye Color | Subject ID | Eye Color |
|:----------:|:---------:|:----------:|:---------:|
| 0001       | Brown     | 0008       | Hazel     |
| 0002       | Brown     | 0009       | Blue      |
| 0003       | Amber     | 0010       | Gray      |
| 0004       | Blue      | 0011       | Brown     |
| 0005       | Green     | 0012       | Hazel     |
| 0006       | Blue      | 0013       | Blue      |
| 0007       | Brown     | 0014       | Brown     |

The above table, makes up a **data set**.  To represent it in written form, we would take the data set to be a true set of ordered pairs $\lbrace (1, \text{brown}), (2, \text{brown}), (3, \text{amber}),\dots, (14, \text{brown})\rbrace$.  A **data point** would be a particular ordered pair such as "$(3, \text{amber})$".  However, when studying data we typically discard the subject identifiers and just consider the eye colors, (brown, brown, amber, blue, green, blue, brown, hazel, blue, gray, brown, hazel, blue, brown) to be the data set and each individual "blue" or "brown" would be a data point.  Dropping the identifiers makes it not be a true set anymore.
</div>

### Notation
In this class we will usually not use notation for the data set itself.  If we do, we'll name it with a capital letter such as $X$ or $Y$.  Then the data points will use subscripted lower case letters.  If our data set were $X$ then our data points would be $x_1,x_2,\dots, x_N$ if there were $N$ data points.  The subscript does not have to give the subject id.  Afterall, those have usually been discarded by the time we get to the data, and we may choose to rearrange the data points so that they are in ascending or descending order.

## Discrete vs. Continuous

The first major distintion we'll make is not about the data itself but about the *process* that created the data and what possible values that process could create.

<div class="note">
In many sources, the process will be called a <strong>variable</strong> or a <strong>random variable</strong>.  I find that this terminology confuses some students who are used to variables being things that are plugged into.
</div>

<div class="definition" text="Continous and Discrete">
A process is <strong>discrete</strong> if there are gaps between the possible values the process can create.  A process is <strong>continuous</strong> if there are no gaps between the possible values the process can create.
</div>

The definition above is imperfect, and fixing it would require a lengthy detour into another area of math called topology.  But we'll see that the distinction between discrete and continuous is mostly intuitive.  It's good to keep the principle in mind.
* **Discrete processes look like the counting numbers.**  The counting numbers are the set $\lbrace 1,2,3,\dots\rbrace$.  There are gaps between the counting numbers.  On a number line, you could put your pencil down on a counting number, wiggle it around slightly, and hit no other counting numbers.
* **Continuous processes look like the real numbers.**  The real numbers make up the whole number line.  If you wiggle your pencil around on the number line you'll hit nothing but real numbers.  There's nothing forcing continuous variables to be one-dimension like a line, however.  The key feature is that we can move through the possiblities without hitting a gap.

One thing to note is that continuous processes must produce infinitely-many possible values.  Discrete processes *can* be infinite (as the counting numbers are), but if a process has only finitely-many values then it *must* be discrete.  This highlights why it is important to look at the process rather than the data itself.  Any data which we collect is automatically finite!

Here are some examples.
* Measuring someone's height or weight is a **continuous** process.  It is measured with real numbers, not whole numbers.  For any valid height, we could wiggle the value up and down a bit and still have nothing but other valid heights.
* Measuring someone's zip code is a **discrete** process.  There are only finitely-many possible zip codes.  You can't move smoothly between two zipcodes.  As you travel you jump instantaneously from one to another.
* Measuring someone's age is **usually a discrete process**.  We only care to measure down to the year (or to the month with infants).  However since time itself flows continuously ([or does it?](https://en.wikipedia.org/wiki/Chronon)) we could measure someone's age down to the millisecond (or smaller) and make it a continuous process.

<details class="example" markdown="1">
<summary>Color</summary>
Suppose that we were collecting data by asking people what their favorite color was.  If this were a printed survey, we would probably only give a few possible answers, perhaps the colors of the rainbow.  This would be **discrete** data because there are only finitely many possible answers.  Even if we enlarged the possible responses to the colors of the biggest box of crayons, it would still be discrete.

Of course, color is not inherently discrete.  Any color can be smoothly brightened to white or darkened to black.  Even among different colors (hues) there is a continuous choice.
<figure class="center">
    <img src="{{imgdir}}/ciegamut.svg" alt="The CIE 1931 color gamut." class="center"/>
    <figcaption> An approximation of the visible gamut (CIE 1931).  Taken from <a href="https://commons.wikimedia.org/wiki/File:CIExy1931.svg">https://commons.wikimedia.org/wiki/File:CIExy1931.svg</a> </figcaption>
</figure>

If our process had been throwing a dart at the CIE 1931 gamut shown above and recording the resulting color, then we would have a continuous process.  
</details>

<details class="example" markdown="1">
<summary>Money</summary>
In a very real sense money is a discrete quantity.  You can not be handed money in denominations smaller than one cent.  So typically, measurements involving money such as measuring someone's salary would be **discrete**.  In reality, banks need to deal with fractions of pennies because interest calculations never come out to whole pennies.  And contrary to what Superman III and Office Space might have you believe, the banks do care about those penny fractions.  So a bank would model your money as a continuous quanity while you personally would likely consider it to be discrete.
</details>


## Numerical vs. Categorical
The other main distinction that we make is that of **numerical** data vs **categorical** data.

<div class="definition" text="Numerical, Categorical Data">
Data is considered <strong>numerical</strong> if it makes sense to do arithmetic with the data.  Otherwise it is considered <strong>categorical</strong>
</div>

<div class="warning">
Not all data that consists of numbers is numerical!
</div>

We want numerical data to really represent a quantity and not just numbers being used as an identification code.  Zip code, telephone number, and apartment number are examples of numbers which make no sense to add, subtrace, or average and therefore do not count as numerical data.


# Working with Discrete Data
When dealing with discrete data, we usually describe it in terms of how often each possible option occurs in the data set.  We can either do this as a **frequency** or **relative frequency**.

<div class="definition" text="frequency, relative frequency">
Suppose that a data set $X$ has values $x_1, x_2, \dots, x_N$. and $x$ is one
of the data points.
<ol>
	<li> The (absolute )<strong>frequency</strong> of $x$ is the number of times that $x$ occurs in the data set. </li>
	<li> The <strong>relative frequency</strong> of $x$ is the percentage of values in $X$ that are equal to $x$ expressed as a decimal.  In other words, the relative frequency of $x$ in the data set its absolute frequency divided by $N$.</li>
</ol>
</div>

## Frequency Tables
A **frequency table** represents a data set purely by the frequency with which each value appears.  We've seen frequency tables before in the unit on voting.  We just called them preference schedules.  The idea is the same.  Rather than writing out a value multiple times, just write out how many times the data point appears.

Take for example the simple data set at the start of this section.

| Subject ID | Eye Color | Subject ID | Eye Color |
|:----------:|:---------:|:----------:|:---------:|
| 0001       | Brown     | 0008       | Hazel     |
| 0002       | Brown     | 0009       | Blue      |
| 0003       | Amber     | 0010       | Gray      |
| 0004       | Blue      | 0011       | Brown     |
| 0005       | Green     | 0012       | Hazel     |
| 0006       | Blue      | 0013       | Blue      |
| 0007       | Brown     | 0014       | Brown     |

As a frequency table we would have:

| Eye Color | Frequency |
|:---------:|:---------:|
| Amber     | 1         |
| Blue      | 4         |
| Brown     | 5         |
| Hazel     | 2         |
| Gray      | 1         |
| Green     | 1         |

The beauty of a frequency table is that it does not matter how large our data set becomes, the number of rows in the frequency table will not change unless we encounter a new eye color. It is possible that this could happen as there are many rare conditions that our table does not account for.  Notable math Youtuber [3Blue1Brown (Grant Sanderson)](https://www.3blue1brown.com/) chose that name because he has sectional heterochromia in one of his eyes.  He would certainly need a new row of the table.  Supposing that we didn't survey people like Grant, here's what a Frequency table with 1000 respondents might look like.

| Eye Color | Frequency |
|:---------:|:---------:|
| Amber     | 56        |
| Blue      | 113       |
| Brown     | 743       |
| Hazel     | 57        |
| Gray      | 7         |
| Green     | 24        |

With a frequency table, it is easy to recover the number of data points, just add the frequencies up.  In the above table we can see that there are $56+113+743+57+7+24 = 100$ data points, as promised. If you are constructing a frequency table, this is a good way to check that you have not forgotten to add any data.

If proportions are desired, then it is easy to augment a frequency table with proportion data.  Simply divide each frequency by the number of data points.  Because dividing by 1000 is not so interesting, we'll look at our original, smaller table.

| Eye Color | Frequency | Relative Frequency        |
|:---------:|:---------:|:-------------------------:|
| Amber     | 1         | $\frac1{17}\approx0.0588$ |
| Blue      | 4         | $\frac4{17}\approx0.2353$ |
| Brown     | 5         | $\frac5{17}\approx0.2941$ |
| Hazel     | 2         | $\frac2{17}\approx0.1176$ |
| Gray      | 1         | $\frac1{17}\approx0.0588$ |
| Green     | 1         | $\frac1{17}\approx0.0588$ |

From here on, we will always give a discrete data set by its frequency table rather than listing out all of the data points.

## Bar Charts

A **bar chart** (or **bar graph**) is a way to visualize discrete data.  In a bar chart, the frequencies are displayed as rectangles (called bars) whose height is the frequency of each value.

<figure class="center">
<img class="center" src="{{imgdir}}/eye_bar_chart.svg" alt="Eye color bar chart of 1000 data points.">
<figcaption> A bar chart showing eye colors for 1000 respondents.</figcaption>
</figure>

Above we see what a bar graph for eye color might look like if our meager survey of only fourteen people were extended to 1000.  The colors of the bars are purely cosmetic.  The bar chart would give the same information regardless of color.  Of course, choosing bar colors which have nothing to do with the underlying eye color would create a very misleading chart.

A bar chart can be made with proportions instead of frequencies, but it does not change the chart meaningfully.

<figure class="center">
<img class="center" src="{{imgdir}}/eye_bar_chart_rel.svg" alt="Eye color bar chart of 1000 data points using proportions.">
<figcaption> A bar chart showing proportions of eye colors for 1000 respondents.</figcaption>
</figure>

## Pie Charts
A pie chart is a more natural way of representing relative frequency.  In a pie chart, a circle is divided up into radial sections so that the area of the section corresponding to a value is proportional to its frequency.  In other words, the relative frequency of a value will give the proportion of the circle it takes up.  For example if a value has a relative frequency of 0.50 (50%) then its corresponding part of the pie chart will take up half of the circle.  Below, our eye color data is represented as a pie chart.

<figure class="center">
<img class="center" src="{{imgdir}}/eye_pie_chart.svg" alt="Eye color bar chart of 1000 data points using proportions.">
<figcaption> A pie chart showing frequencies of eye colors for 1000 respondents.</figcaption>
</figure>

If you were to draw a pie chart by hand, the difficulty would be determining how big to make each radial region.  The trick is to make the angle match the relative frequency of the value.  For example, if a value were to have a relative frequency of 0.5, then it should take up half of the circle, and half of the circle is $360^\circ\div 2 = 180^{\circ}$.  In general 360 times the relative frequency gives the angle of the region.

<figure class="center">
<img class="center" src="{{imgdir}}/eye_pie_chart_angle.svg" alt="Eye color bar chart of 1000 data points using proportions.  The angle of the brown region is shown.">
<figcaption> The brown region has a relative frequency of $\frac{743}{1000}$ so it's angle is  $\frac{743}{1000}\cdot 360^\circ=267.48^{\circ}$ .</figcaption>
</figure>

In the above figure, the brown region has an absolute frequence of 743 out of 1000 data points.  This means that its relative frequency is $743\div1000=0.743$.  So the angle in degrees for the brown region on the pie chart is calculated as $360^\circ\cdot743 = 267.48^\circ$.

## Time Series Data
An important type of data, which tracks how a (numerical) quantity changes over time is called **time series data**.  Some examples of time series data include:
* A child's height is recorded at each doctor's visit.
* A company records its sales every month or year.
* The total US population is recorded every ten years in a census.
* A stock's value is recorded at the end of every trading day.

For all of these examples, there is some quantity changing over time.  In all of these examples, there is some time between measurements so the data is **discrete** and **numerical**.  If the time between data points is sufficiently small, as is possible for stock prices, it may be viewed as continuous data, but this is rare.

One way to think about time series data is that it's the same as any other data except that time at which the data was collected becomes the "subject id."  We don't throw that data out because it gives us valuable information.  Here's some time series data tracking the wins per season for the Florida Gators football team over the past 20 years.

| Year | \# Wins | Year | \# Wins |
|:----:|:-------:|:----:|:-------:|
| 2003 | 8       | 2013 | 4       |
| 2004 | 7       | 2014 | 7       |
| 2005 | 9       | 2015 | 10      |
| 2006 | 13      | 2016 | 9       |
| 2007 | 9       | 2017 | 4       |
| 2008 | 13      | 2018 | 10      |
| 2009 | 13      | 2019 | 11      |
| 2000 | 8       | 2010 | 8       |
| 2011 | 7       | 2021 | 6       |
| 2012 | 11      | 2022 | 6       |

We could treat this data the same as the eye color data.  That is, we throw away the identifier for each data point (the year in this case) and just plot the frequency.  We show the frequency table and resulting bar chart below.

<div class="row">
<div class="colsmall" markdown="1">

| \# Wins | Frequency |
|:-------:|:---------:|
| 4       | 2         |
| 6       | 2         |
| 7       | 3         |
| 8       | 3         |
| 9       | 3         |
| 10      | 2         |
| 11      | 2         |
| 13      | 3         |

</div>
<div class="collarge">
<img class="center" src="{{imgdir}}/uf_wins_bar.svg" alt="Frequency of UF Victories.">
</div>
</div>
The above visualization throws away useful information.  In general, one is more interested in trends of time series rather than frequency data.  More useful visualizations will keep the time data and use it as a label on the horizontal axis of the chart.  The values become labels on the vertical axis.  From there either bars or lines can be used to show the trend.  When the values are connected with lines, the result is called a **line graph**.  When the bar graph is plotted with bars it is called a **time series bar chart**.

<div class="row">
<div class="column">
<img class="center" src="{{imgdir}}/uf_wins_bar_time.svg" alt="Time Series of UF Football Victories.">
</div>
<div class="column">
<img class="center" src="{{imgdir}}/uf_wins_line.svg" alt="Time Series of UF Football Victories.">
</div>
</div>

The figures above show the exact same data both as a time series bar chart and as a line graph.

# Working With Continuous Data

The primary difficulty of continuous data is that frequency is essentially meaningless.  Suppose that you had a data set consisting of people's heights.  As this is continuous data, that means that you are measuring *exactly*, not just rounding to the nearest millimeter.  It's extremely unlikely that two people have exactly the same height.

The solution to this issue is to turn the continuous data into categorical, discrete data.  Practically speaking, we do this all the time.
* When discussing school grades, we end up not caring about the exact score.  Instead we categorize them by letter grades.
* Most shoe brands do not care about the exact size of your feet.  Instead they categorize all foot sizes by shoe size.
* Age is never measured down to the millisecond.  We may measure an infant's age in terms of days or weeks, but by the time we are adults we tend to only care about our age in years.

In truth, we almost never care about the exact value for continuous data, and we pass to categorical data for analysis.

## Histograms

On particular way of dividing continuous (or suitably dense discrete) data into categorical data is by dividing the values into intervals.  A **histogram** is a bar chart made out of frequency data from the intervals.  It's easiest to think about this with an example.  Below, we have some fake exam score data from 100 imaginary students.

<table class="datatable">
<tr>
    <td>72.3</td> <td>69.2</td> <td>75.2</td> <td>80.6</td> <td>74.5</td> <td>83.9</td> <td>74.5</td> <td>68.6</td> <td>96.5</td> <td>93.4</td> 
</tr>
<tr>
    <td>63.5</td> <td>66.3</td> <td>66.7</td> <td>78.6</td> <td>75.9</td> <td>67.4</td> <td>68.2</td> <td>73.2</td> <td>70.2</td> <td>79.8</td> 
</tr>
<tr>
    <td>83.2</td> <td>77.4</td> <td>64.8</td> <td>84.9</td> <td>50.7</td> <td>66.2</td> <td>61.8</td> <td>77.8</td> <td>67.1</td> <td>56.6</td> 
</tr>
<tr>
    <td>68.1</td> <td>71.6</td> <td>54.4</td> <td>59.1</td> <td>48.8</td> <td>68.4</td> <td>71.0</td> <td>77.3</td> <td>84.7</td> <td>88.9</td> 
</tr>
<tr>
    <td>63.7</td> <td>69.5</td> <td>70.3</td> <td>85.5</td> <td>70.0</td> <td>63.7</td> <td>70.6</td> <td>74.1</td> <td>77.9</td> <td>81.9</td> 
</tr>
<tr>
    <td>53.0</td> <td>77.2</td> <td>61.1</td> <td>65.4</td> <td>76.5</td> <td>80.5</td> <td>75.2</td> <td>62.0</td> <td>74.9</td> <td>77.4</td> 
</tr>
<tr>
    <td>88.7</td> <td>72.4</td> <td>74.4</td> <td>56.1</td> <td>69.4</td> <td>66.3</td> <td>62.3</td> <td>66.6</td> <td>72.2</td> <td>62.0</td> 
</tr>
<tr>
    <td>73.4</td> <td>69.1</td> <td>70.9</td> <td>74.9</td> <td>88.9</td> <td>74.2</td> <td>82.3</td> <td>79.1</td> <td>68.8</td> <td>57.4</td> 
</tr>
<tr>
    <td>69.7</td> <td>34.5</td> <td>76.1</td> <td>100.0</td> <td>74.0</td> <td>66.1</td> <td>95.2</td> <td>83.5</td> <td>52.7</td> <td>72.7</td> 
</tr>
<tr>
    <td>69.4</td> <td>78.8</td> <td>67.2</td> <td>63.7</td> <td>69.0</td> <td>79.4</td> <td>82.4</td> <td>61.1</td> <td>72.8</td> <td>69.5</td> 
</tr>
</table>

As you can see, frequency data is not too useful, there are a few 100s, 72.2 is repeated twice, and there are maybe a few other repeats.  But in general, the frequency data does not give much information.  In this imaginary class, grades are assigned on a 10-point scale.  So it makes more sense to classify grades by **intervals**.

<div class="definition">
Given two numbers $a<b$, The <strong>interval</strong> $(a,b)$ consists of all numbers between and not including $a$ and $b$.  If $a$ or $b$ are to be included in the interval, the parentheses can be replaced by braces (e.g. $[a,b)$ or $[a,b]$).  The <strong>width</strong> of an interval is $b-a$ regardless of endpoint inclusion.
</div>

Below, we have the same exam score data classified by what interval it lies in.  A few notes on these intervals.
* The intervals usually have the form $[a,b)$.  This means that the left endpoint is included while the right is not.  For example, the interval $[60,70)$ includes scores of 60 but not 70.
* The final interval, $[90, 100]$ includes both endpoints.

<div class="row">
<div class="colsmall" markdown="1">

| Interval    | Frequency |
|:-----------:|:---------:|
| $[40, 50)$  | 1         |
| $[50, 60)$  | 8         |
| $[60, 70)$  | 34        |
| $[70, 80)$  | 38        |
| $[80, 90)$  | 14        |
| $[90, 100]$ | 4         |

</div>
<div class="collarge">
<img class="center" src="{{imgdir}}/exam_score_hist.svg" alt="Histogram of exam scores.">
</div>
</div>

When dividing the data into intervals for data analysis, we call the intervals **class intervals**.  There are some rules for how we divide the data range into class intervals.
1. **Class intervals must not overlap**.  The typical way to accomplish this is using intervals of the form $[a,b)$ with the last being $[a,b]$ as above.
2. **The width of each interval should be the same.**  If intervals have different widths, then the frequency data is confusing.

## Learning Objectives
* Differentiate between continuous and discrete data.
* Differentiate between numerical and categorical data.
* Construct a frequency table for discrete data.
* Construct a histogram for continuous or sufficiently dense discrete numerical data.
