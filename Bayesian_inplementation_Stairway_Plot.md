# Background
A recent improvement of Stairway Plot 2 for demographic inference, using posterior predictive Bayesian implementation in
https://onlinelibrary.wiley.com/doi/abs/10.1111/1755-0998.14087

> ![Demographic histories estimated using our Bayesian StairwayPlot approach with different prior models for the big European firefly.](https://github.com/user-attachments/assets/f13bb6d7-6511-47a7-b141-c4c8776d983a)
> _**Demographic histories estimated using the Bayesian StairwayPlot approach with different prior models for the big European firefly**_



The Stairway Plot framework (v1 & v2) estimates population size changes through time using the site frequency spectrum (SFS). \
The original method is frequentist, because it uses maximum likelihood estimation and bootstrap (resampling SNPs) to measure uncertainty.\
It tries demographic models with different numbers of change points (stairs), then picks the one minimizing a penalized likelihood (e.g., AIC-like criterion).

_Its CI shows where 95% of those fits fall._ \
_It cannot say “there’s a 95% chance Ne is between these values”, but it only says "if I repeated sampling"._\
_It cannot incorporate prior information about demographic smoothness or expected changes._

# Why test Bayesian models?
Bayesian inference (likelihood + prior) lets you treat unknowns (e.g. historical population sizes at each time interval) as random variables with priors — 
so we can regularize, compare models, and quantify uncertainty properly.

**Testing different Bayesian models allows us to ask:**\
_What kind of prior belief about demographic change best explains the SFS, without overfitting or losing resolution?_
_How much prior biological knowledge (e.g., smoothness, bottleneck rarity) should influence the model?_
_Which demographic trajectory is most probable given the data and prior beliefs?_

**Model regularization and flexibility**\
Compare prior models for the population-size trajectory Ne(t): e.g.,\
_1). i.i.d. prior: population sizes vary freely (too flexible, risk of overfitting)_\
_2). Gaussian Markov random field (GMRF): enforces smoothness across time (constant or gradual change)_\
_3). Horseshoe (HSMRF) prior: allows most changes to be smooth but a few sharp (abrupt bottlenecks)_

**Testing these tells you which regularization yields biologically realistic, data-supported histories.** \
The Bayesian Credible intervals shows where 95% of posterior probability lies. \
It means “given data + prior, there’s a 95% probability Ne(t) lies in this range.”

# Summary
**Testing multiple Bayesian models isn’t just technical fine-tuning is crucial for:**\
_preventing overfitting_\
_improving reliability_\
_quantifying uncertainty properly_\
_ensuring that inferred demographic histories are data-supported rather than algorithmic artifacts_

# Authors' Tutorial
https://revbayes.github.io/tutorials/stairwayplot/

# Installation
https://revbayes.github.io/compile-linux

Download RevBayes from our github repository. Clone the repository with ```-branch dev_stairwayplot2``` using git by running the following command in the terminal:

**Do not use this appeared in above authors' Tutorial (side branch is not merged by default ```dnStairwayPlot```)**

```git clone --branch development https://github.com/revbayes/revbayes.git revbayes```

**Use below with ```-branch dev_stairwayplot2``` advised by the developer, which is essential for running ```?dnStairwayPlot``` later**
```
git clone --branch dev_stairwayplot2 https://github.com/revbayes/revbayes.git revbayes
```
To compile with the system boost:
```
cd revbayes/projects/cmake
./build.sh
```
To compile revbayes using a locally compiled boost, do the following. Be sure to replace the paths in the build command with those you got from boost in the previous step.
```
./build.sh -boost_root /path/to/installed-boost-1.88.0
```
**Add the directory in which you compiled RevBayes to the system path:**
```
export PATH=<your_revbayes_directory>/projects/cmake:$PATH 
```
# Run program
In terminal or on server
```
rb
```

