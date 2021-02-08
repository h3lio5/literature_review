# Summary
* In few-shot learning setting, the network might discard semantic information that is irrelevant for base classes but critical for novel classes. One way to recover this useful semantic information is to leverage representation techniques that do not use class labels like self-supervised learning.
* The key idea in SSL is to learn about statistical regularities within images, such as spatial relationship between patches, or its orientation, that might be a cue to semantics.
* This paper proposes a multi-task framework for few-shot setting, where the two tasks are standard meta-learning task and self-supervised learning task. The self-supervised learning loss acts as a data-dependent regularizer for representation learning.
* The main focus of this paper: self-supervision can, in fact, augment standard supervised training for few-shot transfer learning in the low training data regime without relying on any external dataset.
* The benefits of self-supervision increase with the difficulty of the task, for example when training from a smaller base dataset, or with degraded inputs such as low resolution or greyscale images.
* The paper also proposes a simple method to select images for SSL from a large, generic pool of unlabeled images in a dataset dependent manner. For this, they train a binary classifier to separate source (base) images from unlabeled images from the generic pool. Images with high P(source)/P(pool) are selected.

# Strengths
* Even with no additional training data, adding a self-supervised task as an auxiliary task improved the performance.
* Adding more unlabelled images chosen from the same domain as the base classes improves performance on small datasets in novel domains.
* Models trained with self-supervision tend to avoid accidental correlation of background features to class labels. This correlation is particularly true when the dataset consists of natural images.
