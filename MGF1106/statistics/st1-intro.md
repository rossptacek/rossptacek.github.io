---
layout: page
title: "ST1: Introduction"
---

{% assign basedir = site.url| append: "/MGF1106/statistics" %}
{% assign imgdir = basedir| append: "/images" %}

# Statistics

Statistics is the study of how patterns in data can be used to infer broader trends.  If you browse the news, you will be bombarded with statistical claims.  You will read about which candidate is favored in the upcoming election, which dietary choices will make you live longer, the efficacy of medical treatments, and the list goes on.  The primary issue that we face with statistics is that so often we are only exposed to a clickbait headline which is a gross oversimplification of the statistical procedure.  The result is an inability to distinguish between good and bad statistics and a general mistrust of all statistical claims.

Take for example a simple opinion poll which claims one candidate has a lead over another.  The headline might read "X leads Y by 4 points among registered voters."  There is so much information missing from the headline that it is essentially worthless.  Certainly not all registered voters were polled.  Who *was* polled?  Are their answers representative of all registered voters?  Are registered voters representative of who will actually vote come the election?  If we click on the article we might find a margin of error for the poll.  How should we interpret the margin of error in terms of likelihood that the poll is correct?

In this unit, we will become better consumers of statistical claims by investigating the main ways that statistics can be misleading.  We will consider issues both with how data is collected and how the collected data should be interpreted.

## Populations and Samples
All questions in statistics start with a **population**, a collection of individuals or objects to study.  When we study the population, there is some question that we wish to answer.  Typically, these are questions of proportions or averages, but anything is OK as long as it takes the entire population into account.  Here are some examples.
* Given a population of students, we may wonder what the average GPA of the student body is.  Note that the average is a type of measurement which takes everyone's GPA into account.
* Given a population of people in general, we may wonder what the most common eye color is.  Again, we need to take the whole population's eye color into account in order to answer this accurately.

<div class="definition">
A <strong>census</strong> is when an entire population is measured.  A <strong>parameter</strong> of a population is any calculation made from the results of the census.
</div>

In a pefect world, we would take a **census** of the population in order to determine parameters of the population.  Returning to the previous examples.
* To find the average GPA, we would record each student's GPA.  This is the measurement taken by the census.  Then to produce the parameter, the average GPA, we would take the average of the recorded GPAs.
* To find the most common eye color, we would record each person in the population's eye color in the census.  Then to produce the parameter, the most common eye color, we would just see which color was recorded most frequently.

The fundamental problem that statistics aims to solve is that censuses are often times impossible.  When the population is large it is impossible to gather everyone's measurement to aggregate them.  We have to settle for measuring a subset of the whole population, and doing our best to guess what the measurement of the whole population would be.
<div class="definition">
A <strong>sample</strong> is a subset of population is measured.  A <strong>survey</strong> is a measurement of the sample, and a <strong>statistic</strong> of a the sample is any calculation made from the results of the census.
</div>

Surveys and statistics are analogous to censuses and parameters except that they apply to a sample rather than the entire population.

| | Population | Sample |
| :---: | :---: | :---: |
| Who? | Everyone | Some |
| Gathering Data | Census | Survey |
| Computation from Data | Parameter | Statistic |

Since the parameter is often impossible to measure, the fundemental question is how infer parameters from statistics.  This is why the discipline is called "Statistics".  Here is an example of how these terms are used.

<div class="example" text="Average GPA" markdown="1">
Anna is a college student who wonders what the average GPA of a student at her university is.  Once Anna has made this decision, we know the population and parameter.
* The **population** is the students at Anna's school, and
* The **parameter** is the average GPA.

Since it's not feasible to ask every student their GPA (take a **census**), Anna plans to just ask all of the students in her math class what their GPAs are (give a **survey**) and take the average of their GPAs.
* The **sample** is the students in Anna's math class, and
* The **statistic** is the average GPA of the students in the sample.

Note that this is an exercise in terminology.  We are not making any claims that the average GPA from Anna's class (statistic) is a good estimate for the average GPA of all students at the school (parameter).  Indeed, we'll return to this example a few times to see how Anna's plan is prone to errors.
</div>

### Comparison to Random Processes

Given a population, we can consider the random process which uniformly chooses a member of the population and takes their measurement as a value.  Then measurements of the population become properties of the distributuion.  Then a sample is like running trials of the distribution.  So the question of statistics becomes determining what information we can get about the original distribution if we only have data from running the trials.


### Notation

In the end, when we're doing statistics, we will just be presented with the measurements taken from the sample (or population).  These numbers will be denoted as $x_1, x_2, \dots, x_N$ where $N$ is the size of the sample (or population) that we've taken.  Taken all together these values are called a **data set**.  Unfortunately, a data set is often **not a set** because it might have repeat numbers.  Each individual measurement is called a **data point**.

<details class="example" markdown="1">
<summary></summary>

</details>

Example https://www.cnbc.com/2022/05/14/elon-musk-has-wrong-approach-to-count-fakes-spam-on-twitter-experts.html


## Relationn to Probability Theory
Take for example the following random experiment:  A coin is flipped 10 times and the number of heads is recorded.  The data is summarized in a bar chart below.

<figure>
<img src="{{imgdir}}/FlipTrials.svg" alt="Histogram of trials when a coin is flipped 10 times" class="center">
<figcaption> A simulation of an 10000 trials of an experiment where a coin is flipped 10 times.
</figcaption>
</figure>

Here is some information which can be read from the chart.
* 2505 of the 10000 trials had 5 of the 10 flips be heads.
* 10 of 10000 trials had none of the flips be heads.
* 15 of 10000 trials had all 10 coins be heads.

This pattern in the data is predicted by probability theory.  This is a uniform probability distribution, so we just need to count the number of outcomes in the sample space and event.
* The sample space has $2^{10}=1024$ outcomes and ${}_{10} C_5 = 252$ of them will have 5 heads for a probability of $\frac{252}{1024} \approx 0.2461$.  So the probability distribution predicts 2461 of the 10,000 trials will have 5 heads.  This is very close to the 2505 reported in the data!
* Similarly, the probability distribution says the probability of no heads is $\frac1{1024} \approx 0.0010$.  This means that it predicts 10 of the 10000 will have no heads, which happens to be exactly what the data gives.
* Just as with no heads, the distribution predicts 10 of the 10000 trials to have all heads, which is close to the 15 predicted by the data.

This is more than coincidence.  The **law of large numbers** guarantees that as the number of trials grows the proportion of trials will match the probability more and more closely.  Statistics works in the opposite question.  If you start with just some collected data can you work backward to the distribution generated it?  Failing that, can you at least work out some properties of the distribution such as its expectation or standard deviation?

The major complicating factor is that you will **never be able to answer with absolute certainty**.  Any answer will depend on the amount of data present.  If there is only a single data point, you could hardly say anything.  Even with the 10000 data points in the example above, we likely couldn't tell the difference between a fair coin and one that flips heads 51% of the time.  So any answer that we come up with will be stated in the language of probability theory.

## Populations and Samples



<figure>
<img src="{{imgdir}}/USATodayPoll.png" alt="2020 Election Poll" class="center">
<figcaption> An opinion poll from the 2020 presidential election season.  From <a href="https://www.usatoday.com/story/news/politics/elections/2019/03/22/poll-democrats-priority-candidate-to-beat-trump-2020-biden-generates-interest/3220847002/"> USA Today </a> (Accessed 3/4/2022).
</figcaption>
</figure>
