# Structured Forests for Edge Detection

>[!summary]
>Predict segmentation masks given small areas, “patches” of the input image, using unsupervised learning to learn more variations in edges (no predefined classes of types of edges).

Novel part of method is **structured learning**: fancy term for using input/predicting output that has some explicit structure.
- Consider the structured output space that is dependent on a standard input space -- depends a lot on the nature of the training data because that will be treated as the “standard” space

Why use **random forest** models ([[decision trees]])?
- Each leaf node that contains a portion of the prediction $\hat{y}$ can store a *different* type of output → perfect for constructing a complex structured output
- Using the [[Decision Trees#^ccb62f|information gain criterion]] concept, can define a *generalized* information gain criterion that can represent a structured output space well (by leveraging randomness)


---
Source:
[1406.5549.pdf](https://arxiv.org/pdf/1406.5549.pdf)
