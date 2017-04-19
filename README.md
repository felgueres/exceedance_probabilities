# Applied Statistics in Solar Energy: Why invest on P90?

This post goes through the underpinnings of Exceedance Probabilities and the benefit solar energy developers and enthusiasts alike stand by knowing the basics.

Exceedance Probabilities in the context of solar energy are also referred to as P50/P90 analysis or simply, P values. Among banks and investment firms it's the staple statistical method to determine the economic risk associated with solar resource uncertainty.

Objectively, a P50/P90 analysis determines the likelihood that a solar plant will yield an specific amount of energy (ie. dollars) during any given year of its life. For this reason, exceedance probabilities are paramount for a solar project to a) secure competitive financing and, b) manage operational costs and debt obligations.

So, what exactly are they?

### P as in Percentile

P values refer to the probability that a certain value will be exceeded.
For example, a P90 value of 100, means there is a 90% probability of exceeding 100.

In our context, a P90 of 100 is the likelihood that a solar plant will yield more than 100 units of energy.

Pro-tip: Notice P90 is NOT a 90% probability of producing 100, but of exceeding 100 units (subtle yet very different meaning and a common misunderstanding).

### Methodologies to calculate P values

Dealing with 'uncertainty' and 'statistical methods' may sound intimidating, but once we clear out a few concepts it should be straight forward to grasp.

#### Inputs and High Level

To calculate statistically robust P values of energy estimates we need two inputs:

      1) A long-term historical weather dataset: Using multi-year data assures considering potential worst-case scenarios that could affect a project financial terms.

      2) Performance system modeling: An hourly simulation of the system performance for every single year in the dataset provides the detailed expectations of a system output.

All else equal, yearly outputs are mainly driven by the weather conditions at the project's site. Let's not forget, the goal is to understand that variability and determine the asset expectations on a year-to-year basis.

From an statistics standpoint, we do this by fitting the historical dataset to a function we understand in order to make inferences from it.

In other words, we calculate P values through a two step process:

      1) Fit the previously simulated yearly plant outputs to a distribution function and,

      2) Calculate a desired P value derived from the function properties.


### Example

Consider a fictional 10 MW utility-scale plant somewhere in California.

I've simulated yearly energy outputs for a 1998-2015 dataset at the site, see results in the following table:

## Simulated Yearly Energy Ouputs [GWh]
1998 |1999 |2000 |2001 |2002 |2003 |2004 |2005 |2006 |2007 |2008 |2009 |2010 |2011 |2012 |2013 |2014 |2015
----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:
16.62|17.87|17.66|17.95|17.96|17.49|17.94|17.41|17.60|18.12|18.15|17.87|17.29|17.71|18.28|18.38|18.39|18.03

Plotting a histogram will show how the energy outputs are distributed, or, the density of our sample.

