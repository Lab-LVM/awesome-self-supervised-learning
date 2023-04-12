# SimCLR
 
- Title: A Simple Framework for Contrastive Learning of Visual Representations
- Publication: ICML, 2020
- Link: [[paper](https://arxiv.org/abs/2002.05709)] [[code](https://github.com/sthalles/SimCLR)]

## Simple, but Outperform
![Top-1 accuracy](https://user-images.githubusercontent.com/90434136/231516205-aa947e1a-4751-4962-bb88-acb374640db9.png)

## Major Components
- composition of multiple data augmentations
- learnable nonlinear transformation
- contrastive cross entropy loss
- larger batch sizes and longer training

## Contrastive Learning Framework
![Framework](https://user-images.githubusercontent.com/90434136/231513564-fd0985c7-1933-4125-9bf5-08d95a1b780f.png)
- maximize agreement between differently augmented views of the same data
1. Data augmentation : cropping, color distortions, Gaussian blur...
2. Neural network base encoder f(·) : extract representation vectors -> adopt ResNet
3. Small neural network projection head g(·) : use MLP with 1 hidden layer
4. Contrastive Loss function : Maximize agreement

# Data Augmentation for Contrastive Representation Learning
## Composition of data augmentation operations
![Top-1 accuracy](https://user-images.githubusercontent.com/90434136/231517531-9da6ddfa-b63d-415c-a794-6f77abdc4868.png)
- crucial for learning good representations
- spatial/geometric transformation : cropping, resizing, horizontal flipping, rotation, cutout
- appearance transformation : color distortion, color dropping, brightness, contrast, saturation, hue, Gaussian blur, Sobel filtering

## Composing Augmentations
![Color Crop](https://user-images.githubusercontent.com/90434136/231517965-c384093a-5e52-4cd8-98f1-3ff33881b4a5.png)
- no single transform suffices to learn good representations
- contrastive prediction task harder, but quality of representation improves dramatically
- stand out : random cropping & color distortion

# Architectures for Encoder and Head
## Unsupervised contrastive learning benefits (more) from bigger models
![Unsupervised contrastive learning benefits more](https://user-images.githubusercontent.com/90434136/231518790-edebb9d8-aa2a-47e0-9120-99a4eae04490.png)
- unsupervised learning benefits more from bigger models than its supervised counterpart

## A nonlinear projection head improves the representation quality of the layer before it
![nonlinear projection head improves the representation quality](https://user-images.githubusercontent.com/90434136/231519264-fadd47df-f06b-425e-8a11-c57c3901896d.png)
- using non-linear projection : better than linear projection & no projection

# Loss Functions and Batch Size
## Contrastive learning benefits (more) from larger batch sies and longer training
![benefits from larger batch sies and longer training](https://user-images.githubusercontent.com/90434136/231520026-b82714ea-ccbd-47b7-b708-806736320b97.png)
- larger batch sizes & training longer : provide more negative examples -> signifiant advantage 

## Reference
```tex
@article{DBLP:journals/corr/abs-2002-05709,
  author    = {Ting Chen and
               Simon Kornblith and
               Mohammad Norouzi and
               Geoffrey E. Hinton},
  title     = {A Simple Framework for Contrastive Learning of Visual Representations},
  journal   = {CoRR},
  volume    = {abs/2002.05709},
  year      = {2020},
  url       = {https://arxiv.org/abs/2002.05709},
  eprinttype = {arXiv},
  eprint    = {2002.05709},
  timestamp = {Fri, 14 Feb 2020 12:07:41 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2002-05709.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
