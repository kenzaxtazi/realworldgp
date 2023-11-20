---
permalink: /framework/7_kernel_design/
title: "4. Framework"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /framework/7_kernel_design
- /framework/7_kernel_design.html
---

## Step 7: Kernel design

In this step, the modeller explores the dataset in order to design the kernel function. To compose a kernel, the following characteristics of the target variable should be considered: smoothness, lengthscales, periodicity, outliers and tails, asymmetry, and stationarity. Tools such as first and second order statistics, scatter plots (with low dimensional projections), covariance and correlation matrices, autocorrelation plots, power density spectrum, and k-Nearest Neighbour analysis can be used to find these properties. The modeller should exercise their common sense when applying these tests keeping in mind the task they are trying to solve, as defined in Step 1. They should also view this exercise as hypothesis testing and ascertain if the characteristics of the dataset match the domain knowledge, outlined in Step 3, and if not, why.

This step is also important for inference time. The covariance is inverted analytically and, in most cases, Cholesky decomposition is used. However, this method requires the covariance matrix is Hermitian positive definite. This means the decomposition will fail if the one of the input dimensions is linearly related to another or a combination of other inputs. In practice, many GP models are set to have a zero mean function $\mu(\bm{x})$. However, the stability of inference can also be improved by modelling the most obvious features of the dataset through $\mu(\bm{x})$ the rather than $k(\bm{x}-\bm{x}^{\prime})$.

Now that we have a clear understanding of the data. We can design the kernel function through `kernel composition'. The kernel can be built by combining standard operators and base kernel functions \citep{duvenaud2014construction}. Adding is equivalent to applying the logical operator ‘OR’, i.e.~changes in the amplitude can be explained by either term in the sum. For example, the resulting kernel will have high value if either of the two base kernels have a high value. Multiplying is similar to an ‘AND’ operation, i.e.~changes in the amplitude are explained by both term in the multiplication. For example, the kernel will have high value if both base kernels have a high value. It's worth noting that multiplying kernels can result in a lower-dimensional representation of the data, simplify eigenvalue decomposition, result in a sparse matrix, and allow for pre-computation, thus making this procedure a computationally efficient way to combine with kernels. The design of the kernel will first and foremost affect the smoothness of the samples. The modeller can enforce this by choosing the smoothness of the mean and covariance functions. This is in particular useful for modeling data with underlying structures, such as financial time series data or image data.

If the model does not initially converge close the lengthscales values determined previously. They can be initialised manually. If this still does not change where the model converges, strong guidance can be applied through constraints and priors. In real-world cases, including such specifications are not uncommon to achieve the desired results. These include:

* __Boundary constraints__. The modeller enforce boundary constraints on the model parameters, such as bounds on the mean function parameters or variance and lengthscale of the kernel function. This can be useful when modeling physical processes that have known limits or constraints. In practice, using constraints may be difficult. If they do not match the observations, the model can break down. It is usually better to have small and positive priors (see next point).
* __Bayesian priors__. The model incorporate prior knowledge about the parameters of the model using priors distributions. For example, a Gaussian prior can be placed on the parameters of the covariance function to encourage the model to converge to a particular solution.
* __Constraints on the covariance function__. The modeller can enforce constraints on the covariance function, such as stationarity or monotonicity. These constraints can help to ensure that the model has physically meaningful properties.

Note that kernels with many hyperparameters will be more likely to overfit the data. Furthermore, recent literature suggests that even when a large number of terms are used, only a few parameters drive the outputs of the model after inference ([Lu, Boukouvalas and Hensman, 2022](https://proceedings.mlr.press/v162/lu22b.html)). Regularisation techniques can be applied to the kernel function to limit overfitting ([Cawley and Talbot, 2007](https://www.jmlr.org/papers/v8/cawley07a.html)) but are usually quite involved to put in place. %The kernels could also be modified put more emphasis on different parts of the marginal distribution such as extremes.
