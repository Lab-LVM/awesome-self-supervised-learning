# SimCLRv2
 
- Title: Big Self-Supervised models are Strong Semi-Supervised Learners
- Publication: NeurIPS, 2020
- Link: [[paper](https://arxiv.org/abs/2006.10029v2)] [[code](https://github.com/google-research/simclr)]

## Main findings & Contribution
- for semi-supervised learning via the task-agnostic use of unlabeled data
  -  the fewer the labels, the more benefit from a bigger model
- with the task-specific use of unlabeled data, the predictive performance improve and transfer into a smaller network
- deeper projection head
  -  improve semi-supervised performance when fine-tuning from a middle layer of the projection head


## Reference
```tex
@article{DBLP:journals/corr/abs-2002-05709,
  author    = {Ting Chen and
               Simon Kornblith and
               Mohammad Norouzi and
               Geoffrey E. Hinton},
  title     = {Big Self-Supervised models are Strong Semi-Supervised Learners},
  journal   = {CoRR},
  volume    = {abs/2002.05709},
  year      = {2020},
  url       = {https://arxiv.org/abs/2006.10029v2},
  eprinttype = {arXiv},
  eprint    = {2006.10029v2},
  timestamp = {Mon, 26 Oct 2020 03:09:28 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2002-05709.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
