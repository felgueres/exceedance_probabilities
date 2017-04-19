# Applied Statistics in Solar Energy: Exceedance Probabilities

This post goes through the underpinnings of Exceedance Probabilities and the benefit solar energy developers and enthusiasts alike stand by knowing the basics.

Exceedance Probabilities in the context of solar energy are also referred to as P50/P90 analysis or simply, P values. Among banks and investment firms it's the staple statistical method to determine the economic risk associated with solar resource uncertainty.

Objectively, a P50/P90 analysis determines the likelihood that a solar plant will yield an specific amount of energy (ie. dollars) during any given year of its life. For this reason, exceedance probabilities are paramount for a solar project to a) secure competitive financing and, b) manage operational costs and debt obligations.

So, what exactly are they?

### P as in Probability

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

All else equal, yearly outputs are mainly driven by the weather conditions at the project's site. Let's not forget, the goal is to understand this variability and determine the asset expectations on a year-to-year basis.

From an statistics standpoint, we do this by fitting the historical dataset to a function we understand in order to make inferences from it.

In other words, we calculate P values through a two step process:

      1) Fit the previously simulated yearly plant outputs to a distribution function and,

      2) Calculate a desired P value derived from the function properties.


### Example

Consider a fictional 10 MW utility-scale plant somewhere in California, let's call it 'El Nopal'.

I've simulated yearly energy outputs for a 1998-2015 dataset at 'El Nopal', see results in the following table:

Show table (Table 1)

Plotting a histogram will show how the energy outputs are distributed, or, the density of our sample.

SHOW FIG. Histogram

The most typical path going forward is to assume the data follows a Normal Probability Distribution (see Wikipedia) and to calculate its Cumulative Form. This is a nice idea if the data was normally distributed, however, that's arguably not the case with solar resource.
Across a 20-30 year life of a solar project, outlier events such as cyclic weather patterns or volcanic eruptions may skew the data (in our example we potentially have one!).

An alternative approach is to not assume any particular distribution and build one directly from the data. Particularly, we want to build an Empirical Cumulative Density Function.

For illustration purposes, I will calculate the Exceedance Probabilities with both methods and expose why understanding the difference matters.

Let's assume we are using the standard distribution first.
This approach is simple since we know what the function looks like (see Wikipedia). Note it takes two parameters to model, the Mean and Standard Deviation of the dataset.

For our hypothetical plant, this is what it looks like with a mean of X and a Standard Deviation of Y.

Show figure of Cumulative Density Function (fig.2)

To interpret this plot, take the red dot and it reads:
'The proportion of the simulations with an output greater than 50 is X'.

That's it! We can solve the function to get the proportion of the population (probability) that is greater than any value P.

Let's stop and think about this further.

If you were to invest on a solar plant with minimal risk exposure, would you want to calculate your Return of Investment using a high or low P value?

To answer that, notice a P10 value means that the proportion of yearly simulations where the outcome exceeds such value is only 10%. Another way to think about it is that, a P value is inversely proportional to the expected production.

For example a high probability of exceedance, ie. P90, will reference a relatively low production yield. And the reverse is true for low P values.

That is why Financial Institutions and Plant Owners, on both their best interests would plan according to at least the P50 (which is the expected value or mean); the latter makes sure they service debt obligations and manage operational costs, while the former reduces risk of borrower's default.

### Empirical CDF

Now, let's take a look to the Empirical procedure.

Take our hypothetical plant and dataset, there are 18 years, 18 production values.

Each value constitutes an equal contribution of the total probability or 1 / 18.

Since the distribution is cumulative, we want to sort the values (lowest to highest), and do a cumulative sum of the total contribution at each consecutive data point. The procedure is shown below:

Show Table 2 -- Empirical CDF calculation

With that, we are ready to plot.

Plot 3 -- empirical methods plot

In contrast to the first method, we obtain specific P values by performing linear interpolation.

For example, a P90 value can be computed by interpolating between the values in the table for which the Cumulative Density is equal to 0.1. This is crucial since it means we need as many data points as possible to establish a representative cumulative curve and by consequence, reliable exceedance probabilities.

So, this curve tells us a slightly different story than our first method.

Plot 4 -- Combine both plots.

Comparing both methods:

Table 3. Differences

X for 1
Y for 2

Let's take the outlier year as an example. Under the normal method.
Fitting an empirical distribution would yield more realistic estimates.
However, new datasets are becoming available and it's time to reconsider.

And notice that the mean of the distribution is equivalent to the P50 value.

### About me:

I'm a Data Scientist at Enertis, a consulting firm advising developers, banks and investment funds on solar energy systems.

Applied statistics and predictive modeling, utilizing time-series field data to isolate and overcome fleet performance issues.
