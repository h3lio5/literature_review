# Summary
* MAML is a meta-learning algorithm that is model-agnostic,in the sense that it is compatible with any model trained with gradient descent and applicable to a variety of different learning problems, including classification, regression, and reinforcement learning.
* The key idea of MAML is to train the model’s initial parameters such that the model has maximal performance on a new task after the parameters have been updated through one or more gradient steps computed with a small amount of data from that new task.
* The paper presents MAML from two different standpoints:
  * Feature learning: it can be viewed as building an internal representation that is broadly suited for many tasks. It explicitly optimizes the model for fast adaptability; intuition behind this approach is that some internal representation are more transferrable than others.
  * Dynamical systems: it can be viewed as maximizing sensitivity of the loss functions of new tasks with respect to the parameters such that small changes in the parameters will produce large improvements on the loss function of any new task, when altered in the direction of the gradient of that loss.
# Strengths
* As the name suggests, MAML can be applied to any model architecture amenable to gradient based learning.
* It is very simple to implement using the modern deep learning packages like Pytorch, Tensorflow, Mxnet, etc.
# Weakness
* It is not scalable with the number of inner loop updates as the outer loop update(meta-training) requires it to differentiate through the entire inner optimization procedure.
