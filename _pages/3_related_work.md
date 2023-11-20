---
permalink: /related_work/
title: "3. Related work"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /related_work/
- /related_work.html
---

Research focused on overcoming the limitations of GPs is vast, from improving scalability ([Liu et al., 2020a](https://arxiv.org/pdf/1807.01065.pdf)), to overcoming the model selection problem ([Liu et al., 2020b](https://proceedings.neurips.cc/paper/2020/hash/f52db9f7c0ae7017ee41f63c2a7353bc-Abstract.html); [Simpson et al., 2021](https://arxiv.org/abs/2106.08185)). However, these methods are usually not beginner-friendly and in most cases applied to clean and well-studied benchmark datasets. Previous work on the democratisation of GPs is centred around creating an Automatic Statistician ([Steinruecken et al., 2019](https://link.springer.com/chapter/10.1007/978-3-030-05318-5_9)) which takes in data and outputs results and a model fit in natural language. This framework builds on Automated Bayesian Covariance Discovery ([Lloyd et al., 2014](https://ojs.aaai.org/index.php/AAAI/article/view/8904)) which uses the Bayesian Information Criterion to brute force the design of sensible kernel function. However, this endeavour sets aside one of the main advantages of GPs: incorporating prior knowledge. It also does not educate modellers about how to use GPs and therefore properly interpret their results.

Instead, our work follows a similar structure to other data science and machine learning guidelines with supporting code and examples to empower the deployment of GPs in the real world ([Yu and Kumbier, 2020](https://arxiv.org/abs/1901.08152); [Bell et al., 2022](https://arxiv.org/abs/2206.05985)).
