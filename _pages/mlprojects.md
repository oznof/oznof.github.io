---
layout: fwide
permalink: /mlprojects/
title: "Machine Learning Projects"
author_profile: false
toc: false
classes: wide widel pr
---

## Bayesian Optimization with Informative Covariance
[Paper](https://arxiv.org/abs/2208.02704)  [Slides (June 2022)](/assets/slides/BOIC_ANCWorkshop_June2022.pdf)  [Code](https://github.com/oznof/BOIC)

### Informative Covariance

<p align="center"><img src="/assets/images/BOIC/example_intro.png" alt="Motivating Example" width="800" title="Overconfident models are unable to capture the ground truth, leading BO astray. The stationary model with an informative quadratic mean fits the trend too well, resulting in small residuals. Small residuals lead to a smaller signal variance and a longer lengthscale that drive interpolation uncertainty down everywhere. The stationary assumption posits that signal variance and lengthscale do not change based on location, but it does not hold for functions with irregular bumps. The proposed informative models, being nonstationary, allow the specification of spatially-varying properties."/></p>

A class of informative priors over functions is proposed for optimization with Gaussian process surrogates.
The proposed nonstationary covariance functions encode a priori preferences via spatially-varying prior (co)variances and promote local exploration via spatially-varying lengthscales. Both nonstationary effects are induced by a shaping function that captures information about the location of optima. Experiments show that these informative priors can significantly increase sample efficiency of high-dimensional Bayesian optimization, even under weak prior information. These priors also complement other methods, including trust-region optimization and belief-augmented acquisition functions.

### (Mode-)Collapsed Acquisition Functions

<p align="center"><img src="/assets/images/BOIC/ei_cei.png" alt="Collapsed Expected Improvement" width="800" title="A comparison of EI and CEI. In this example, CEI can solve the problem that is due to overconfident stationary models. Overall, it leads to more informative acquisitions as it avoids locations with small predictive variances."/></p>

The problem above, that is due to overconfident stationary surrogates, can also be solved by modifying the acquisition step. The proposed [Collapsed Expected Improvement (CEI)](/assets/docs/techrep_cei_tr.pdf) is based on the repeated application of the Laplace method with mode collapse, resulting in more informative acquisitions. This method may also be combined with informative priors. Since an approximate posterior over promising points is computed as a byproduct, this information may be used to update the shaping function that induces the nonstationary effects.
In addition, the underlying idea offers a general strategy to estimate multimodal functions/distributions without the problems generally associated with 1-turn variational inference (mass-covering or mode-seeking).

## High-dimensional Bayesian Optimization for Likelihood-Free Inference
[Thesis (2018)](https://project-archive.inf.ed.ac.uk/msc/20182903/msc_proj.pdf)

<p align="center"><img src="/assets/videos/BOLFI/intro_example_1d_10s.gif" alt="Motivating Example" width="400" title="A motivating example of Bayesian optimization for likelihood-free inference. High density regions correspond to regions where a discrepancy is small. In turn, this discrepancy is assumed to be conditionally normally
distributed with a Gaussian process prior. A major difficulty in high-dimensional problems is that of finding the regions of small discrepancies. For this reason, advances in high-dimensional Bayesian optimization, including high-dimensional regression, are directly applicable to high-dimensional likelihood-free inference, increasing sample efficiency."/></p>

Standard inference methods rely on the ability to explicitly evaluate the likelihood function. However, many models such as those in natural sciences are based on stochastic simulators and the likelihood function is no longer available. Several likelihood-free inference methods attempt to solve this issue, but can be inefficient. As an alternative, Bayesian optimization for likelihood-free inference (BOLFI) has emerged. In this work, the focus is on relatively high-dimensional problems. By exploiting advances in high-dimensional Bayesian optimization with additive models, higher sample efficiency is possible. New performance measures are also designed and results demonstrate their usefulness.

## Machine Learning Practical - Deep Learning
[Report on Activation Functions](/assets/docs/mlp1.pdf)  [Report on Learning rules, BatchNorm, and ConvNet](/assets/docs/mlp2.pdf)

[Interim Report on Neural Data Augmentation](/assets/docs/mlp3.pdf)  [Report on Neural Data Augmentation](/assets/docs/mlp4.pdf)

<p align="center"><img src="/assets/images/Misc/mlp_mnist.png" alt="Synthetic image samples from neural generative models" width="800" title="Synthetic image samples from neural generative models, CDCGAN (left) and CDCVAE (right)."/></p>

My interests in Bayesian statistics and machine learning led me to pursue a MSc in Artificial Intelligence at the University of Edinburgh, from which I graduated as the top student. Courses in Bayesian statistics were supplemented by more hands-on statistical programming and machine learning courses.

## ECG-based Biometrics
[Paper (2017)](https://www.scitepress.org/PublishedPapers/2017/61954/61954.pdf) [Poster (2017)](/assets/posters/ECGBiometrics_DAE_2017.pdf)  [Slides on ECG-based biometrics and dynamical systems (2017)](/assets/slides/ECGBiometrics_March2017.pdf)

<p align="center"><img src="/assets/images/Biometrics/ECG_overview.png" alt="ECG-based Biometrics" width="1200" title="An overview of ECG-based Biometrics."/></p>

Biometric identification is the task of recognizing an individual using biological or behavioral traits.
As a research assistant at [IT-Lisbon, Pattern and Image Analysis](https://www.it.pt/Groups/Index/18), I collaborated on the [Project LearnBIG](https://www.it.pt/Projects/Index/3242), focusing on signal denoising and representations of physiological signals for biometric systems: 1) helped on the development and maintenance of databases to store and annotate biosignals; 2) explored deep learning architectures for ECG-based biometrics, finding that deep autoencoders successfully learn lower-dimensional representations of heartbeat templates, leading to superior identification performance, and that these can be learned offline; 3) implemented and tested other SOTA methods for feature extraction, dimensionality reduction and classification; 4) explored state-space models for statistical biosignal processing.

## Pending Projects

<p align="center"><img src="/assets/images/Pending/scope.png" width="500" title="Scope."/></p>

In order to develop more sample-efficient methods, BOIC focused on the design of more informative Gaussian Process (GP) priors for optimization (red), and the other objective is to accelerate [Likelihood-Free Inference](/assets/docs/lfiwis.pdf) (orange). Another research direction focuses on ambient space transformations (pink), aiming to show that these transformations, including dimensionality reduction methods, are complementary to the proposed priors.

The exploration of active learning strategies, including ideas from [Search-Aware Bayesian Optimization](/assets/docs/sabo.pdf), is also a fruitful research direction.

Finally, there is the possibility to explore the connections between GP priors and Bayesian neural networks. It is typically more intuitive, and more model agnostic, to elicit priors in the observable/function space, rather than the space of neural network parameters, where there is a general lack of intrinsic meaning to experts, from which information is drawn.
