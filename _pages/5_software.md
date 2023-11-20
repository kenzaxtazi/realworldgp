---
permalink: /software/
title: "5. Software"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /software/
- /software.html
---

__This section needs a more content and systemic analysis of the different options. A table would be nice too. Please feedback if you think I am missing any obvious software packages here.__

In the last few years, a number of packages to perform GP regression and classification have been developed in Python and Julia. In this section, we discuss the advantages and drawbacks of seven open-source packages. The packages are compared using five characteristics: beginner friendliness, customisability, community, scalability, and intuitiveness. We focus mainly on how the software can be applied to exact inference but also discuss possible extensions to approximations methods.

[`scikit-learn`](https://scikit-learn.org/stable/index) is a comprehensive Python library for predictive data analysis. It provides a number of simple tools for exact GP regression and classification, and is a good place for GP novices to start. The library comes with lots of documentation and large community.

[`GPy`](http://sheffieldml.github.io/GPy/) is also a Python based library. It is more customiseable than `sklearn` but still more beginner friendly than `GPflow`. The modeller can use non-Gaussian likelihoods, apply sparse and variational approximation during inference and deploy multi-output GPs. There is scope to write custom kernel but the documentation is rather limited with most of it being written as notebooks.

[`GPFlow`](https://gpflow.org) builds on Tensorflow. The documentation is good and the library has many in-built variational approximations.

[`GPyTorch`](https://gpytorch.ai) builds on Pytorch. The main difference with `GPFlow` is that `GPyTorch` provides GPU scaling. The documentation has steadily improved in recent years and the library has many built-in  variational approximation schemes and specialised solvers. Although the GP models are very customiseable, they are less intuitive to build than in the previously presented libraries.

[`GPJax`](https://docs.jaxgaussianprocesses.com) is a didactic GP library that also supports GPU acceleration and just-in-time compilation in Python. The authors seek to provide a flexible API as close as possible to how the underlying mathematics is written on paper to enable researchers to rapidly prototype and develop new ideas. `GPJax` also allows graph inputs.

[`stheno`](https://github.com/wesselb/stheno) is an implementation of GP modelling in Python and Julia.  Similar to `GPJax` is an mathematically intuitive library but run by a small community. The Python library can be built on Tensorflow and PyTorch, therefore lends itself to, in the latter case, to more GPU scalability.

[`GaussianProcesses.jl`](https://stor-i.github.io/GaussianProcesses.jl/latest/) is Julia based software package. It has many of the features of the other packages of other packages with the exception of multi-output GPs and GPU scaling.

Other noteworthy software libraries include and `Stan MCMC` (Python), `PyMC` (Python), `GPML` (MATLAB), and `GP Stuff` (MATLAB and R).
