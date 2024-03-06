---
layout: post
title: Oversampling and Undersampling
subtitle: A technique for Imbalanced Classification
# gh-repo: mazino2d/mazino2d.github.io
# gh-badge: [star, fork, follow]
tags: [machine-learning]
# cover-img: /assets/img/path.jpg
# thumbnail-img: /assets/img/thumb.png
# share-img: /assets/img/path.jpg
comments: true
---

The imbalanced classification problem is what we face when there is **a severe skew in the class distribution of our training data**, such as 1:100 or 1:1000 examples in the minority class to the majority class. It can influence the performance on our machine learning algorithms. 

One way the imbalance may affect our Machine Learning algorithm is when **our algorithm completely ignores the minority class**. The reason this is an issue is because the minority class is often the class that we are most interested in.

An approach to combat this challenge is **Oversampling and Undersampling**.

## Oversampling

#### Naive random over-sampling

Very simple, this method is over-sampling by duplicating some of the original samples of the minority class.

This technique can be effective for those machine learning algorithms that are affected by a skewed distribution and where multiple duplicate examples for a given class can influence the fit of the model. This might include algorithms that iteratively learn coefficients, like artificial neural networks that use stochastic gradient descent. It can also affect models that seek good splits of the data, such as support vector machines and decision trees.

In some cases, seeking a balanced distribution for a severely imbalanced dataset can cause affected algorithms to overfit the minority class, leading to increased generalization error. The effect can be better performance on the training dataset, but worse performance on the holdout or test dataset.

Code example:

```python
from imblearn.over_sampling import RandomOverSampler
ros = RandomOverSampler(random_state=0)
X_resampled, y_resampled = ros.fit_resample(X, y)
```



#### Synthetic Minority Oversampling Technique (SMOTE)

Perhaps the most widely used approach to synthesizing new examples is called the *Synthetic Minority Oversampling TEchnique*.

SMOTE works by selecting examples that are close in the feature space, drawing a line between the examples in the feature space and drawing a new sample at a point along that line.

Specifically, a random example (`x`) from the minority class is first chosen. Then k of the nearest neighbors for that example are found (typically k=5). A randomly selected neighbor (`x_neighbor`) is chosen and a synthetic example is created at a randomly selected point between the two examples in feature space.

```x_new = x + lambda * (x_neighbor - x)```

where `lambda` is a random number in the range `[0, 1]`. This interpolation will create a sample on the line between `x` and `x_neighbor`.

The approach is effective because new synthetic examples from the minority class are created that are plausible, that is, are relatively close in feature space to existing examples from the minority class.

A general downside of the approach is that synthetic examples are created without considering the majority class, possibly resulting in ambiguous examples if there is a strong overlap for the classes.

Code example:

```python
from imblearn.over_sampling import SMOTE
X_resampled, y_resampled = SMOTE().fit_resample(X, y)
```

#### Borderline-SMOTE

These examples that are misclassified are likely ambiguous and in a region of the edge or border of decision boundary where class membership may overlap. As such, this modified to SMOTE is called Borderline-SMOTE.

Borderline-SMOTE will classify each sample *x* to be 
- (i) noise (i.e. all nearest-neighbors are from a different class than the one of *x*)
- (ii) in danger (i.e. at least half of the nearest neighbors are from the same class than *x*)
- (iii) safe (i.e. all nearest neighbors are from the same class than *x*) 

It will use the samples **in danger** to generate new samples. Then, it will select  *x_neighbor* by 2 ways:
- Neighbor will belong to the same class than the one of the sample.
- Neighbor can be from any class.

#### Adaptive Synthetic Sampling (ADASYN)

Another approach involves generating synthetic samples inversely proportional to the density of the examples in the minority class.

That is, generate more synthetic examples in regions of the feature space where the density of minority examples is low, and fewer or none where the density is high.

ADASYN is based on the idea of adaptively generating minority data samples according to their distributions: more synthetic data is generated for minority class samples that are harder to learn compared to those minority samples that are easier to learn.

With online Borderline-SMOTE, a discriminative model is not created. Instead, examples in the minority class are weighted according to their density, then those examples with the lowest density are the focus for the SMOTE synthetic example generation process.

