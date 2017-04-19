# Applied Statistics in Solar Energy: Invest on P90.

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

# Simulated Yearly Energy Ouputs [GWh]
1998 |1999 |2000 |2001 |2002 |2003 |2004 |2005 |2006 |2007 |2008 |2009 |2010 |2011 |2012 |2013 |2014 |2015
----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:|----:
16.62|17.87|17.66|17.95|17.96|17.49|17.94|17.41|17.60|18.12|18.15|17.87|17.29|17.71|18.28|18.38|18.39|18.03
