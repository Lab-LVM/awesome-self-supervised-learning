# SimCLRv2
 
- Title: Big Self-Supervised models are Strong Semi-Supervised Learners
- Publication: NeurIPS, 2020
- Link: [[paper](https://arxiv.org/abs/2006.10029v2)] [[code](https://github.com/google-research/simclr)]

![simclrv2_1](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/38720006-2b4a-44c6-bed2-1338c7de9a9f)

## Main findings & Contribution
- for semi-supervised learning via the task-agnostic use of unlabeled data
  -  the fewer the labels, the more benefit from a bigger model
- with the task-specific use of unlabeled data, the predictive performance improve and transfer into a smaller network
- deeper projection head
  -  improve semi-supervised performance when fine-tuning from a middle layer of the projection head

## Method
![simclrv2_2](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/3a02d8de-e2fc-4543-bb44-eeb922de7fb5)
1. unlabeled data is used in a task-agnostic way
 - for general representation via unsupervised pretraining
 - general representations are adapted for a specific task via supervised fine-tuning
2. unlabeled data is used in a task-specific way
 - for improving predictive performance & obtaining a compact model
3. train Student networks on the unlabeled data with imputed labels from the fine-tuned Teacher network
Summarize : pretrain → fine-tune → distill

## Experiments
#### Bigger Models Are More Label-Efficient
<img width="580" alt="simclrv2_3" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/72e43d9d-c7a7-41a7-893e-582ca7d2ba35">

 - increase width & depth, using SK → improve performance
 
<img width="566" alt="simclrv2_4" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/17cb3161-7e56-45fc-87f4-362fa8ddbdf4">

 - bigger models are more label-efficient
 - gains → larger for semi-supervised learning

#### Bigger/Deeper Projection Heads Improve Representation Learning
<img width="425" alt="simclrv2_5" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/f01f069c-9a4e-456b-a585-80a6fb120da3">

- deeper projection head during pretraining is better
- fine-tuning from the first layer is better than fine-tuning from the input (0th layer)
- bigger ResNets, improvements from having a deeper projection head are smaller

#### Distillation Using Unlabeled Data Improves Semi-Supervised Learning
<img width="573" alt="simclrv2_6" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/ca00a15e-2e5e-4be7-9d45-a8478f016c08">

- Student model has Smaller, Same architecture with Teacher model → distillation improve model efficiency

## Reference
```tex
@article{DBLP:journals/corr/abs-2006-10029,
  author    = {Ting Chen and
               Simon Kornblith and
               Mohammad Norouzi and
               Geoffrey E. Hinton},
  title     = {Big Self-Supervised models are Strong Semi-Supervised Learners},
  journal   = {CoRR},
  volume    = {abs/2006.10029},
  year      = {2020},
  url       = {https://arxiv.org/abs/2006.10029v2},
  eprinttype = {arXiv},
  eprint    = {2006.10029v2},
  timestamp = {Mon, 26 Oct 2020 03:09:28 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2006-10029.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
