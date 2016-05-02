* Classification problem
* Use segments of straight lines (either along x or y) to split the data. When it is in use, one would get a decision tree.
* Use entropy the help decide how to split in each step.
  * entropy = sum -prob(i)*log(prob(i)) (common in statistical physics)
  * information gain = entropy before splitting - weighted average entropy after splitting
  * maximize information gain in each step. 
  * Another metrics of information gain is gini, not entropy.
