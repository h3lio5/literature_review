# Summary 
* Classic pre-training approach has no guarantee of learning an initialization that is good for fine-tuning, and ad-hoc tricks are required for good performance, whereas meta-learning approaches like MAML optimize for generalization by performing gradient descent on meta-test loss, akin to cross-validation.
* MAML requires the meta-training step to differentiate through the entire inner optimization procedure (adaptation step) which does not scale with the number of inner update steps because it requires computing higher-order derivates. However, this scalability issue can be circumvented by completely ignoring the higher-order derivates, giving us a first-order MAML approach.
* This paper proposes an algorithm, Reptile, which is much similar to FOMAML in terms of computation and performance.
* By using a Taylor series expansion to approximate the update performed by Reptile and MAML, they show that both the algorithms are similar:
  * minimize the expected loss (joint training).
  * maximize the within-task generalization: specifically, it maximizes the inner product between the gradients on different minibatches from the same task.
* The paper also provides an informal argument, which is that Reptile finds a point that is close (in Euclidean distance) to all of the optimal solution manifolds of the training tasks.
* The paper also suggests that when doing stochastic gradient descent, we are automatically performing a MAML-like update that maximizes the generalization between different minibatches. This observation partly explains why fine tuning works well.
# Strengths
* The Reptile algorithm is much cheaper to train than the MAML algorithm for larger datasets.
* The Reptile algorithm does not need meta-training and meta-testing data splits, which is more similar to real world scenarios.
* It has nice theoretical guarantees that it will work similar to MAML.
* Reptile is not that sensitive to the inner loop hyperparameters, unlike FOMAML, whose performance significantly drops if mini-batches are selected the wrong way.
# Weakness
* It did not give good results in reinforcement learning setting.
* There was a considerable gap between the training and test loss.
* It does not fare well when momentum is enabled in the optimizers. Reptile works because sequential steps come from different mini-batches. With momentum, a mini-batch has influence over the next few steps, reducing this effect.
