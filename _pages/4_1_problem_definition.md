---
permalink: /framework/1_problem_definition/
title: "4. Framework"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /framework/1_problem_definition
- /framework/1_problem_definition.html
---


## Step 1: Problem definition

As in any data science problem, the first step is to define the task at hand. What kind of predictions would we like to make? Will the model interpolate or extrapolate the training data? What should the model output be (e.g.~a report, one model, an ensemble of models, a forecast, a de-noised timeseries)? Is the output conditional on other variables? For example, the time for a PhD to travel to the Engineering Department will depend on their start location, their mode of transport, the time of day and the time until their thesis submission. In particular, it is important to distinguish between different types of regression. Typically, problems are defined as in [Section 2](2_gp_definition.md) but they could also be posed as an auto-regressive task:
$$ y_t = f(y_{t-1})+ \epsilon_t $$
where $y$ at the variable $t-1$ is used to predict the observation of $y$ at the next $t$. This setup is common for emulation problems where the modeller is interested in replicating the behaviour of a system that is expensive or difficult to study in real life. The type of task which the modeller solves will determine how they design the model(s). For example, forecasting a single time-series along time in the future would mean we want to concentrate on incorporating long term dependencies present in the data. The task also shapes the metrics that should be used at validation and test time: do we care about modelling uncertainties, the mean or the extremes?
