### ROC curve and its cousin in finance
ROC curve is a plot of true positive rate (TPR) vs false positive rate (FPR).
* It should be monotonous.
* We would like it to be "curving up".

Its cousin in finance is return vs volatility. 

To get the best threshold for our model, we would like to find the northwest corner of the ROC.
But in reality, we also need to consider the cost function. For a fixed cost, TPR and FPR lies on a line. In fiance, the
corresponding curve is called utility curve. For constant utility, return vs volatility is a curve due to margin effect. Either
way, we want to find the utility curve that is tangent to the ROC.
