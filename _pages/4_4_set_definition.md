---
permalink: /framework/4_set_definition/
title: "4. Framework"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /framework/4_set_definition
- /framework/4_set_definition.html
---

## Step 4: Training, validation and test set definition

A held out dataset allows the modeller to check whether they are under or overfitting, and to give some indication of the performance they would get on `real' unseen data. The separation of the data should reflect the goals and the performance they want to measure in Step 1, and information from Step 3. Ideally the dataset should be separated into three groups: a training set, a validation set, and a test set which will not be iterated over. In many cases, the data is used in real-world is not i.i.d., it is dependent and  correlated, and come from heterogeneous sources and samplings regimes. If the effective number of data points (the number of independent samples that would be needed to produce the same information content as the given sample) is fairly small, then a cross-validation scheme is strongly recommended to assess the stability and predictability of the model ([Yu and Kumbier, 2020](https://arxiv.org/abs/1901.08152)).
