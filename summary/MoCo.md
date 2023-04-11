# MoCo v1
- Title: Momentum Contrast for Unsupervised Visual Representation Learning
- Publication: CVPR, 2020
- Link: [[paper](https://arxiv.org/pdf/1911.05722.pdf)] [[code](https://github.com/facebookresearch/moco/blob/3631be074a0a14ab85c206631729fe035e54b525/moco/builder.py#L6)]

## Abstract
- keywords
  - negative samples are encoded in queue (dynamic dictionary)
  - momentum is updated with the query encoder
- methods
  - MoCo trains a visual representation encoder by matching an encoded query q to a dictionary of encoded keys using a contrastive loss
  - The size of the dictionary is more important than the batch size.
<img width="300" alt="img1" src="https://user-images.githubusercontent.com/87194339/212867164-3f9f95e8-af8f-488d-bb3b-a301eb7a8095.png"> 

- constrastive loss function (InfoNCE)
<img width="200" alt="img2" src="https://user-images.githubusercontent.com/87194339/212869520-a47e9c42-742c-4765-b1f2-da4db0c2350e.png">
- To achieve lower loss, the value of positive sample should be smaller. (It means numerator should be smaller)

## MoCo vs SimCLR
- MoCo is an asymmetric structure, and uses the values stored in the dynamic dictionary as negative samples
- SimCLR, on the other hand, has a symmetrical structure, and uses all images except itself in the batch as negative samples.
- So MoCo doesn't affected by batch size, but SimCLR doesn't.
<img width="600" alt="img1" src="./img/moco_vs_simclr.png"> 

## Conceptual comparison of three contrastive loss mechanisms
- end-to-end method calculates the gradient by back-propagation in both directions, and its performance is determined by the batch size.
- memory bank method uses 'memory bank' to store and compare old data using fixed-sized memory.
- MoCo uses momentum to create a dynamic queue and use it to learn the model.
<img width="600" alt="img1" src="./img/contrastive_loss_mechanisms.png"> 

## Pseudocode of MoCo in a PyTorch-like style
1. Initialize parameters from momentum encoder to parameters from encoder
2. Augmentation and delivery of images to be placed on both sides
* &ensp;augmentation: resize&crop, color jittering(lightness, saturation), horizontal flip, grayscale conversion
3. Pass the previously augmented data through the encoder and the moment encoder, respectively
* &ensp;The Momentus Encoder does not calculate gradient
4. Calculate logit for positive pair and negative pair (normalization), InfoNCE loss calculation
5. Update the encoder by backpropagating, and update the moment encoder by multiplying the weight by the existing moment parameter m.
6. Add the key of this mini batch in the queue, and if the dictionary size is overflowing, pop the oldest key to update the memory bank
<img width="600" alt="img1" src="./img/pseudocode_of_moco.png"> 


## Comparison of three contrastive loss mechanisms
* The k on the x-axis represents the number of negative samples
* End-to-end needs to increase the batch size to secure the number of negative samples, but due to memory limitations, it is not easy to grow above 1024
* MoCo method shows better accuracy than end-to-end or memory bank
* MoCo method can improve performance by increasing memory bank size
* <img width="600" alt="img1" src="./img/comparison_of_contrastive_loss.png"> 

## Reference
```tex
@article{DBLP:journals/corr/HeZRS15,
  author    = {Kaiming He and
               Haoqi Fan and
               Yuxin Wu and
               Saining Xie and
               Ross Girshick},
  title     = {Momentum Contrast for Unsupervised Visual Representation Learning},
  journal   = {CVPR},
  year      = {2020},
  url       = {https://arxiv.org/pdf/1911.05722},
  eprinttype = {arXiv},
  eprint    = {1911.05722},
}
```
