---
layout: post
title: Evaluation Metrics for Binary Classification
subtitle: A comprehensive guide to choosing the best metrics for binary classification problems
# gh-repo: mazino2d/mazino2d.github.io
# gh-badge: [star, fork, follow]
tags: [machine-learning]
# cover-img: /assets/img/path.jpg
# thumbnail-img: /assets/img/thumb.png
# share-img: /assets/img/path.jpg
comments: true
---

**Classification metrics** let you assess the performance of machine learning models but there are so many of them, each one has its own benefits and drawbacks, and selecting an evaluation metric that works for your problem can sometimes be really tricky.

In this blog, I will talk about:

- What is the **definition** and **intuition** behind most major classification metrics,
- **The non-technical explanation** that you can communicate to business stakeholders about metrics for binary classification,
- How to **plot** performance charts and **calculate** common metrics for binary classification,
- **When** should you **use** them.

With that, you will understand the trade-offs so that making metric-related decisions will be easier.

## 1. Confusion Matrix

It is a table that summarizes the performance of a classification model by comparing its predicted labels to the true labels. It displays the number of true positives (TP), true negatives (TN), false positives (FP), and false negatives (FN) of the model's predictions.

- **True positives** (TP)
  - Definition: occur when the model predicted _positive_ and it’s _true_.
  - Example: you predicted that a woman is pregnant and she actually is.
- **True negatives** (TN)
  - Definition: occur when the model predicted _negative_ and it’s _true_.
  - Example: you predicted that a man is not pregnant and he actually is not.
- **False positives** (FP)
  - Definition: occur when the model predicted _positive_ and it’s _false_.
  - Example: you predicted that a man is pregnant but he actually is not.
- **False negatives** (FN)
  - Definition: occur when the model predicted _negative_ and it’s _false_.
  - Example: you predicted that a woman is not pregnant but she actually is.

{: .box-note}
**Note**: Just Remember, We describe predicted values as **Positive** and **Negative** and actual values as **True** and **False**.

### How does it look

| | Positive (Predicted) | Negative (Predicted) |
| Positive (Actual) | True Positive - TP | False Negative - FN |
| Negative (Actual) | False Positive - FP | True Negative - TN |

### How to compute

```python
from sklearn.metrics import confusion_matrix

y_pred_class = y_pred_pos > threshold
cm = confusion_matrix(y_true, y_pred_class)
tn, fp, fn, tp = cm.ravel()
```

### When to use it

- It is extremely useful for measuring Recall, Precision, Specificity, Accuracy, and most importantly, ROC AUC or Precision-Recall AUC.
- You like to see the nominal values rather than normalized to get a feel for how the model is doing in different classes.

## 2. Positive Predictive Value | Precision

It measures how many observations predicted as positive are in fact positive. **When you are optimizing precision you want to make sure that people that you put in prison are guilty**.

```text
Precision = PPV = TP / (TP + FP)
```

### How to compute

```python
from sklearn.metrics import confusion_matrix, precision_score

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
precision = precision_score(y_true, y_pred_class) # or optionally tp/ (tp + fp)
```

### When to use it

- When raising false alerts is costly, when you want all the positive predictions to be worth looking at you should optimize for precision.
- It usually doesn’t make sense to use it alone but rather coupled with other metrics like recall.

## 3. True Positive Rate | Recall | Sensitivity

It measures how many observations out of all positive observations have we classified as positive. **When you are optimizing recall you want to put all guilty in prison**.

```text
Recall = Sensitivity = TPR = TP / (TP + FN)
```

### How to compute

```python
from sklearn.metrics import confusion_matrix, recall_score

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
recall = recall_score(y_true, y_pred_class) # or optionally tp / (tp + fn)
```

### When to use it

- That being said, recall is a go-to metric, when you really care about catching all fraudulent transactions even at a cost of false alerts. Potentially it is cheap for you to process those alerts and very expensive when the transaction goes unseen.
- Usually, you will not use it alone but rather coupled with other metrics like precision.

## 4. True Negative Rate | Specificity

It measures how many observations out of all negative observations have we classified as negative. **You can think of it as recall for negative class**.

```text
Specificity = TNR = TN / (TN + FP)
```

### How to compute

```python
from sklearn.metrics import confusion_matrix

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
true_negative_rate = tn / (tn + fp)
```

### When to use it

- When you really want to be sure that you are right when you say something is safe. A typical example would be a doctor telling a patient “you are healthy”. Making a mistake here and telling a sick person they are safe and can go home is something you may want to avoid.
- Usually, you don’t use it alone but rather as an auxiliary metric.

