# Bayesian-Parameter-Optimization #

This is a constrained global optimization package built upon bayesian inference and gaussian process, that attempts to find the maximum value of an unknown function in as few iterations as possible. This technique is particularly suited for optimization of high cost functions, situations where the balance between exploration and exploitation is important.

## Installation ##
The latest release can be obtained by two ways:
* PyPI (pip):

`$ pip install bayesian-optimization`
* Conda from conda-forge channel:

`$ conda install -c conda-forge bayesian-optimization`

## Dependencies ##
* NumPy
* Scipy
* Scikit-learn

## Quick Overview ##
For a quick overview of the Bayesian Optimization package, the jupyter notebook [Bayesian_optimization_case_study](https://github.com/martell-n-tardy/Bayesian-Parameter-Optimization/blob/main/Bayesian_optimization_case_study.ipynb) provides an detailed example of the package's most important features.

## How does it work? ##
Bayesian optimization works by constructing a posterior distribution of functions (gaussian process) that best describes the function you want to optimize. As the number of observations grows, the posterior distribution improves, and the algorithm becomes more certain of which regions in parameter space are worth exploring and which are not, as seen in the picture below.

![picture alt](https://github.com/martell-n-tardy/Bayesian-Parameter-Optimization/blob/main/bo_example.png)

As you iterate over and over, the algorithm balances its needs of exploration and exploitation taking into account what it knows about the target function. At each step a Gaussian Process is fitted to the known samples (points previously explored), and the posterior distribution, combined with a exploration strategy (such as UCB (Upper Confidence Bound), or EI (Expected Improvement)), are used to determine the next point that should be explored (see the gif below).

![picture alt](https://github.com/martell-n-tardy/Bayesian-Parameter-Optimization/blob/main/bayesian_optimization.gif)
This process is designed to minimize the number of steps required to find a combination of parameters that are close to the optimal combination. To do so, this method uses a proxy optimization problem (finding the maximum of the acquisition function) that, albeit still a hard problem, is cheaper (in the computational sense) and common tools can be employed. Therefore Bayesian Optimization is most adequate for situations where sampling the function to be optimized is a very expensive endeavor. See the references for a proper discussion of this method.

This project is under active development, if you find a bug, or anything that needs correction, please let me know.

## Citation ##
If you used this package in your research and is interested in citing it here's how you do it:

    @Misc{,
        author = {Martell Tardy},
        title = {{Bayesian Optimization}: Open source constrained global optimization tool for {Python}},
        year = {2021--},
        url = " https://github.com/Bayesian-Parameter-Optimization"
    }
