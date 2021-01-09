# Summary
* Present the online meta-learning problem setting, where the agent simultaneously uses past experiences in a sequential setting to learn good priors, and also adapt quickly to the current task at hand.
* Drawing ideas from the Follow the Leader (FTL) method -- which was a successful algorithm in online-learning setting -- and meta-learning, the paper proposes a practical algorithm, Follow the Meta Leader(FTML), that learns to fully utilize the structure across tasks and extract information from data to learn new tasks with only a few examples.
* In other words, FTML is just an extension of MAML algorithm to the online-learning setting.
# Strengths
* Provides a O(log(T)) theoretical guarantee for regret with one additional higher order smoothness assumption.
* Their results on the MNIST experiment show that FTML can learn new tasks more and more effectively as new task is recieved, demonstrating effective forward transfer.
* The algorithm is fairly simple to implement.
# Weakness
* The FTML algorithm stores all the past experience making it difficult to scale to larger datasets.
# Future directions
* Understand the interplay between limited memory and catestrophic forgetting.
* Use more powerful update rules in the inner optimization steps.
* Explore alternative approaches like Mirror Descent which does not store all the past experience, making it computationally cheaper and amenable to scale to larger datasets.
