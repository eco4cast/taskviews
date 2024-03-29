# Uncertainty quantification, Data assimilation, Modeling & Statistics
## Overview
*Curators: Abby Lewis^1, Ben Toh^2, Jake Zwart^3, Alexey Shiklomanov^4, Leah Johnson^1, Ethan White^2, Hassan Moustahfid^5, Kelly Heilman^6, Ash Griffin^7, Jody Peters^8, Quinn Thomas^1, Mike Dietze^9*
^1Virginia Tech, ^2University of Florida, ^3USGS, ^4NASA, ^5NOAA, ^6University of Arizona, ^7MailChimp, ^8University of Notre Dame, ^9Boston University

The crux of a successful forecasting system is an effective model with properly specified uncertainty. Numerous techniques are available to create a model for a given forecasting problem, and each modeling technique will require different mechanisms for incorporating, quantifying, and propagating uncertainty. Here, we outline the tools available for both empirical (statistical, Bayesian, and machine learning) and mechanistic models (Figure 1: C). To expand on existing modeling resources, we then describe how uncertainty can be incorporated into a forecasting workflow using different types of model and tools for assimilating new data to update a forecast (Figure 1: D). 

![Figure 1. Conceptual diagram of the components in the forecast workflow, including the iterative forecast and adaptive management cycles. A (Data Ingest, Cleaning, Management) and D (Visualization/Decision Support Tools, User Interface) will be described in future task views. B (Data Assimilation) and C (Model) are described below.](images/Fig1_StatsMethodsUncertaintyTaskView.png)


## Empirical models 

In general, empirical models let data speak for itself, making inferences and predictions without extensively encoding the underlying ecological process. These models are often fast and computationally efficient when making predictions. However, they are only informed by previous values in the dataset and therefore may be unlikely to perform well outside of the range of observed conditions. Furthermore, improper variable selection and assumptions on distributions can cause inaccurate predictions. In this section, we outline tools for two categories of empirical models: statistical models and machine learning. 

### Statistical model (frequentist) 

Statistical models use historical data to estimate statistical parameters, then use those estimates to forecast into the future. In this section we focus on some of the more commonly used tools for fitting statistical models and making forecasts within a frequentist framework. Time series models, e.g. Auto Regressive Integrated Moving Average ([ARIMA](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average)) models, are a common choice of statistical model relevant to forecasting. These models focus on learning the temporal pattern of the past, including seasonality and temporal autocorrelation, and project this pattern into the future in a forecasting setting.

#### Tools for frequentist models  

