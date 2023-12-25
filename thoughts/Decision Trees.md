# Decision Trees
Training is governed by an **information gain criterion** at every node that decides what variable to use to split the data based on calculating the information gain for each variable and choosing the one with the *largest*.

What is information gain? ^ccb62f
- *Reduction* in the **entropy** of a variable that would occur if the dataset was split using that variable
	- Entropy = amount of information is in a variable = probability distribution of a variable (predictability)
		- Usually, **Shannon entropy** is used
	- Large entropy = balanced distribution (each value carries lower probability) = unpredictable

So, decision trees are constructed from the training dataset by splitting the data this way (choosing variables) until maximum depth is reached or information gain falls below a certain threshold value (can’t get any more information by splitting further).



---
Sources:
[Information Gain and Mutual Information for Machine Learning - MachineLearningMastery.com](https://machinelearningmastery.com/information-gain-and-mutual-information/#:~:text=It%20is%20commonly%20used%20in,into%20groups%20for%20effective%20classification.)