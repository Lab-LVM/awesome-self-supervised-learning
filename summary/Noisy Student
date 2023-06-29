# Self-training with Noisy Student
- Title: Self-training with Noisy Student improves ImageNet classification
- Publication: CoRR, 2019
- Link: [[paper](https://arxiv.org/pdf/1911.04252.pdf)] [[code](https://github.com/google-research/noisystudent)]

## Abstract
- Use the student model for self-training and distillation, but student model is larger than teacher model and includes noise.
- Create a student model by combining labels and pesudo labeled images using a larger model.

## How to improve self-training and distillation?
1. Set the size of the student model equal to or larger than the size of the teacher model.
  - Learn better in large dataset than small dataset.
2. Add noise to the student model to make learning more difficult from the pseudo label.
  - Learn to be a general model.

## How to apply noise to the student model
- dropout, static depth, and data augmentation (rand augmentation): to make learning more general than the teacher model.
- Stochastic depth: Randomly reducing depth in the learning phase.
  - If it is set to kill the depth, just let it flow without doing any operations.
  - Rand Augment: You only need to determine the number of image transformations to be applied (N) and the strength of the transformations (M).

## Algorithm of Noisy Student Training
- Use both labeled and unlabeled images.
1. Learn the teacher model with a labeled image. (loss function: cross entropy)
2. Teacher model creates pseudo label for unlabeled image.
3. Learn the student model using images 1 and 2.
4. Reuse the student model as the teacher model, return to number 2 and repeat.
<img width="300" alt="img1" src="./img/noisy student_algo.png">

- The entire algorithm is expressed as a symbol as follows.
- This algorithm is an enhanced version of self-training and is one of the methods of self-supervised learning and distillation.
<img width="300" alt="img1" src="./img/noisy student_symbol.png">

## Key points in this mechanism
1. Add noise to the student model.
2. Student model is not smaller than the teacher model.
- What is different from knowledge distillation.

## Deep dive to Noise
- When creating pseudo labels in the teacher model, no noise was given.
- In the training process in the student model, two types of noise are intentionally assigned.
  1. input noise: randAugment
    - Ensures consistency to predict the same across augmented versions of images.
  2. model noise: dropout and stochastic depth
    - Learning like ensemble.

## Other techniques used in the Noisy student model
1. filtering: filtering images with low confidence in the teacher model
2. balancing: matching the number of images per class in the unlabeled dataset
  - Copy and extend images for insufficient classes, and select images with high confidence when overflowing
3. when Learning pseudo labels, both soft and hard label are properly learned, but soft label is a little better

## Experiments
- Build a model using EfficientNet (based on EfficientNet-L2)
- labeled: starting with batch size 2048 to reduce batch size when model cannot be fit in memory.
  - Same performance with batch size 512, 1024, 2048
- unlabeled: use large batch as much as it is a large model
  - Used 14 times larger than labeled batch size, takes 6 days with 2048 cores to learn
- The best performance was repeated three times
  - "Repeat" means that making a teacher model by reusing student model.

<img width="300" alt="img1" src="./img/noisy student_repeat.png">

1. Initial teacher model: Learning by EfficientNet-B7
2. student model learned by EfficientNet-L2 (teacher: EfficientNet-B7)
3. student model learned by EfficientNet-L2 (teacher: EfficientNet-B7)
4. student model learned by EfficientNet-L2 (teacher: EfficientNet-B7)

- EfficientNet-L2 with Noisy Student Training performs well!
<img width="300" alt="img1" src="./img/noisy student_perf.png">

## Reference
```tex
@article{DBLP:journals/corr/abs-1911-04252,
  author       = {Qizhe Xie and
                  Eduard H. Hovy and
                  Minh{-}Thang Luong and
                  Quoc V. Le},
  title        = {Self-training with Noisy Student improves ImageNet classification},
  journal      = {CoRR},
  volume       = {abs/1911.04252},
  year         = {2019},
  url          = {http://arxiv.org/abs/1911.04252},
  eprinttype    = {arXiv},
  eprint       = {1911.04252},
  timestamp    = {Sun, 01 Dec 2019 20:31:34 +0100},
  biburl       = {https://dblp.org/rec/journals/corr/abs-1911-04252.bib},
  bibsource    = {dblp computer science bibliography, https://dblp.org}
}
```