## 5. False Positive Rate | Type I error

It measures how many observations out of all negative observations have we classified as positive. **You can think of it as a fraction of false alerts that will be raised based on your model predictions.**

```text
FPR = FP / (FP + TN) = 1 - Specificity = 1 - TNR
```

### How to compute

```python
from sklearn.metrics import confusion_matrix

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
false_positive_rate = fp / (fp + tn)
```

### When to use it

- If the cost of dealing with an alert is high you should focus to FPR metric and consider increasing the threshold to get fewer alerts.
- You rarely would use this metric alone. Usually as an auxiliary one with some other metric.

## 6. False Negative Rate | Type II error

It measures how many observations out of all positive observations have we classified as negative. **You can think of it as a fraction of missed alerts that will not be raised based on your model predictions.**

```text
FNR = FN / (FN + TP) = 1 - Recall = 1 - TPR
```

### How to compute

```python
from sklearn.metrics import confusion_matrix

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
false_positive_rate = fp / (fp + tn)
```

### When to use it

- If the cost of letting the fraudulent transactions through is high and the value you get from the users isn't you can consider focusing on this number.
- Usually, it is not used alone but rather with some other metric.

## 7. False Discovery Rate

It measures how many predictions out of all positive predictions were incorrect. **You can think of it as a fraction of false alert in all predictions that were predicted as alert**.

```text
FDR = FP / (FP + TP) = 1 - precision
```

### How to compute

```python
from sklearn.metrics import confusion_matrix

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
false_discovery_rate = fp/ (tp + fp)
```

### When to use it

- When raising false alerts is costly and when you want all the positive predictions to be worth looking at you should optimize for precision.
- Again, it usually doesn’t make sense to use it alone but rather coupled with other metrics like recall.

## 8. Accuracy

It measures how many observations, both positive and negative, were correctly classified. You shouldn't use accuracy on imbalanced problems. Then, it is easy to get a high accuracy score by simply classifying all observations as the majority class.

### How to compute

```python
from sklearn.metrics import confusion_matrix, accuracy_score

y_pred_class = y_pred_pos > threshold
tn, fp, fn, tp = confusion_matrix(y_true, y_pred_class).ravel()
accuracy = accuracy_score(y_true, y_pred_class) # or optionally (tp + tn) / (tp + fp + fn + tn)
```

### When to use it

- When your problem is balanced using accuracy is usually **a good start**. An additional benefit is that it is really **easy to explain** it to non-technical stakeholders in your project,
- When every class is **equally important** to you.

## 9. F-score

Simply put, **it combines precision and recall into one metric**. The higher the score the better our model is. You can calculate it in the following way:

```text
F = (1 + beta^2) * precision * recall / (beta^2 * precision + recall)
```

- With `0 < beta < 1` we care more about precision
- With `beta > 1` we care more about recall
- With `beta = 1` it is somewhere in the middle.

### How to compute

```python
from sklearn.metrics import f1_score
y_pred_class = y_pred_pos > threshold
f1= f1_score(y_true, y_pred_class)
```

### When to use it

Pretty much in every binary classification problem. It is my go-to metric when working on those problems. It can be easily explained to business stakeholders.

## 10. ROC AUC score

ROC Curve is a chart that visualizes the tradeoff between true positive rate (TPR) and false positive rate (FPR). Basically, for every threshold, we calculate TPR and FPR and plot it on one chart.

Of course, the higher TPR and the lower FPR is for each threshold the better and so classifiers that have curves that are more top-left side are better.

In order to get one number that tells us how good our curve is, we can calculate the Area Under the ROC Curve, or ROC AUC score. The more top-left your curve is the higher the area and hence higher ROC AUC score.

Alternatively, it can be shown that ROC AUC score is equivalent to calculating the rank correlation between predictions and targets. From an interpretation standpoint, it is more useful because it tells us that this metric shows how good at ranking predictions your model is. **It tells you what is the probability that a randomly chosen positive instance is ranked higher than a randomly chosen negative instance**.

### How to compute

```python
from scikitplot.metrics import plot_roc
fig, ax = plt.subplots()
plot_roc(y_true, y_pred, ax=ax)
from sklearn.metrics import roc_auc_score
roc_auc = roc_auc_score(y_true, y_pred_pos)
```

### When to use it