![alt text](https://github.com/felgueres/Exceedance_Probabilities/blob/master/data/01_Histogram_Yearly_Outputs.png "Hist-Yearly-Outputs")

The most typical path going forward is to assume the data follows a Normal Probability Distribution (see Wikipedia) and to calculate Cumulative Form (the integral). This is a nice idea if the data was normally distributed, however, that's arguably not the case with the solar resource.

Across a 20-30 year life of a solar project, outlier events such as cyclic weather patterns or volcanic eruptions may skew the data (in our example we potentially have one!).

An alternative approach is to not assume any particular distribution and build one directly from the data. Particularly, we want to build an Empirical Cumulative Density Function.

For illustration purposes, I will calculate the Exceedance Probabilities with both methods and expose why understanding the difference matters.

Let's assume we are using the standard distribution first.

## Normal Distribution Approach

This approach is simple since we know what the function looks like [(Wikipedia)](https://en.wikipedia.org/wiki/Normal_distribution).
Note it takes two parameters, the Mean and Standard Deviation of the dataset.

For our hypothetical plant, this is what it looks like with the calculated mean and variance.

![alt text](https://github.com/felgueres/Exceedance_Probabilities/blob/master/data/02_Gaussian_Dataset.png "Gaussian-PDF")

### The integral of this curve is the cumulative density function -- what we are interested in.

![alt text](https://github.com/felgueres/Exceedance_Probabilities/blob/master/data/03_Gaussian_CDF.png "Gaussian-CDF")

To interpret this plot, take the P10 value, it reads: **'The likelihood that the plant will yield more than 18.4 GWh is 10%'.**
That's it! We can solve the function to get the proportion of the population (probability) that is greater than any value P.
Let's stop and think about this further.

**If you were to invest on a solar plant with minimal risk exposure**, would you want to calculate your Return of Investment using a high or low P value?
To answer that, notice a P10 value means that the proportion of yearly simulations where the outcome exceeds such value is only 10%. Another way to think about it is that, a P value is inversely proportional to the expected production.

For example a high probability of exceedance, ie. P90, will reference a relatively low production yield. And the reverse is true for low P values.
That is why Financial Institutions and Plant Owners, on both their best interests would plan according to at least the P50 (which is the expected value or mean); the latter makes sure they service debt obligations and manage operational costs, while the former reduces risk of borrower's default.

## Empirical Approach
Now, let's take a look to the Empirical procedure.
Take our hypothetical plant and dataset, there are 18 years, 18 production values.
Each value constitutes an equal contribution of the total probability or 1 / 18.
Since the distribution is cumulative, we want to sort the values (lowest to highest), and do a cumulative sum of the total contribution at each consecutive data point. The procedure is shown below:

|Energy Output [GWh]| Prob  |cumsum
|------------------:|------:|------:
|              16.62|0.05556|0.05556
|              17.29|0.05556|0.11111
|              17.41|0.05556|0.16667
|              17.49|0.05556|0.22222
|              17.60|0.05556|0.27778
|              17.66|0.05556|0.33333
|              17.71|0.05556|0.38889
|              17.87|0.05556|0.44444
|              17.87|0.05556|0.50000
|              17.94|0.05556|0.55556
|              17.95|0.05556|0.61111
|              17.96|0.05556|0.66667
|              18.03|0.05556|0.72222
|              18.12|0.05556|0.77778
|              18.15|0.05556|0.83333
|              18.28|0.05556|0.88889
|              18.38|0.05556|0.94444
|              18.39|0.05556|1.00000

With that, we are ready to plot.

![alt text](https://github.com/felgueres/Exceedance_Probabilities/blob/master/data/04_Empirical_CDF.png "Empirical-CDF")

In contrast to the first method, we obtain specific P values by performing linear interpolation.
For example, a P90 value can be computed by interpolating between the values in the table for which the Cumulative Density is equal to 0.1. This is crucial since it means we need as many data points as possible to establish a representative cumulative curve and by consequence, reliable exceedance probabilities.
So, this curve tells us a slightly different story than our first method:

![alt text](https://github.com/felgueres/Exceedance_Probabilities/blob/master/data/05_PX_Comparison.png "PX-Comparison")

The plot exposes the empirical distribution of an 18-year irradiance dataset deviates at various sections when compared to the calculated normal distribution. For this example, the P90 and P50 values calculated using the normal CDF differs optimistically by 0.6% and -0.3%, respectively.

Take particular note to the deviations on the tail of the distributions. Assuming a normal distribution may lead to arrive to seemingly irrational conclusions, in this example it would suggest that the simulated production for year 1998 has a likelihood of occurring 1 in 330 years.

Invest on P90 from an empirical distribution if possible.
As we've seen, to evaluate a project's financial risk we use P50 and P90 exceedance probabilities based on a multi-year historical dataset. Weather, just as stock and other phenomena is a fat tailed distribution which does not fit to the normal distribution very closely, thus, the empirical methodology yields more reliable results and realistic estimates to manage your plant expectations.
