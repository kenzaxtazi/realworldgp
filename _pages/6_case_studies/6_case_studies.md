---
permalink: /case_studies/
title: " 6. Case studies"
layout: archive
sidebar:
  nav: "sidebar"
redirect_from:
- /case_studies/
- /case_studies.html
---

The following section describes implementation details of four case studies. The case study code is in implemented in `GPytorch` and `GPflow` with all the code executable from `Jupyter` notebooks.

## 6.1. Glacier elevation change (GP interpolation)

The framework is applied to the case study glacier elevation over Greenland using data derived from ICESat and ICESat-2 satellites. In this regression problem, we would like to estimate glacier elevation change at unsampled locations. Ocean distance, topographic elevation, slope, aspect, surface glacier velocity, and spatial coordinates $x$-$y$ are used as inputs ($D=7$). The dataset is also large with $N=5\times10^5$. We compare the framework with a pre-existing application of GPs to this [problem](https://ui.adsabs.harvard.edu/abs/2019AGUFM.C41A..08G).

[Part I: Problem definition](6_case_stdies/glaciers_gpframe_s1s4.html) \
[Part II: Data exploration]() \
[Part III: Model iteration]() \
[Part IV: Scaling and testing]()

## 6.2. Himalayan precipitation (GP extraloplation)

The aim of this case study is to predict future precipitation in the Upper Indus Basin, Himalayas. We use ERA5 climate reanalysis data and historical atmospheric indices (derived from observations). The data has 1,185,840 data points $N$, 29 possible input dimensions $D$.

[Part I: Problem definition]() \
[Part II: Data exploration]() \
[Part III: Model iteration]() \
[Part IV: Scaling and testing]()

## 6.3. Lorenz 96 model (Multi task GP)

In this case study, we apply multi-task GP to learn the physical relationships between dimensions of the Lorenz 96 model in order to forecast future behaviour. The Lorenz 96 model is often used as simpler proxy for climate model as it can recreate the chaotic patterns observed in the atmosphere. The dataset is large with $N=399,601$, $D=1$ and $M=8$

[Part I: Problem definition]() \
[Part II: Data exploration]() \
[Part III: Model iteration]() \
[Part IV: Scaling and testing]()

## 6.4. Ocean turbulence regimes (Classification)

[Part I: Problem definition]() \
[Part II: Data exploration]() \
[Part III: Model iteration]() \
[Part IV: Scaling and testing]()

## 6.5. Further reading

Below are further examples of GPs studies (with code) that deal with scalibity and kernel design for real world problems.