- You should **use** it when you ultimately care about **ranking predictions** and not necessarily about outputting well-calibrated probabilities.
- You should **not use** it when your data is **heavily imbalanced**.
- You should **use** it when you **care equally about positive and negative classes**. If we care about true negatives as much as we care about true positives then it totally makes sense to use ROC AUC.

## 11. PR AUC score | Average precision

It is a curve that combines precision (PPV) and Recall (TPR) in a single visualization. For every threshold, you calculate PPV and TPR and plot it. The higher on y-axis your curve is the better your model performance.

You can use this plot to make an educated decision when it comes to the classic precision/recall dilemma. Obviously, the higher the recall the lower the precision. Knowing at which recall your precision starts to fall fast can help you choose the threshold and deliver a better model.

Similarly to ROC AUC score you can calculate the Area Under the Precision-Recall Curve to get one number that describes model performance.

**You can also think about PR AUC as the average of precision scores calculated for each recall threshold [0.0, 1.0]**. You can also adjust this definition to suit your business needs by choosing/clipping recall thresholds if needed.

### How to compute

```python
from scikitplot.metrics import plot_precision_recall
fig, ax = plt.subplots()
plot_precision_recall(y_true, y_pred, ax=ax)
from sklearn.metrics import average_precision_score
avg_precision = average_precision_score(y_true, y_pred_pos)
```

### When to use it

- when your data is **heavily imbalanced**.
- when you **care more about positive than negative class**.
- when you want to **choose the threshold** that fits the business problem.
- when you want to **communicate precision/recall decision** to other stakeholders

## 12. Cohen Kappa Metric

In simple words, Cohen Kappa tells you how much better is your model over the random classifier that predicts based on class frequencies.

To calculate it one needs to calculate two things: “observed agreement” (po) and “expected agreement” (pe). **Observed agreement** (po) is simply how our classifier predictions agree with the ground truth, which means it is just **accuracy**. The **expected agreement** (pe) is how the predictions of the random classifier that samples according to class frequencies agree with the ground truth, or **accuracy of the random classifier**.

From an interpretation standpoint, I like that it extends something very easy to explain (accuracy) to situations where your dataset is imbalanced by incorporating a baseline (dummy) classifier.

```text
K = (Po - Pe) / (1 - Pe)
```

### How to compute

```python
from sklearn.metrics import cohen_kappa_score
cohen_kappa = cohen_kappa_score(y_true, y_pred_class)
```

### When to use it

This metric is not used heavily in the context of classification. Yet it can work really well for **imbalanced problems** and seems like **a great companion/alternative to accuracy**.

## 13. Matthews Correlation Coefficient

It's a **correlation between predicted classes and ground truth**. It can be calculated based on values from the confusion matrix. Alternatively, you could also calculate the correlation between `y_true` and `y_pred`.

```text
MCC = TP*TN - FP*FN / ((TP+FP)(TP+FN)(TN+FP)(TN+FN))
```

### How to compute

```python
from sklearn.metrics import matthews_corrcoef

y_pred_class = y_pred_pos > threshold
matthews_corr = matthews_corrcoef(y_true, y_pred_class)
```

### When to use it

- When working on imbalanced problems,
- When you want to have something easily interpretable.

## 14. Log loss

Log loss is often used as the **objective function** that is optimized under the hood of machine learning models. Yet, it can also be used as a performance metric.

Basically, we calculate the difference between ground truth and predicted score for every observation and average those errors over all observations. For one observation the error formula reads:

```text
logloss = - (y_true * log(y_pred) + (1 - y_true)*log(1 - y_pred))
```

Model gets punished very heavily when we are certain about something that is untrue. For example, when we give a score of 0.9999 to an observation that is negative our loss jumps through the roof. That is why sometimes it makes sense to clip your predictions to decrease the risk of that happening.

### How to compute

```python
from sklearn.metrics import log_loss
loss = log_loss(y_true, y_pred)
```

### When to use it

Pretty much always there is a performance metric that better matches your business problem. Because of that, I would use log-loss as an objective for your model with some other metric to evaluate performance.

## 15. Brier score

It is a measure of how far your predictions lie from the true values. For one observation it simply reads:

```text
brierloss = (y_pred - t_true)^2
```

Basically, it is a **mean square error** in the probability space and because of that, it is usually used to calibrate probabilities of the machine learning models.

### How to compute

```python
from sklearn.metrics import brier_score_loss
brier_loss = brier_score_loss(y_true, y_pred_pos)
```

### When to use it

When you care about **calibrated probabilities**.
