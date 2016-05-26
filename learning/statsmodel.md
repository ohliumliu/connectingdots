### Statsmodel: statistical package in python
* Import
```python
import statsmodels.api as sm
import statsmodels.formula.api as smf
```
Here `smf` holds a lot of models.

* Usage
```python
smf.ols("Y~U+V", data = df).fit() # linear model with two parameters. + doesn't mean addition here. It means including a feature.
```
Here a model was generated using data from a data frame. The column name was used in the expression to construct the model. 
This is from R. 

The expression is using Patsy. For example, Y~U+V-1 means two parameter linear model without intercept. Y~np.log(X) is actually a
log linear relationship.

Use `dir(smf)` to check available models. 

For example, logit is continuous Logistic function. In Sklearn, in contrast, Logistic
has to be a classifier.
