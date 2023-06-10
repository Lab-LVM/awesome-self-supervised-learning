# BYOL
 
- Title: Bootstrap Your Own Latent : A New Approach to Self-Supervised Learning
- Publication: arXiv, 2020
- Link: [[paper](https://arxiv.org/abs/2006.07733)] [[code](https://github.com/open-mmlab/mmselfsup)]

<img width="360" alt="BYOL_1" src="https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/411c38b0-553e-492c-a904-c9a8dce66f0f">

#### online & target networks
- online → predict the target network representation of the same image
- target → be updated with a slow-moving average of the online
#### without negative pairs

## Method
![BYOL_2](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/d410345d-4d91-4622-b467-74168ff8eec8)
- target network → provide the regression targets to train the online network

![BYOL_3](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/1d4fff17-71c5-499c-b80d-d4c3e61e883a)
- ξ [ksi] : exponential moving average of θ

1. image x → two augmentaed view v, v’
2. online network : v→ y_θ (= f_θ(v)) → z_θ (=g_θ(y_θ))
3. target network : v’ → y’_ξ (=f_ξ(v’)) → z’_ξ (=g_ξ(y’_ξ))
4. output : prediction q_θ(z_θ) of z’_ξ
5. l2_norm for q_θ(z_θ) & z’_ξ
6. (v’ → online network / v → target network) ⇒ compute L^~_θ,ξ
7. Total Loss = L_θ,ξ + L^~_θ,ξ
8. each training step → stochastic optimization step
9. end of training → only keep encoder f_θ

## Experiments
#### Deeper & Wider → better
![BYOL_4](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/19dbdb24-c202-47b5-956c-c81977abe17e)

#### Use the same fixed split of 1% and 10% of ImageNet labeled training data
![BYOL_5](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/33d38be6-18e5-4208-b5b3-911c3e4c2ea9)

#### Batch size & Image augmentations 
![BYOL_6](https://github.com/Team-Ryu/awesome-self-supervised-learing/assets/90434136/41125e32-7e32-4a78-86a1-20955605d318)

- Contrastive methods → rely on color distortion
- BYOL → keep any info captured by target into online to improve predictions
- not rely on negative pairs → remain stable (while decreasing the num of Batch size)

## Reference
```tex
@article{DBLP:journals/corr/abs-2006-07733,
  author    = {Jean-Bastien Grill and
              Florian Strub and
              Florent Altché and
              Corentin Tallec and
              Pierre H. Richemond and
              Elena Buchatskaya and
              Carl Doersch and
              Bernardo Avila Pires and
              Zhaohan Daniel Guo and
              Mohammad Gheshlaghi Azar and
              Bilal Piot and
              Koray Kavukcuoglu and
              Rémi Munos and
              Michal Valko},
  title     = {Bootstrap Your Own Latent : A New Approach to Self-Supervised Learning},
  journal   = {CoRR},
  volume    = {abs/2006.07733},
  year      = {2020},
  url       = {https://arxiv.org/abs/2006.07733},
  eprinttype = {arXiv},
  eprint    = {2006.07733},
  timestamp = {Thu, 10 Sep 2020 09:46:02 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2006-07733.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
