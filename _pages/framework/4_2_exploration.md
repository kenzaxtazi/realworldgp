---
permalink: /framework/2_exploration/
title: "4. Framework"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /framework/2_exploration
- /framework/2_exploration.html
---

## Step 2: Initial data exploration

The next step is to perform an initial exploration of the data in order to understand whether it is suitable for GP regression. One should consider:

* Number of data points $N$. For $N > 10^4-10^5$, exact GP computation becomes prohibitively expensive ([Deisenroth and Ng., 2015](https://arxiv.org/abs/1502.02843); [Wang et al., 2019](https://arxiv.org/abs/1903.08114)). $N < 100$ may be too small especially in the case of a complex kernel with many hyperparameters which can lead to overfitting. Smaller $N$ can be mitigated using Markov Chain Monte Carlo (MCMC) estimation ([McNeish et al., 2016](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwj6mcz6_5OCAxVmUUEAHcHnBToQFnoECBYQAQ&url=https%3A%2F%2Fwww.tandfonline.com%2Fdoi%2Fabs%2F10.1080%2F10705511.2016.1186549&usg=AOvVaw0ZidbH7fi2dLBxWTPctuIB&opi=89978449)).
* Number of input dimensions $D$. GPs are not immune to the curse of dimensionality. For $D > 10$, it is hard for the modeller to form a clear image of the problem. It can therefore also be difficult to design an appropriate kernel. The number of parameters used to define the kernel will also increase, meaning it will be easier to overfit. Furthermore, if $D$ is very large $D>100$, constructing the covariance matrix, which scales as $\mathcal{O}(N^2D)$, can become a computational bottleneck.
* Output requirements. Are probability distributions needed for this task? If the modeller simply requires the mean output an alternative method may be more appropriate.

Further considerations:

* We propose a range of values for the upper limit of $N$. This is because the limit will depend on how the model is used. Higher $N$ can be used for one-off modelling rather than learning hyperparameters through repeated likelihood evaluation.
* Above these limits, it is worth considering the use of a GP as a wrapper for a deep learning model ([Sun et al., 2022](https://hess.copernicus.org/articles/26/5163/2022/hess-26-5163-2022.html)). In this case, a deep learning model can be trained on a large subset of the data. The inputs to the GP can be the output from the deep learning model or their residuals. The GP could also be used to refine the predictions for specific locations in the input feature space using held-out data. This will then yield uncertainties which can be used for uncertainty quantification, active learning, etc.. $^{\dagger}$
* It may be acceptable to work in the top end of the dimension range if only a few dimensions are doing most of the predictive work. Furthermore, it is also possible to select or generate a set of lower dimensional features to feed into the model using decision trees such as Random Forests or dimensionality reduction methods such as Principal Component Analysi ([Binois and Wycoff, 2022](https://arxiv.org/abs/2111.05040)).
* For large datasets (see Step 5), two approaches are possible. In the first case, the data can be divided into chunks, independent GPs or `GP experts' applied are then to each part and predictions are made using a (robust) Bayesian Committee Machine ([Tresp, 2000](https://www.dbs.ifi.lmu.de/~tresp/papers/bcm6.pdf); [Deisenroth and Ng, 2015](https://arxiv.org/abs/1502.02843)}. In the second case and conditional on specific structure, scaling GP methods can be also applied.

$^{\dagger}$ If the models are not trained jointly, the procedure will result in overfitting and the residuals will go to zero with the GP collapsing to 0 uncertainty. If the GP is fit on the training data (and not the just the held-out data) using a neural network will be more likely to result in overfitting since the model might fit the data perfectly even before applying the GP.
