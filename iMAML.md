# Summary
* Despite its appealing properties, meta-learning an initialization requires backpropagation through the inner optimization process, i.e. backpropagating through the dynamics of gradient descent. 
* iMAML addresses two main issues encountered by MAML by decoupling meta-gradient computation and choice of inner level optimizer. 
  * <ins><b>Memory efficiency and scalability:</b></ins> By leveraging implicit differentiation approach, they derive an analytical expression for the meta (or outer level) gradient that depends only on the solution to the inner optimization and not the path it takes, eliminating the need to store the path, thereby making iMAML memory efficient and scalable to a large number of inner opt. steps.
  * <ins><u>Vanishing gradients</u></ins>: The dependence of the model-parameters on the meta-parameters shrinks and vanishes as the number of inner gradient steps grows, making meta-learning difficult. To overcome this limitation, the authors propose an l2 regularized algorithm, which encourages the model-parameters to remain close to meta-parameters.
# Strengths
* It achieves slightly better results on the few-shot classification task than the MAML (full GD) with significantly lower memory footprint — iMAML has constant space complexity while MAML has linear. However, the time consumption is nearly same for the same number of inner gradient steps.
* iMAML is agnostic to the inner optimization method used, as long as it can find an approximate solution to the inner-level optimization problem. This permits the use of higher-order methods, and in principle even non-differentiable optimization methods or components like sample- based optimization, line-search.
# Weakness
* Implementing the conjugate gradient descent algorithm to compute jacobian-vector product can be cumbersome.
