---
title: Modeling using Python
linktitle: Modeling using Python
toc: true
type: docs
date: "2020-04-29T00:00:00+01:00"
draft: false
menu:
  resources:
    parent: Resources
    name: Modeling using Python
    weight: 11

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## General comments

**R equivalents**
- `glmnet`: [`pyglmnet`](https://glm-tools.github.io/pyglmnet/index.html)
- `lme4`: [`pymer4`](http://eshinjolly.com/pymer4/) and a `sklearn` wrapper [`sklearn-lmer`](https://github.com/nimh-mbdu/sklearn-lmer)

**[Scikit-learn](https://scikit-learn.org) (`sklearn`)**
- Mostly produces *predictive* models (`fit`, `predict` and `score`); no built-in inference mechanisms
- Easy to perform CV for parameter selection (`.GridSearchCV`)
- Many [metrics](https://scikit-learn.org/stable/modules/model_evaluation.html#classification-metrics) implemented
  - [Classification](https://scikit-learn.org/stable/modules/model_evaluation.html#classification-metrics), [Regression](https://scikit-learn.org/stable/modules/model_evaluation.html#regression-metrics), [Clustering](https://scikit-learn.org/stable/modules/clustering.html#clustering-evaluation), [Distances and kernels](https://scikit-learn.org/stable/modules/metrics.html#metrics)
- Many [preprocessing](https://scikit-learn.org/stable/modules/preprocessing.html#preprocessing) tools:
  - Label encoding, scaling, standardization, transformations, etc.
- Many related packages:
  - [Related Projects](https://scikit-learn.org/stable/related_projects.html)
  - [SciKits](http://scikits.appspot.com/scikits)

**[Statsmodels](https://www.statsmodels.org) (`statsmodels`)**
- Classical statistical techniques with inference
  - ANOVAs, LMM, GLM, hypothesis testing, etc.
  - Regularization (Elastic net, Rigde, LASSO)
  - Rich family of GLM distributions
- Uses `R`-like formulas to describe models

**[Scipy stats module](https://docs.scipy.org/doc/scipy-0.15.1/reference/stats.html) (`scipy.stats`)**
- Implements some basic statistical functions:
  - Distributions
  - Estimators
  - Hypothesis tests
  - Transformations
  - Gaussian KDE

## Categorical Data

**Logistic Regression**
- [`sklearn.linear_model.LogisticRegression`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression):
  - L1, L2 and elastic net penalties
  - For multi-class problems: one-vs-all and multinomial
- [`pyglmnet.GLM(distr="binomial")`](https://glm-tools.github.io/pyglmnet/api.html)
  - Elastic net regularization (LASSO and Ridge)
  - Cross-validation
  - Group regularization
- [`pymer4.Lmer(family="binomial")`](http://eshinjolly.com/pymer4/)
  - Mixed effect models
- [`pyGAM.LogisticGAM`](https://pygam.readthedocs.io/en/latest/api/logisticgam.html):
  - GAM (with interactions), Cross-validation, similar to `sklearn`'s API
- `statsmodels`:
  - [Binomial GLM](https://www.statsmodels.org/dev/glm.html)
  - [Binomial GLM GAM](https://www.statsmodels.org/dev/gam.html)
  - [Binomial GLM LMM](https://www.statsmodels.org/dev/mixed_linear.html)
  - [Multinomial GLM](https://www.statsmodels.org/stable/discretemod.html)

**Other GLM**
- Probit:
  - [`pyglmnet.GLM(distr="probit")`](https://glm-tools.github.io/pyglmnet/api.html)
    - Elastic net regularization (LASSO and Ridge)
    - Cross-validation
    - Group regularization
  - `statsmodels`:
    - [Probit GLM](https://www.statsmodels.org/stable/discretemod.html)

**Ridge Classifier** (Ridge regression on -1/+1 responses)
- [`sklearn.linear_model.RidgeClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.RidgeClassifier.html#sklearn.linear_model.RidgeClassifier)
  - [`sklearn.linear_model.RidgeClassifierCV`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegressionCV.html#sklearn.linear_model.LogisticRegressionCV) performs CV on a solution path

**Discriminant analysis**
- [`sklearn.discriminant_analysis`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.discriminant_analysis)
  - [LDA](https://scikit-learn.org/stable/modules/generated/sklearn.discriminant_analysis.LinearDiscriminantAnalysis), [QDA](https://scikit-learn.org/stable/modules/generated/sklearn.discriminant_analysis.QuadraticDiscriminantAnalysis)
  
**Ensemble and Tree-based Methods**
- [`sklearn.ensemble`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.ensemble):
  - [AdaBoost](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostClassifier), [Bagging](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.BaggingClassifier), [Gradient Boosting](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingClassifier), [Random Forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier)
- [`sklearn.trees.DecisionTreeClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html#sklearn.tree.DecisionTreeClassifier)
  
**Gaussian Process**
- [`sklearn.gaussian_process.GaussianProcessClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.gaussian_process.GaussianProcessClassifier)

**Naive Bayes**
- [`sklearn.naive_bayes`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.naive_bayes)

**K-Nearest-Neighbors**
- [`sklearn.neighbors.KNearestNeighborsClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier)
  - uniform weights, distance weights, custom weights
  - multiple [distance metrics](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.DistanceMetric.html?highlight=distancemetric#sklearn.neighbors.DistanceMetric)

**Neural Networks**
- [`sklearn.linear_model.Perceptron`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Perceptron.html#sklearn.linear_model.Perceptron)
- [`sklearn.neural_network.MLPClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html#sklearn.neural_network.MLPClassifier)
  - multiple layers
  - activations: identity, logistic (sigmoid), ReLU, tanh
  - weight decay
- [`sklearn.neural_network.BernoulliRBM`](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.BernoulliRBM.html#sklearn.neural_network.BernoulliRBM)
- [`sknn.nlp.Classifier`](https://scikit-neuralnetwork.readthedocs.io/en/latest/guide_model.html)
  - Compatible with `sklearn`
  - Many more types of layers and activations
- [pyTorch](https://pytorch.org/docs/stable/nn.html), [TensorFlow](https://www.tensorflow.org/api_docs/python/) (see also [Keras](https://keras.io/))

**Support Vector Machines**
- [`sklearn.svm`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.svm)
  - [Linear](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html#sklearn.svm.LinearSVC)
  - [Kernel](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html#sklearn.svm.SVC): linear, polynomial, Gaussian, etc.

**Multiclass and Multilabel Data**

- [`sklearn.multiclass`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.multiclass)
  - meta-estimator for one-vs-one and one-vs-rest (one-vs-all)
- [`sklearn.multioutput.MultiOutputClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.multioutput.MultiOutputClassifier)
  - to apply binary classifiers to multiple outputs



## Numerical Data

**Linear Regression, ANOVA and Linear Mixed Models**
- [`sklearn.linear_model.LinearRegression`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html#sklearn.linear_model.LinearRegression)
  - Regularizations: [Ridge](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Ridge.html#sklearn.linear_model.Ridge), [LASSO](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Lasso.html#sklearn.linear_model.Lasso), [Elastic net](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.ElasticNet.html#sklearn.linear_model.ElasticNet)
  - Multi-task/multi-output: [Elastic net](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.MultiTaskElasticNet.html#sklearn.linear_model.MultiTaskElasticNet), [LASSO](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.MultiTaskLasso.html#sklearn.linear_model.MultiTaskLasso)
- [`pymer4`](http://eshinjolly.com/pymer4/) 
  - Mixed effect models
  - [`sklearn-lmer`](https://github.com/nimh-mbdu/sklearn-lmer): a `sklearn` wrapper with CV
- [`pyglmnet.GLM(distr="gaussian")`](https://glm-tools.github.io/pyglmnet/api.html)
  - Elastic net regularization (LASSO and Ridge)
  - Cross-validation
  - Group regularization
- [`pyGAM.LinearGAM`](https://pygam.readthedocs.io/en/latest/api/lineargam.html):
  - GAM (with interactions), Cross-validation, similar to `sklearn`'s API
- [`statsmodels`](https://www.statsmodels.org/dev/user-guide.html#regression-and-linear-models)
  - [Linear Regression](https://www.statsmodels.org/dev/regression.html)
  - [GAM](https://www.statsmodels.org/dev/gam.html)
  - [Linear Mixed Effect Models](https://www.statsmodels.org/dev/mixed_linear.html)
  - [ANOVA](https://www.statsmodels.org/dev/anova.html)
  - [MANOVA](https://www.statsmodels.org/dev/generated/statsmodels.multivariate.manova.MANOVA.html#statsmodels.multivariate.manova.MANOVA)


**GLM**
- Count data (Poisson)
  - [`pyglmnet.GLM(distr="poisson")`](https://glm-tools.github.io/pyglmnet/api.html)
    - Elastic net regularization (LASSO and Ridge)
    - Cross-validation
    - Group regularization
  - [`pymer4.Lmer(family="poisson")`](http://eshinjolly.com/pymer4/)
    - Mixed effect models
  - [`pyGAM.PoissonGAM`](https://pygam.readthedocs.io/en/latest/api/poissongam.html):
    - GAM (with interactions), Cross-validation, similar to `sklearn`'s API
  - `statsmodels`:
    - [Contingency Tables](https://www.statsmodels.org/dev/contingency_tables.html)
    - [Poisson GLM](https://www.statsmodels.org/dev/glm.html)
    - [Poisson GLM GAM](https://www.statsmodels.org/dev/gam.html)
    - [Poisson GLM LMM](https://www.statsmodels.org/dev/mixed_linear.html)
    - [Generalized Poisson GLM](https://www.statsmodels.org/stable/discretemod.html)
- Count data (Binomial)
  - `statsmodels`:
    - [Binomial GLM](https://www.statsmodels.org/dev/glm.html)
    - [Binomial GLM GAM](https://www.statsmodels.org/dev/gam.html)
    - [Binomial GLM LMM](https://www.statsmodels.org/dev/mixed_linear.html)
- Count data (Negative Binomial)
  - `statsmodels`:
    - [Negative Binomial GLM](https://www.statsmodels.org/dev/glm.html)
    - [Poisson GLM GAM](https://www.statsmodels.org/dev/gam.html)
- Count data (Zero-Inflated Models)
  - `statsmodels`:
    - [Zero-Inflated Poisson GLM](https://www.statsmodels.org/stable/discretemod.html)
    - [Zero-Inflated NegativeBinomial GLM](https://www.statsmodels.org/stable/discretemod.html)
    - [Zero-Inflated Generalized Poisson GLM](https://www.statsmodels.org/stable/discretemod.html)
- Right-continuous Data (Gamma)
  - [`pyglmnet.GLM(distr="gamma")`](https://glm-tools.github.io/pyglmnet/api.html)
    - Elastic net regularization (LASSO and Ridge)
    - Cross-validation
    - Group regularization
  - [`pymer4.Lmer(family="gamma")`](http://eshinjolly.com/pymer4/)
    - Mixed effect models
  - [`pyGAM.GammaGAM`](https://pygam.readthedocs.io/en/latest/api/gammagam.html):
    - GAM (with interactions), Cross-validation, similar to `sklearn`'s API
  - `statsmodels`:
    - [Gamma GLM](https://www.statsmodels.org/dev/glm.html)
    - [Gamma GLM GAM](https://www.statsmodels.org/dev/gam.html)
- Right-continuous Data (Inverse Gaussian)
  - [`pymer4.Lmer(family="inverse_gaussian")`](http://eshinjolly.com/pymer4/)
    - Mixed effect models
  - [`pyGAM.InvGaussGAM`](https://pygam.readthedocs.io/en/latest/api/invgaussgam.html):
    - GAM (with interactions), Cross-validation, similar to `sklearn`'s API
  - `statsmodels`:
    - [Inverse Gaussian GLM](https://www.statsmodels.org/dev/glm.html)
    - [Inverse Gaussian GLM GAM](https://www.statsmodels.org/dev/gam.html)
- Right-continuous with Excess Zero Data (Tweedie with $p\in(1,2)$)
  - `statsmodels`:
    - [Tweedie GLM](https://www.statsmodels.org/dev/glm.html)
    - [Tweedie GLM GAM](https://www.statsmodels.org/dev/gam.html)

**Kernel Linear Regression**
- [`sklearn.kernel_ridge.KernelRidge`](https://scikit-learn.org/stable/modules/generated/sklearn.kernel_ridge.KernelRidge.html#sklearn.kernel_ridge.KernelRidge)
  - Kernels: linear, polynomial, Gaussian, etc.

**Ensemble and Tree-based Methods**
- [`sklearn.ensemble`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.ensemble):
  - [AdaBoost](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.AdaBoostRegressor.html#sklearn.ensemble.AdaBoostRegressor), [Bagging](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.BaggingRegressor.html#sklearn.ensemble.BaggingRegressor), [Gradient Boosting](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingRegressor.html#sklearn.ensemble.GradientBoostingRegressor), [Random Forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html#sklearn.ensemble.RandomForestRegressor)
- [`sklearn.trees.DecisionTreeRegressor`](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeRegressor.html#sklearn.tree.DecisionTreeRegressor)
  
**Gaussian Process**
- [`sklearn.gaussian_process.GaussianProcessRegressor`](https://scikit-learn.org/stable/modules/generated/sklearn.gaussian_process.GaussianProcessRegressor.html#sklearn.gaussian_process.GaussianProcessRegressor)

**K-Nearest-Neighbors**
- [`sklearn.neighbors.KNearestNeighborsRegressor`](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsRegressor.html#sklearn.neighbors.KNeighborsRegressor)
  - uniform weights, distance weights, custom weights
  - multiple [distance metrics](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.DistanceMetric.html?highlight=distancemetric#sklearn.neighbors.DistanceMetric)

**Neural Networks**
- [`sklearn.neural_network.MLPRegressor`](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPRegressor.html#sklearn.neural_network.MLPRegressor)
  - multiple layers
  - activations: identity, logistic (sigmoid), ReLU, tanh
  - weight decay
- [`sknn.nlp.Regressor`](https://scikit-neuralnetwork.readthedocs.io/en/latest/guide_model.html)
  - Compatible with `sklearn`
  - Many more types of layers and activations
- [pyTorch](https://pytorch.org/docs/stable/nn.html), [TensorFlow](https://www.tensorflow.org/api_docs/python/) (see also [Keras](https://keras.io/))
  
**Support Vector Machines**
- [`sklearn.svm`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.svm)
  - [Linear](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVR.html#sklearn.svm.LinearSVR)
  - [Kernel](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVR.html#sklearn.svm.SVR): linear, polynomial, Gaussian, etc.


## Unsupervised Learning

**Clustering**
- [`sklearn.cluster`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.cluster)
  - [K-means](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html#sklearn.cluster.KMeans), [Agglomerative clustering](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html#sklearn.cluster.AgglomerativeClustering)
  
**Gaussian Mixture Model**
- [`sklearn.mixture.GaussianMixture`](https://scikit-learn.org/stable/modules/generated/sklearn.mixture.GaussianMixture.html#sklearn.mixture.GaussianMixture)
  
## Dimensionality Reduction

- [`sklearn.decomposition`](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.decomposition):
  - [Kernel PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.KernelPCA.html#sklearn.decomposition.KernelPCA), [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html#sklearn.decomposition.PCA)
- [`sklearn.manifold`](https://scikit-learn.org/stable/modules/manifold.html#manifold):
  - Isomap, t-SNE, eetc.
- [`sknn.ae.AutoEncoder`](https://scikit-neuralnetwork.readthedocs.io/en/latest/module_ae.html)
  - Neural network autoencoder

