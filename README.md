# Performance_Evaluation_Linear-Regression
Evaluating different models based on raw data,binary,muti class

Common Techniques for evaluating performance:

- Visually observe using Plots
- Residual Histograms
- Evaluate with Metrics like Root Mean Square Error (RMSE)

# Binary Classifier Metrics
positive = number of actual positives (count)
negative = number of actual negatives (count)
True Positive = tp = how many samples were correctly classified as positive (count)
True Negative = tn = how many samples were correctly classified as negative (count)
False Positive = fp = how many negative samples were mis-classified as positive (count)
False Negative = fn = how many positive samples were mis-classified as negative (count)

### True Positive Rate (TPR, Recall, Probability of detection) = True Positive/Positive
How many positives were correctly classified? (fraction)
Recall value closer to 1 is better. closer to 0 is worse
Example: Radar Operator watching the skies for enemy planes.

Positive Class = Enemy Plane

Negative Class = Friendly Plane

True Positive Rate or Probability of detection – is the probability of correctly classifying an enemy plane </i>

### True Negative Rate = True Negative/Negative
How many negatives were correctly classified? (fraction)
True Negative Rate value closer to 1 is better. closer to 0 is worse
True negative rate – is the probability of correctly classifying a friendly plane

### False Positive Rate (FPR, Probability of false alarm) = False Positive/Negative
How many negatives were mis-classified as positives (fraction)
False Positive Rate value closer to 0 is better. closer to 1 is worse
Another name for this is Probability of false alarm – is the probability of mis-classifying a friendly plane as an enemy plane

### False Negative Rate (FNR, Misses) = False Negative/Positive
How many positives were mis-classified as negative (fraction)
False Negative Rate value closer to 0 is better. closer to 1 is worse
False Negative Rate - is the probability of mis-classifying an enemy plane as a friendly plane

### Precision = True Positive/(True Positive + False Positive)
How many positives classified by the algorithm are really positives? (fraction)
Precision value closer to 1 is better. closer to 0 is worse
Precision would go up as enemy planes are correctly identified, while minimizing false alarm

### Accuracy = (True Positive + True Negative)/(Positive + Negative)
How many positives and negatives were correctly classified? (fraction)
Accuracy value closer to 1 is better. closer to 0 is worse
Accuracy would go up when enemy planes and friendly planes are correctly identified

### F1 Score = harmonic mean of Precision and Recall = 2*Precision*Recall / (Precision + Recall)
F1 Score closer to 1 is better. Closer to 0 is worse.
Reference:
** Harmonic Mean - https://en.wikipedia.org/wiki/Harmonic_mean
** Confusion Matrix - https://en.wikipedia.org/wiki/Confusion_matrix

# Binary Classifier Raw Score Evaluation
The actual output of many binary classification algorithms is a prediction score. The score indicates the system’s certainty that the given observation belongs to the positive class

To convert this raw score to a positive or negative class, we need to specify a cut-off. A sample with score greater than the cut-off is classified as positive class and a sample with score less than the cut-off is classified as negative class.

We need to now assess how algorithm would behave under different classification thresholds. Instead of manually performing this step, we can compute "AUC" metric. AUC refers to Area Under Curve. The curve here refers to the plot that has Probability of False Alarm (False Positive Rate) in X-Axis and Probability of Detection (Recall) in Y-Axis. By plotting False Alarm vs Recall at different cut-off thresholds, we can form a curve. AUC measures the area under this curve.

### Common Techniques for evaluating performance:

** Visually observe raw score using Plots
** Evaluate Area Under Curve (AUC) Metric
Reference:
https://en.wikipedia.org/wiki/Receiver_operating_characteristic

AUC is a different type of metric. It measures the ability of the model to predict a higher score for positive examples as compared to negative examples. Since AUC is independent of the selected threshold, you can get a sense of the prediction performance of your model from the AUC metric without picking a threshold.

** Reference:
https://docs.aws.amazon.com/machine-learning/latest/dg/binary-classification.html

In this example, let's look at how to compute AUC metric from raw scores and use that to compare model performance

# Evaluating Performance of a Multi-class Classifier
Multi-class Model is used for predicting one of many possible outcomes

Exam Grades: A, B, C, D Dress Size: Small, Medium, Large, X-Large

Typical metrics used in multiclass are the same as the metrics used in the binary classification case. The metric is calculated for each class by treating it as a binary classification problem after grouping all the other classes as belonging to the second class. Then the binary metric is averaged over all the classes to get either a macro average (treat each class equally) or weighted average (weighted by class frequency) metric.

** Reference:
https://docs.aws.amazon.com/machine-learning/latest/dg/multiclass-classification.html

To find out how good the model predictions are, we need to check predictions against previously unseen samples that were not used for training. Usually, 30% of the available samples are reserved for testing while remaining 70% of samples are used for training.

By comparing predicted values against known results in test data, we can assess overall model performance

Common Techniques for evaluating performance:

- Visually observe using Plots
- Confusion Matrix
- Evaluate with Metrics like Recall, Precision, F1 Score and so forth
While Plots are good for humans to visually observe the results, we often need a single metric that can indicate quality of a model. This can be useful for programmatically identifying which model is performing better (for example: using automatic model tuning to select the best performing model)

** Reference:
https://docs.aws.amazon.com/machine-learning/latest/dg/multiclass-classification.html
Confusion Matrix:
https://en.wikipedia.org/wiki/Confusion_matrix
