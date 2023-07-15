# PIRL
 
- Title: Self-Supervised Learning of Pretext-Invariant Representations
- Publication: CVPR, 2020
- Link: [[paper](https://openaccess.thecvf.com/content_CVPR_2020/papers/Misra_Self-Supervised_Learning_of_Pretext-Invariant_Representations_CVPR_2020_paper.pdf)] [[code](https://github.com/facebookresearch/vissl)]

## Learn Invariant Representations rather than convariant ones
<img width="500" alt="PIRL1" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/94c26c1d-db55-415b-98aa-8bea317f2b2c">

##
<img width="500" alt="PIRL2" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/e7c48a33-6d21-4fac-9539-bcb34a75136b">

### Convolutional network
- ResNet-50
1. extract 9 patches from image I
2. compute an image representations for each patches by extracting activations from the res5 layer of the ResNet-50 and average pool
3. apply a linear projection to obtain 128-dimensional patch representations
4. concatenate the patch representations in random order and apply a second linear projection on the result
5. desire to remain as close as possible to the covariant pretext task

### Loss function
<img width="250" alt="PIRL3" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/6df4333e-b6ba-4f76-930b-21d406a6e40a">

- encourage the presentation of image and transformed counterpart to be similar / with other images to be dissimilar
<img width="250" alt="PIRL4" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/7bf46067-7bc1-47dc-9491-66b5b448f4d7">

- NCE (Noise Contrastive Estimator)
<img width="250" alt="PIRL5" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/7725f11d-df0f-467b-a475-d036d3d79999">

## Result
<img width="500" alt="PIRL6" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/7b79d91d-b06d-4ee2-ac84-26c46f9dda63">
<br>
<img width="500" alt="PIRL7" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/9c275713-f295-4836-b6cc-a30830c0ab4f">
<br>
<img width="500" alt="PIRL8" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/0b52c2a8-89ab-44ac-865e-4c31d616b00d">

## Reference
```tex
@article{DBLP:journals/corr/abs-1912-01991,
  author    = {Ishan Misra and
              Laurens van der MAaten},
  title     = {Self-Supervise Learning of Pretext-Invariant Representations},
  journal   = {CVPR},
  volume    = {abs/1912.01991},
  year      = {2020},
  url       = {https://arxiv.org/abs/1912.01991},
  eprinttype = {arXiv},
  eprint    = {1912.01991},
  timestamp = {Wed, 4 Dec 2019 13:59:48 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-1912-01991.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
