* Skewed group: rare class. Small validation error may not be an indication of good performance. 
This is often used as an example in Baysian method.
* Precision/Recall:

||Prediction=1|Prediction=0|
|----|----|----|
|Actual=1|True positive|False negative|
|Actual=0|False positive|True negative|

  * Recall:  true positive as a fraction of all positive cases. Also called sensitivity.
  * Precision: True positive as a fraction of all cases that is predicted to be positive. 
  * Specificity: true negative as a fraction of all negative cases.
  There is always a trade off between precision and recall, determined by the threshold (for logistic regression problems).
  When threshold is increased, precision is decreasing while recall is increasing.
* How to balance precision and recall.
  * Use the F score: precision and recall 调和平均值. 1/precision: how many cases that are predicted positive 
  needed to have one true positive. 1/recall: how many true cases needed to have one true positive. 
  We want to balance 1/precision and 1/recall, hence the average. We also want 1/precision and 1/recall to be close to 1.

 
