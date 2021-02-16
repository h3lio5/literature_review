# Summary
* This paper provides a framework of unsupervised learning visual representation as a dynamic dictionary look-up. The dictionary is structured as a large FIFO queue of encoded representations of data samples. 
* The approach uses a contrastive learning loss objective where the contrastive losses measure the similarities of sample pairs in a representation space. Instead of matching an input to a fixed target, in contrastive loss formulations the target can vary on-the-fly during training and can be defined in terms of the data representation computed by a network.
* The negative samples are obtained from the dynamic dictionary (and represent encodings of previous mini-batches) and the positive samples are obtained encoding a "view" of the input image. The query sample is a different view of the same input image but formed using a different data augmentation technique.
* The choice of the key encoder is a moving-average (momentum update) of the query encoder because it allows the dictionary keys to be consistent throughout the training. Using a fixed key encoder like that in memory-bank approaches will lead to the dictionary representation to be inconsistent and training a key encoder end-to-end will restrict the size of negative samples to the size of mini-batch.
* Transformations applied: a 224×224-pixel crop is taken from a randomly resized image, and then undergoes random color jittering, random horizontal flip, and random grayscale conversion.
# Strengths
* This framework is general enough to be applicable with different pretext tasks.
* MoCo can outperform its supervised pre-training counterpart in 7 detection/segmentation tasks on PASCAL VOC, COCO, and other datasets, sometimes surpassing it by large margins.
# Some useful insights
* Batch normalization prevents the model from learning good representations as the model appears to "cheat" in the pretext task and easily finds a low-loss solution. This is possibly because the intra-batch communication among samples (caused by BN) leaks information. Shuffling the order of the mini-batch samples of the key encoder and re-shuffling them again after encoding, samples to the query encoder are not shuffled at all.