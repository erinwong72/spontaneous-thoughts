---
theme: simple
---
# Physics-Informed Neural Networks
by Erin Wong

---
## Contents
1. Background
2. 
3. 
---
# 1. Background
---
## What are physics-informed neural networks (PINNs)?
1) **Traditional physics**: parameterization of physics models to best fit the problem using known physics equations
2) **Data-driven** approach: learning the model purely using supervised learning trained on large amounts of data

![[Pasted image 20230902120837.png|475]] <!-- element class="fragment" data-fragment-index="3" -->

notes: PINNs use both data and known physics equations to learn the model. This allows for training with less data while creating consistent and applicable models that agree with the physics involved with the problem.

---
## Limitations of purely data-driven approaches
The biggest limitation is the **data**, as it’s often noisy and may only represent a very small portion of the whole domain → overfitting.

**Regularization** is often employed to combat this problem.

[insert self-made image] ![[Pasted image 20230902122239.png]]
notes: Regularization such as L2 works through penalizing large weights in the network, discouraging the model from overfitting. But, the data still remains a problem--if it’s only a small subset of the domain, the model won’t be able to extrapolate or generalize to data beyond what has been given.

---
## How do PINNs address this problem?
In a way, they are also a type of **regularization**, ensuring that the model complies with the physics governing the situation.

The special part of a PINN that makes it different from a regular neural network are the *loss* function(s).
1) **Physics** loss term
2) **Data** loss term

notes: If we want to regularize the model based on specific physics equations governing the situation, such equations usually involve derivatives with respect to some variable. Based on the governing equations, some loss can be determined based on the relationship between the first and nth order derivative, and implemented as the physics loss. 

The data loss term would then just be a standard loss like MSE between predicted and ground truth values.