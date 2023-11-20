---
permalink: /framework/5_scaling_sctructures/
title: "4. Framework"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /framework/5_scaling_sctructures
- /framework/5_scaling_sctructures.html
---

## Step 5: Scaling structures

When working with a large dataset, the modeller should also analyse the training data to find structure that may lead to the application of scaling methods. Three cases and how to identify them are discussed below.

* __Case 1__: Oversampled functions. An oversampled function is sampled more frequently than is required to capture its underlying structure and variation. In the case of a periodic function this would be more than the Nyquist frequency. In this situation, the modeller can use sparse GP regression with variational inference of inducing points ([Titsias, 2009](https://proceedings.mlr.press/v5/titsias09a.html)). Many GP libraries, such [`GPflow`](https://gpflow.org) or [`GPyTorch`](https://gpytorch.ai), offer built-in functions to perform this approximation.
* __Case 2__: Timeseries data. For timeseries data, the GP can be mapped to a Stochastic Differential Equation (SDE) ([Hartikainen, 2010](https://ieeexplore.ieee.org/document/5589113)). This approximation has a linear cost in the number of time points and works well in many situations. However the mapping between the covariance matrix and the SDE can be expensive, sometimes more expensive than solving SDE itself. [`TemporalGPs.jl`](https://github.com/JuliaGaussianProcesses/TemporalGPs.jl), a package Julia, provides a framework to apply this method.
* __Case 3__: Kronecker product structure. For such dataset with the following kernel structure, such as gridded data:

    $$\text{Cov}\biggl(\begin{bmatrix} x_1 \\ x_2  \end{bmatrix} \begin{bmatrix} x_1^{\prime} \\ x_2^{\prime}\end{bmatrix} \biggl)=\text{Cov}(x_1,x_1^{\prime} )\otimes \text{Cov}(x_2,x_2^{\prime}),$$

    the Kronecker identity can be used to invert the matrices in a piecewise fashion ([Saatcci et al., 2012](https://mlg.eng.cam.ac.uk/pub/pdf/Saa11.pdf)). This trick is used in the Structured Kernel interpolation (SKI) ([Wilson and Nickish, 2015](https://proceedings.mlr.press/v37/wilson15.html)). Both SKI and SKIP are implementable in [`GPyTorch`](https://gpytorch.ai).

If no structure is apparent, a baseline that is hard to beat is to the divide the data into smaller datasets, as previously mentioned. This can be done naively by separating data chronologically or into tiles. However, it can be useful to make use of clustering algorithms, such as k-means or k-nearest neighbours, to group features that exhibit similar properties.
