# Background
A recent improvement of Stairway Plot 2 for demographic inference, using posterior predictive Bayesian implementation in
https://onlinelibrary.wiley.com/doi/abs/10.1111/1755-0998.14087

The Stairway Plot framework (v1 & v2) estimates population size changes through time using the site frequency spectrum (SFS).
The original method was frequentist, because it uses maximum likelihood estimation and bootstrap (resampling SNPs) to measure uncertainty.

#Its CI shows where 95% of those fits fall.

#It cannot say “there’s a 95% chance Ne is between these values”; it only says “if I repeated sampling.

#It cannot incorporate prior information about demographic smoothness or expected changes.

# Why test Bayesian models?
Bayesian inference (likelihood + prior) lets you treat unknowns (e.g. historical population sizes at each time interval) as random variables with priors — 
so we can regularize, compare models, and quantify uncertainty properly.

#Testing different Bayesian models allows us to ask:

“What kind of prior belief about demographic change best explains the SFS, without overfitting or losing resolution?”


#Model regularization and flexibility

Compare prior models for the population-size trajectory Ne(t): e.g.,

1). i.i.d. prior: population sizes vary freely (too flexible, risk of overfitting)

2). Gaussian Markov random field (GMRF): enforces smoothness across time

3). Horseshoe (HSMRF) prior: allows most changes to be smooth but a few sharp (abrupt bottlenecks)


#Testing these tells you which regularization yields biologically realistic, data-supported histories.

The Bayesian Credible intervals shows where 95% of posterior probability lies.
It means “given data + prior, there’s a 95% probability Ne(t) lies in this range.”

# Summary
#Testing multiple Bayesian models isn’t just technical fine-tuning is crucial for:

preventing overfitting,

improving reliability,

quantifying uncertainty properly,

and ensuring that inferred demographic histories are data-supported rather than algorithmic artifacts.

# Authors' Tutorial
https://revbayes.github.io/tutorials/stairwayplot/
