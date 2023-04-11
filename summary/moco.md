# Moco
- Title: Momentum Contrast for Unsupervised Visual Representation Learning
- Publication: CVPR, 2020
- Link: [[paper](https://arxiv.org/pdf/1911.05722.pdf)] [[code](https://github.com/facebookresearch/moco/blob/3631be074a0a14ab85c206631729fe035e54b525/moco/builder.py#L6)]

## Abstract
- keywords
  - negative samples are encoded in queue (dynamic dictionary)
  - momentum update with the query encoder
- methods
  - moco trains a visual representation encoder by matching an encoded query q to a dictionary of encoded keys using a contrastive loss
  - larger dictionary size than batch size test !
<img width="300" alt="img1" src="https://user-images.githubusercontent.com/87194339/212867164-3f9f95e8-af8f-488d-bb3b-a301eb7a8095.png"> 

- constrastive loss function (InfoNCE)
<img width="200" alt="img2" src="https://user-images.githubusercontent.com/87194339/212869520-a47e9c42-742c-4765-b1f2-da4db0c2350e.png">



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
