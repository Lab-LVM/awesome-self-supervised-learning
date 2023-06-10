# SEER
 
- Title: Self-supervised Pretraining of Visual Features in the Wild
- Publication: arXiv, 2021
- Link: [[paper](https://arxiv.org/abs/2103.01988)] [[code](https://github.com/facebookresearch/vissl)]

<img width="304" alt="SEER_1" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/ed306761-263e-4817-b184-72a93f6fc030">

## Can we achieve good performance by pretraining on an extremely large collection of random, uncurated and unlabeled images?
- pretraining high capacity models on billions of random internet images
- not rely on image meta-data or any form of weak/manual annotations

## Method
#### SwAV
![SEER_2](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/45e162ec-7cf7-4d9e-a218-3015aaef625a)

1. given a batch of B images, each images x_i → augmented x_i1, x_i2 
2. with a convnet → (f_11, …, f_B1) , (f_12, …, f_B2)
3. each set of features → assigned independently on the cluster prototypes (using Optimal Transport solver)
4. swap between the two sets : y_i1 (cluster assignment of x_i1) has to be predicted from f_i2 (feature representation of x_i2)
<img width="229" alt="SEER_4" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/273a9b2e-d057-4aee-b04b-1b99aacd20cc">

5. cluster prediction loss : cross entropy between the cluster assignment & a softmax of the dot products of f and all prototypes v_k

![SEER_5](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/5d17a890-36d5-4512-8830-2dd95a6afbb1)

#### RegNetY
- efficient in terms of both memory and runtime
- RegNetY : standard RegNets + Squeeze-and-excitation op
- 4 stages → stage depths (2, 7, 17, 1) & stage widths (528, 1056, 2904, 7392)

## Experiments
#### 84.2% top-1 accuracy on ImageNet → +1% from SimCLRv2
<img width="588" alt="SEER_6" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/594d3c1c-be10-4f6c-8043-4b88ae142684">

#### impact of model capacity : more significant on Pretrained than from Scratch
<img width="289" alt="SEER_7" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/c326d89e-1820-4660-8957-411fd5a27ab2">

#### achieve 77.9% top-1 accruacy with only 10% of ImageNet
<img width="296" alt="SEER_8" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/f0935ac6-14c6-42f5-9057-3a04951345d5">

## Reference
```tex
@article{DBLP:journals/corr/abs-2103-01988,
  author    = {Priya Goyal and
              Mathilde Caron and
              Benjamin Lefaudeux and
              Min Xu and
              Pengchao Wang and
              Vivek Pai and
              Mannat Singh and
              Vitaliy Liptchinsky and
              Ishan Misra and
              Armand Joulin and
              Piotr Bojanowski},
  title     = {Self-supervised Pretraining of Visual Features in the Wild},
  journal   = {CoRR},
  volume    = {abs/2103.01988},
  year      = {2021},
  url       = {https://arxiv.org/abs/2103.01988},
  eprinttype = {arXiv},
  eprint    = {2103.01988},
  timestamp = {Fri, 5 Mar 2021 13:53:36 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2103-01988.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