The following are commonly used tools for fitting and running frequentist models for the interpreted programming languages R and Python. See the [Reproducible Forecasting Workflows post](https://ecoforecast.org/reproducible-forecasting-workflows/#scripted) for more details on these two interpreted languages. 
* R   
+ The [stats](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/00Index.html) (aka “base R”) package provides time series functions such as [ts()](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/ts.html) and [arima()](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/arima0.html) for representing time series objects and fitting ARIMA models.   
+ The [forecast package](https://cran.r-project.org/web/packages/forecast/index.html) offers more useful tools for fitting ARIMA models. For example, [auto.arima()](https://www.rdocumentation.org/packages/forecast/versions/8.14/topics/auto.arima) finds the best set of parameters for both seasonal and non-seasonal components of the ARIMA model based on Akaike information criterion (AIC) or Bayesian information criterion (BIC); [forecast()](https://www.rdocumentation.org/packages/forecast/versions/8.14/topics/forecast) makes predictions and great forecasting plots (with prediction uncertainty!) based on your choice of ARIMA model. It also provides useful statistical tests and cross-validation functions. See [this online textbook](https://otexts.com/fpp2/arima.html).   
+ The [nlme](https://cran.r-project.org/web/packages/nlme/index.html), [lme4](https://cran.r-project.org/web/packages/glmmTMB/index.html) and [glmmTMB](https://cran.r-project.org/web/packages/glmmTMB/index.html) packages can be used to fit Generalized Linear Mixed Models (GLMM), incorporating autoregressive model (AR1) structure alongside other random effects.
+ The [mgcv](https://cran.r-project.org/web/packages/mgcv/index.html) and [gamm4](https://cran.r-project.org/web/packages/gamm4/index.html) packages provide the [gamm()](https://www.rdocumentation.org/packages/mgcv/versions/1.8-35/topics/gamm) function to fit Generalized Additive Mixed Models, incorporating AR1 structure, random effects and splines, and spatial smoothers.
* Python
+ The [statsmodels](https://www.statsmodels.org/stable/index.html) module provides the core functions for working with ARIMA models including [arima.model.ARIMA()](https://www.statsmodels.org/stable/generated/statsmodels.tsa.arima.model.ARIMA.html#statsmodels.tsa.arima.model.ARIMA) for fitting models of specific orders and functions for comparing the fits of models with different orders. 
+ The [pmdarima](https://pypi.org/project/pmdarima/) module provides a high level wrapper to statsmodels with equivalent functionality to 'forecast::auto.arima()' in R. The [auto_arima()](https://alkaline-ml.com/pmdarima/modules/generated/pmdarima.arima.auto_arima.html?highlight=auto_arima) function provides automated model selection to determine the best seasonal and non-seasonal ARIMA models based on a suite of information criteria. This package also provides useful statistical tests and cross-validation functions.

### Statistical model (Bayesian)
In a Bayesian framework, all fitted parameters have a probability distribution. This is useful as it enables robust accounting of parameter uncertainty, and allows for the model to be informed by existing data or expertise. Often, a Bayesian framework also allows the user to fit more complicated and hierarchical time series models, while accounting for uncertainty in parameters, drivers, and observation data. Options for fitting Bayesian models include (1) working directly with Markov chain Monte Carlo (MCMC) samplers, (2) interfacing with existing MCMC or Gibbs samplers such as Just Another Gibbs Sampler (JAGS), Bayesian inference Using Gibbs Sampling (BUGS), or Stan, (3) using readily available “native” functions, and (4) Laplace approximation. These methods are all described in more detail below.

####Work directly with Markov chain Monte Carlo (MCMC)
* R
+ The [mcmc](https://cran.r-project.org/web/packages/mcmc/index.html) package facilitates sampling from a posterior distribution using the Metropolis algorithm and provides other useful helper functions
+ The [MCMCpack](https://cran.r-project.org/web/packages/MCMCpack/index.html) package also provides a function to sample from a distribution using the Metropolis algorithm and provides other useful helper functions
+ The [BayesianTools](https://cran.r-project.org/web/packages/BayesianTools/index.html) package provides functions to run a range of different MCMC algorithms as well as non-MCMC sampling algorithms such as rejection sampling and sequential Monte Carlo (SMC). Also provides model selections and multi-model inference functionality. Treats the model as a ‘black box’ so particularly handy for calibrating mechanistic models.
* Python 
+ The [pymc3](https://docs.pymc.io/) module allows models to be written using the Python language, and fits the model using various sampling algorithms.

####Interface with JAGS/BUGS/Stan
Instead of working directly with MCMC samplers, a model can be specified in the [JAGS](https://mcmc-jags.sourceforge.io/) (Just Another Gibbs Sampler), [BUGS](https://www.mrc-bsu.cam.ac.uk/software/bugs/) (Bayesian Inference Using Gibbs Sampling), [nimble](https://cran.r-project.org/web/packages/nimble/index.html), or [Stan](https://mc-stan.org/) syntax. Stan can be faster for complex, hierarchical models without conjugacy. For simple models, ones that have conjugate relationships, or models with a lot of latent variables, JAGS/BUGS/NIMBLE are usually faster.These languages select samplers based on the model, and provide posterior samples. Differences in these programs are primarily in the backend algorithms.
* R
+ [rjags](https://cran.r-project.org/web/packages/rjags/index.html), [R2jags](http://R2jags) and [jagsUI](https://cran.r-project.org/web/packages/jagsUI/index.html) are some of the packages that pass data and model specification to JAGS.
+ The [nimble](https://cran.r-project.org/web/packages/nimble/index.html) package compiles and runs models in C, making them more computationally efficient. It provides a lot of flexibility to optimize samplers and create customized functions and samplers. See some [examples of custom distributions for ecology](https://r-nimble.org/nimbleecology-custom-nimble-distributions-for-ecologists).
+ The [rstan package](https://mc-stan.org/rstan/) interfaces R with [Stan](https://mc-stan.org/users/documentation/). 
+ [bayesforecast](https://CRAN.R-project.org/package=bayesforecast) package uses Stan as a backend to implement ARIMA, Generalized AutoRegressive Conditional Heteroskedasticity (GARCH) and other forecasting models.
* Python 
+ The [pyjags](https://pypi.org/project/pyjags/) and [pystan](https://pypi.org/project/pystan/2.2.0.0/) modules are used to interface with JAGS and Stan.

####Readily available “native” functions
By trading flexibility and customizability for some convenience, some packages allow us to fit Bayesian models with “native” functions. 
* R
+ [brms](https://cran.r-project.org/web/packages/brms/index.html) lets us fit the ARMA model with syntax and formula familiar to every R user: e.g., fit <- brm(y ~ x + arma(p = 1, q = 1), data = data). Uses Stan under the hood.
+ [rstanarm](https://cran.r-project.org/web/packages/rstanarm/index.html) documentations provide [a number of examples](https://mc-stan.org/rstanarm/articles/) of fitting GLMM using native R syntax with Stan under the hood.
+ [glmmfields](https://github.com/seananderson/glmmfields) fits spatiotemporal GLMM using Stan under the hood.
+ [MCMCPack](https://cran.r-project.org/web/packages/MCMCpack/index.html) provides functions to fit numerous regression models under Bayesian framework.
+ [spBayes](https://cran.r-project.org/web/packages/spBayes/index.html) fits spatiotemporal GLMM using native R language
+ The [BMS](http://bms.zeugner.eu/) package enables Bayesian model averaging, sampling data according to different g-priors and model priors and can work with a wide variety of samples

####Laplace Approximation
The Bayesian approach is generally much more time consuming than frequentist and machine learning. Fitting time for MCMC is slow and due to the iterative nature of MCMC, parallelization of individual chains is not possible. One of the most common and well supported ways is to approximate the posterior distributions using Laplace approximation. The [R-INLA package](http://www.r-inla.org/) (inla) provides ways to fit a wide variety of statistical models via the integrated nested Laplace approximation approach. It is now heavily used in temporal, spatial and spatiotemporal GLMM. 

### Spatio-temporal statistical models
The book [Spatio-Temporal Statistics with R](https://spacetimewithr.org/) by Wikle et al. (2019) provides an accessible introduction to both frequentist and Bayesian approaches to spatiotemporal modeling (i.e. models for forecasting across both space and time) using a range of packages in R.  The book particularly emphasizes the use of basis functions to approximate spatiotemporal covariance structures. The website provides open text and hands-on activities. 

### Machine learning
Unlike statistical models, Machine Learning (ML) models make few assumptions about probability distributions, instead relying on algorithms to learn patterns by themselves. ML allows for complex interactions among predictors (commonly called *features* in the ML community) without *a priori* specification. However, often it is best to carefully select the features used to train the ML models based on which features will most likely be influential to the variable being predicted. This feature selection can either be guided by ML models themselves, or by domain experts. Furthermore, outputs from other mechanistic or statistical methods can be used as features to train a ML model. Given enough data, ML methods often provide more accurate predictions than parametric statistical methods, largely due to their flexibility and limited a priori assumptions on variable distributions. Injecting process knowledge into ML techniques is an active and growing area of research (e.g. ‘[theory-guided machine learning](https://ieeexplore.ieee.org/abstract/document/7959606)’, [neural hierarchical models](https://onlinelibrary.wiley.com/doi/full/10.1111/ele.13462?casa_token=qVMfHetF3hsAAAAA%3A1XJBLU1VLvNDPEPfGIXybcYcr2jb86Foy8twEkHpk_yVVySg_FtalJVDECQxdS-28OYeBqCF4s4tGiiJ), [process-guided deep learning](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2019WR024922)). 

Methods that are generally considered ML include decision tree based methods (e.g. Classification And Regression Tree ([CART](https://en.wikipedia.org/wiki/Decision_tree_learning), [random forest](https://en.wikipedia.org/wiki/Random_forest), [gradient boosted trees](https://en.wikipedia.org/wiki/Gradient_boosting#Gradient_tree_boosting)), support vector machines (SVM), and artificial neural networks (ANN). More complicated deep learning models are a form of ANNs  and are increasingly utilized in ecological forecasting. Empirical Dynamic Modeling is a time-series specific machine learning approach that is often used in ecological forecasting.

####Tools used for ML models 
* R
+ [gbm](https://cran.r-project.org/web/packages/gbm/index.html) and [xgboost](https://cran.r-project.org/web/packages/xgboost/index.html) for Gradient boosted trees
+ [randomForest](https://cran.r-project.org/web/packages/randomForest/index.html) for random forest
+ [caret](https://cran.r-project.org/web/packages/caret/) streamlines the process of fitting ML (and some stats) models, providing functions to pre-process data, conduct feature selections and parameter tuning, which is a very important aspect of ML.
+ [bartMachine](https://cran.r-project.org/web/packages/bartMachine/index.html) to fit Bayesian Additive Regression Trees (BART), which infuse Bayesian framework with decision tree methods to achieve uncertainty quantification
+ [rEDM](https://cran.r-project.org/web/packages/rEDM/index.html) for Empirical Dynamic Modeling (based on cppEDM C++ library)
* Python 
+ [scikit-learn](https://scikit-learn.org/stable/) (also known as sklearn) is the widely used ML library
+ [pyEDM](https://pypi.org/project/pyEDM/) is used for Empirical Dynamic Modeling (based on cppEDM C++ library)

####Interface with machine learning platform/libraries
For neural networks and deep learning, (e.g. the Long Short-Term Memory (LSTM) recurrent neural networks, which are popular in fitting time series), it is extremely common and popular to use a number of libraries that are based on or interface primarily with Python, e.g., [Tensorflow](https://www.tensorflow.org/), [PyTorch](https://pytorch.org/) and [keras](https://keras.io/). Thanks to Rstudio, there are now packages that interface R with these libraries ([tensorflow](https://tensorflow.rstudio.com/), [keras](https://keras.rstudio.com/) and [torch](https://blogs.rstudio.com/ai/posts/2020-09-29-introducing-torch-for-r/)).

## Mechanistic models
Mechanistic models can range from simple deterministic (finite-difference or differential equation-based) models to highly complex "black box" simulators. Simple deterministic models are often designed using custom code, but tools are available for parameter fitting and manipulating differential equations. Fewer tools are available for model fitting using external executables or agent based models. 

### Simple deterministic model
The simplicity of these is both a strength and weakness in a forecasting framework; simplifying a model structure reduces parameter uncertainty and may avoid overfitting, but it may obscure important ecological processes. 

Deterministic models are typically designed using custom code, and there are very few off-the-shelf tools to help create deterministic models. That being said, a few packages (listed below) are useful to help with parameter fitting and manipulating differential equations. For more information on (frequentist) parameter fitting in R, see this [tutorial](https://www.r-bloggers.com/learning-r-parameter-fitting-for-models-involving-differential-equations/) from R-bloggers. Bayesian inference for a limited variety of ordinary differential equations (ODEs) are available in the beta version of BUGS, or in R through the [deBInfer](https://cran.r-project.org/web/packages/deBInfer/index.html) package. 

Packages to note:
* Packages to fit ODEs
+ [deSolve](https://cran.r-project.org/web/packages/deSolve/index.html) in R
+ [ODEINT](https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.odeint.html) and [GEKKO](https://gekko.readthedocs.io/en/latest/) in Python
+ [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/) in Julia
* Packages to “run” a compiled model
+ R -- `system2` function in base R; `processx` package
+ Python -- `subprocess.call` (part of the standard library?)
* Packages for state space models (e.g. deterministic/stochastic latent process and statistical observation process)
+ [LibBi](http://libbi.org/): C++ based library for state-space modelling and Bayesian inference supporting multiple cores. Estimate model likelihood and parameters using Sequential Monte Carlo (SMC), Particle MCMC (PMCMC), Kalman filter and others. Allows writing deterministic models in relatively simplistic script.
+ [RBi](https://cran.r-project.org/web/packages/rbi/vignettes/introduction.html)  in R: R wrapper package to interface with LibBi
+ [pomp](https://tjmckinley.github.io/SimBIID_tutorial/) in R: statistical inference for partially-observed Markov processes (i.e., non-linear stochastic dynamical systems). Supports parameter estimations such as Particle MCMC (PMCMC), trajectory matching, improved iterated filtering (IF2), Approximate Bayesian Computation (ABC) and variations of Kalman Filter.
+ [SimBIID](https://tjmckinley.github.io/SimBIID_tutorial/) in R: R package mainly for simulation-based inference for infectious disease models. Provides simplistic syntax to write SIR models. Support ABC-SMC and PMCMC.
+ [nimble and nimbleSMC](https://r-nimble.org/) packages in R: Supports particle filtering and PMCMC. User creates a state-space model in BUGS.
+ [pyEMU](https://pypi.org/project/pyemu/) is a Python module that interfaces with Pest++ to fit model parameters and estimate model uncertainty. PEST++ is model-independent and should be able to fit parameters given the correctly formatted inputs, which is facilitated by pyEMU

### Black box models
The previously-mentioned [BayesianTools](https://cran.r-project.org/web/packages/BayesianTools/index.html) R package was originally designed to calibrate “black box” ecological models and provides an in-depth vignette for coupling such models to R.

While optimized for terrestrial ecosystem models, the Predictive Ecosystem Analyzer ([PEcAn](https://pecanproject.github.io/)) is a predominantly R-based workflow that includes utilities for efficient Bayesian calibration of black box models by using Gaussian Process models to [emulate the Likelihood surface](https://doi.org/10.5194/bg-15-5801-2018). More recently, this approach has been extended to a [hierarchical across-site calibration](https://www.biorxiv.org/content/10.1101/2021.04.28.441243v1).

## Uncertainty
Understanding how much uncertainty is present in ecological forecasts is essential to both scientific inference and decision making. Decisions based on a highly confident forecast will be very different from those based on a forecast with a wide range of possible outcomes, and an incomplete accounting of uncertainty will lead to falsely overconfident (and thus risk prone) decisions. Uncertainty accounting requires both quantifying uncertainty for models, or components of models, and propagating that uncertainty through other aspects of the full forecast. Forecasts may include a variety of different types of uncertainty such as parameter uncertainty, random effect uncertainty, initial condition uncertainty, covariate or driver uncertainty, and process uncertainty.

### Statistical model (frequentist)
For most frequentist models, uncertainty sources are limited to parameter uncertainty and residual error, which are produced by most of the tools described for statistical modeling above. Parameter uncertainty can also be estimated using bootstrapping and other similar methods. Tools for producing prediction intervals (the range of values expected to capture a percentage of future observations) for these models include:
* R: forecast() function from the [forecast](https://cran.r-project.org/web/packages/forecast/index.html) package can be used to produce prediction intervals for many statistical models.
* Python: the same functionality is available in the get_forecast() function in [statsmodels](https://www.statsmodels.org/stable/index.html).

### Statistical model (Bayesian)
Statistical models that are formulated as Bayesian models have considerable flexibility in how multiple sources of uncertainty are incorporated and modeled. Standard inclusions are parameter uncertainty, residual process error, and observational uncertainty. Hierarchical models (the Bayesian versions of mixed effects models) allow variation in parameters between groups, and uncertainty in the parameters that describe the group level variation. Additionally, it is possible to explicitly include model uncertainty when using Bayesian methods, for example through Bayesian model averaging approaches. Typically estimates of all types of error/uncertainties, including predictive, must be obtained via Monte Carlo methods (as described below) as closed form solutions are only rarely available. 

### Machine learning models
Machine learning covers a wide range of models with equivalently wide ranges of approaches to uncertainty, including some methods that lack uncertainty estimates entirely using their standard implementations. Since machine learning is often focused on prediction, many methods produce estimates of uncertainty in the predictions, which is useful in a forecasting context. Some approaches are implemented so that the tools for prediction intervals described in *Statistical models (frequentist)* can also be used with these models. For neural networks, Monte Carlo dropout and Gaussian mixture methods [have also been used](https://arxiv.org/pdf/2012.14295.pdf). Other approaches may require handling uncertainty in a manner specific to the modeling approach. 

### Mechanistic Models: Monte Carlo propagation and partitioning
Most mechanistic models do not inherently include analytical uncertainty estimators, and thus uncertainty is usually incorporated using Monte Carlo methods (which can also be applied to any of the previous approaches). Monte Carlo methods involve running the model repeatedly with stochastic variation in either model inputs (e.g., incorporating uncertainty in the initial conditions and/or drivers), parameter values (to capture uncertainty in the parameters of the model), and/or residual/process error distribution. This is typically implemented using an ensemble approach, where each ensemble member has parameter and driver inputs drawn from a specified distribution (see Table 1 for tools). For models that include a temporal component uncertainty propagates into the future due to compounding differences in parameters and drivers between ensemble members. Uncertainty partitioning can be done using either global variance-based methods (e.g. Sobol indices) or one at a time (OAT) methods. Using OAT methods, all but one source of uncertainty is set to not have any variability, the contribution of that source of uncertainty to variability in the forecast output is determined, and this process is repeated for all other sources of uncertainty. A primer on [Monte Carlo propagation and OAT partitioning](https://github.com/EcoForecast/EF_Activities/blob/master/Chapter_11_UncertAnalysis.Rmd) is available as part of the [Ecological Forecasting book](https://press.princeton.edu/books/hardcover/9780691160573/ecological-forecasting).

### Uncertainty in covariates
One of the unique challenges related to uncertainty for forecasting is incorporating uncertainty in the value of future covariates. For example, a model that relies on climate covariates should include uncertainty in future climate conditions in forecasts. In Bayesian approaches this uncertainty can be incorporated directly into the model to make predictions. In other approaches it can be incorporated by running the model repeatedly using ensembles of covariates based on uncertainty in the covariate forecast. The different sets of predictions can then be incorporated using ensemble approaches (see *Mechanistic Models: Monte Carlo propagation and partitioning*). 

###Propagating uncertainty
There are currently not many “off the shelf” tools for propagating uncertainty in forecasts, as many forecasting practitioners develop their own pipelines for analyzing and propagating uncertainty into their forecasts. However, a few tools do exist:

* R 
+ The [spup](https://rjournal.github.io/archive/2018/RJ-2018-047/index.html) package provides tools for spatial uncertainty propagation and analysis
+ The [sensitivity](https://cran.r-project.org/web/packages/sensitivity/index.html) package provides tools for global variance-based sensitivity analyses that can be used for uncertainty partitioning
* Python
+ [Uncertainpy](https://uncertainpy.readthedocs.io/en/latest/) provides tools for uncertainty quantification and sensitivity analysis using quasi-Monte Carlo methods and polynomial chaos expansions
* Julia
+ [Measurements.jl](https://juliaphysics.github.io/Measurements.jl/stable/) package for propagating uncertainty using linear error propagation theory

Additionally, many resources and tutorials exist that can be useful for both analyzing and propagating uncertainty:

Uncertainty Analysis:
* [Uncertainty Analysis](https://youtu.be/rDCkjzVQNSw) YouTube tutorial ([EFI/NEON series](https://www.youtube.com/watch?v=kq0DTcotpA0&list=PLLWiknuNGd50Lc3rft4kFPc_oxAhiQ-6s))
* [UQWorld](https://uqworld.org/): uncertainty quantification community and resources 

Uncertainty Propagation YouTube Tutorials ([EFI/NEON series](https://www.youtube.com/watch?v=kq0DTcotpA0&list=PLLWiknuNGd50Lc3rft4kFPc_oxAhiQ-6s)): 
* [Tradeoffs & Analytical Moments](https://youtu.be/fxJX729jHnY)
* [Linear Tangent](https://youtu.be/-PZrKjSEuiw)
* [Monte Carlo](https://youtu.be/Wdob95zfqe8)

##Data assimilation
Updating model predictions to incorporate new data is a central component of near-term ecological forecasting (Figure 1). One way of doing this would be to repeat the entire model-fitting procedure above any time new observations are added to a dataset. However, that may be very computationally expensive, especially for large complex models. Instead, one might prefer to update existing model predictions using just the new observations (and their uncertainties) and then re-generate new predictions starting from the updated model state. We describe this process as **data assimilation**.

**A Note on Vocabulary**
The term “Data assimilation” (or sometimes, “model-data fusion”) is often used to describe a variety of modeling activities. Some people use “batch data assimilation” or “parameter data assimilation” to describe fitting models to data (see earlier sections). Others use “data assimilation” to broadly refer to any activity that combines information from data and models in any way, such as initializing a model with observed conditions or using observations as model drivers or boundary conditions. For the purposes of this document, we use “data assimilation” to mean the specific approach we describe above; namely, iteratively updating model states using observations (sometimes called “state” data assimilation or “sequential” data assimilation; Figure 2).

![Figure 2. In a sequential data assimilation framework, estimates of model states (and optionally parameters) are updated as new observations are assimilated into the model. The updated states take into account state observations and modeled state estimates as well as the relative confidence in each (shown as distributions). The updated states are then used as initial conditions for the model to make predictions at the next time step (t+1) using the model’s equations. Figure from Ellen Bechtel and Jake Zwart.
](images/Fig2_StatsMethodsUncertaintyTaskView.png)

For a given time step, a data assimilation algorithm takes two things as inputs: a joint probability distribution of model predictions for all model variables, and distributions of observations of a subset of those model variables. The data assimilation algorithm then synthesizes this information from both the model and the data and produces as output a new joint posterior distribution of all model variables (taking into account covariance between model variables). This new joint posterior distribution is used as the new model initial condition to generate updated predictions into the future (Figure 2).

###Data assimilation approaches 
Different data assimilation approaches (Table 1) differ in their assumptions about the distributions of the model and data predictions. Below we highlight some of the most commonly used data assimilation approaches.
* The simplest approach is the **Kalman Filter (KF; [EFI/NEON tutorial](https://github.com/EcoForecast/EF_Activities/blob/master/Exercise_09_KalmanFilter.Rmd))**, which assumes that both model predictions and data have Gaussian (normal) distributions and that the model is linear. This assumption gives the Kalman filter a simple (iterative) analytical solution. Because of its computational efficiency and conceptual simplicity, implementations of the Kalman filter abound.
+ If you are using a model ensemble to estimate model uncertainty, the **ensemble Kalman filter (EnKF)** first fits a multivariate normal distribution (i.e., calculates the sample mean and covariance of the ensemble) and then proceeds as the normal Kalman filter.
+ For highly computationally demanding models, where one is limited in the size of ensemble that can be used, the **unscented Kalman Filter (uKF)** uses the complex “unscented transform” to sample ensemble members systematically (rather than the random sampling in EnKF) and analytically back-transform the ensemble predictions to estimate the mean vector and covariance matrix (rather than the simple sample mean and covariance in EnKF).
* The linear model assumption of the Kalman filter can be relaxed by solving for the linear tangent approximation of model, much as one would do in initial two terms of a Taylor Series; this class of methods is called the **extended Kalman filter (eKF)**. Similar adjoint approaches are employed in variational data assimilation approaches (e.g. 4DVar).
* The most general, completely distribution-agnostic data assimilation approach is the **particle filter ([EFI/NEON tutorial link](https://github.com/EcoForecast/EF_Activities/blob/master/Exercise_10_ParticleFilter.Rmd))**, which simply resamples your model ensemble members weighted according to their likelihood relative to the observations. This approach is conceptually simple and typically easy to implement, but requires very large model ensembles and a variety of resampling methods to avoid rapid loss of effective sample size (prediction collapsing onto a small number of ensemble members that do not represent the true spread of the predictive distribution).
Data assimilation is an active area of research, particularly in atmospheric science (not least because of its importance to numerical weather prediction), and new data assimilation approaches are constantly released. Some exciting recent developments (at least to the authors) include LaVEnDAR ([Pinnington et al. 2020](https://doi.org/10.5194/gmd-13-55-20200, which implements an ensemble approach to 4DVar), the Tobit-Wishart ensemble filter (TWEnF, [Raiho et al. 2020](https://www.biorxiv.org/content/10.1101/2020.05.05.079871v10), which estimates the process error dynamically and accounts for zero-bound and zero-inflated data), and strongly coupled Earth System data assimilation techniques ([Penny et al. 2019](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2019MS001652)), among others (Table 1).

In theory, data assimilation effectively and elegantly links uncertainties in parameters (see previous sections) and states. In practice, using data assimilation to track uncertainties in parameters and states simultaneously can be challenging (e.g., avoiding rapid convergence of all ensemble members to a single point) and often requires careful algorithm tuning. For example, Kalman Filter implementations sometimes artificially inflate the variance of the distributions to avoid convergence (e.g., filter inflation), but figuring out the right amount of inflation typically requires a lot of problem-specific trial and error (or methods that solve for the process error dynamically, e.g. TWEnF).

###Tools for data assimilation 
Numerous tools exist for data assimilation , though a majority of these tools are targeted to large-scale models and big data and may be more complicated than needed for smaller ecological forecasting applications. Table 1 provides a sampling of the data assimilation tools available, but is by no means a comprehensive list.  

|Table 1: Examples of data assimilation tools|
| **Software**       | **Software programming language**     | **DA methods supported**     | **Target application and model programming language supported**  | 
| :------------- | :----------: | -----------: | -----------: | 
|  [DART](https://dart.ucar.edu/) | Fortran  | KF, enKF    | Large-scale models and big data in any language; originally created for atmospheric & oceanic models  |
|  [Nimble](https://r-nimble.org/) | R (with C++ backend)  | Particle Filter, enKF | Small-scale models that can be implemented in R |
|  [pomp](https://kingaa.github.io/pomp/) | R  | Particle Filter, enKF | Small-scale models that can be implemented in R  |
|  [PyDA](https://www.mdpi.com/2311-5521/5/4/225) | Python  | exKF, enKF, 3DVar, 4DVar | Small-scale models implemented in Python; originally created for researchers with little DA experience |
|  [KalmanFilter.jl](https://github.com/mschauer/Kalman.jl) | Julia  | KF | Small-scale models that can be implemented in Julia |
|  [StateSpace.jl](https://github.com/ElOceanografo/StateSpace.jl) | Julia  | KF, eKF, uKF, enKF  |Small-scale models that can be implemented in Julia 

 |
|  [ParticleFilters.jl](https://github.com/JuliaPOMDP/ParticleFilters.jl) | Julia  | Particle Filter | Small-scale models that can be implemented in Julia  |
|  [EMPIRE](http://www.met.reading.ac.uk/~darc/empire/index.php) | Python and Fortran  | Particle Filter, enKF, 3DVar, 4DEnVar | Medium- to large-scale models that can be implemented in any language |
|  [LaVEnDAR](https://gmd.copernicus.org/preprints/gmd-2019-60/gmd-2019-60.pdf) | Python  | 4DEnVar | Land surface models implemented in any language |
|  [BayesianTools](https://cran.r-project.org/web/packages/BayesianTools/index.html) | R  | Particle Filter | Small- to Medium-scale models in any language  |
|  [OpenDA](https://www.openda.org/) | C/C++, Java, Fortran  | enKF, 
Steady State KF, Particle Filter, 3DVar, DudEnKF^1    | Small- to large-scale models that can be implemented in any language  |
^1DudEnKF - Doesn’t Use Derivatives Ensemble Kalman Filter. See details [here](https://www.sciencedirect.com/science/article/pii/S0043135419311170). 
