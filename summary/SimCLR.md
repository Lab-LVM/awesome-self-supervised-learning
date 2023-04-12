# SimCLR
 
- Title: A Simple Framework for Contrastive Learning of Visual Representations
- Publication: ICML, 2020
- Link: [[paper](https://arxiv.org/abs/2002.05709)] [[code](https://github.com/sthalles/SimCLR)]

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
