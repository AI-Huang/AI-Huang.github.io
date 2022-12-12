---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Benchmark of ResNet on CIFAR-10"
summary: ""
authors: [Kan Huang]
tags: [Benchmark, ResNet, Computer Vision]
categories: []
date: 2022-11-29T13:19:00+08:00
# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: "https://github.com/AI-Huang/CV_Playground"
url_pdf: "https://arxiv.org/abs/1512.03385"
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

This is a **TensorFlow** replication of experiments on CIFAR-10 mentioned in ResNet ([K. He, et al., Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385)). My codes:

- Adapts Keras's example codes of ResNet for CIFAR-10 (note that this is a simpler version specially designed for CIFAR-10);
- Apply the SENet module to the ResNet;
- Re-train the ResNet w/o SENet on CIFAR-10 for benchmark evaluation.

For statistical validation, each group of experiment has been run for 5 times.

Firstly, I try to reproduce the results with totally the same [model codes](https://github.com/AI-Huang/CV_Playground/blob/master/models/tf_fn/resnet_cifar10.py) given by Keras. The batch size is set to 32. The optimizer is Adam with an initial learning rate 0.001. The validation split is 0, and the whole train set is used as training data. The data augmentation could be found at [keras_augmentation](https://github.com/AI-Huang/CV_Playground/blob/master/data_loaders/tf_fn/data_generator.py). The leanring scheduler could be found at [keras_lr_scheduler](https://github.com/AI-Huang/CV_Playground/blob/master/models/tf_fn/optim_utils.py). Our results outperform Keras's on `ResNet44v1_CIFAR10`, but go worse a little on other models.

ResNet20 keras_augmentation Adam 0.001 0 keras_lr_scheduler 0.9183

| Model               | Author | best test accuracy |
| ------------------- | ------ | ------------------ |
| ResNet20v1_CIFAR10  | Keras  | 0.9216             |
| ResNet20v1_CIFAR10  | Kan    | 0.9183             |
| ResNet32v1_CIFAR10  | Keras  | 0.9246             |
| ResNet32v1_CIFAR10  | Kan    | 0.9227             |
| ResNet44v1_CIFAR10  | Keras  | 0.9250             |
| ResNet44v1_CIFAR10  | Kan    | 0.9252             |
| ResNet56v1_CIFAR10  | Keras  | 0.9271             |
| ResNet56v1_CIFAR10  | Kan    | 0.9236             |
| ResNet110v1_CIFAR10 | Keras  | 0.9265             |
| ResNet110v1_CIFAR10 | Kan    | 0.9260             |

Later, I follow the same configuration by K. He, et al., and use standard normalization. Random translation (padding, and then crop with a horizonal flip) is also applied. The validation split changes from 0 to 0.1 thus results in a 45k/5k train/val split. We follow the same optimizer settings. We use the SGD optimizer with an initial learning rate of 0.1, a momentum of 0.9, a weight decay of 0.0001 and finally a mini-batch size of 128.
`cifar10_scheduler` is applied. In original paper, learning rate is reduced by a factor 0.1 on some a step such as the 32k and 48k step. Here we convert these step indices into epoch indices by equation:
$$ steps_per_epoch = \lceil \frac{45000}{batch_size} \rceil , $$
$$ epoch_to_reduce_lr = \lceil \frac{32000|48000}{steps_per_epoch} \rceil . $$
Thus we have an adapted schedule:

| steps (batchsize 128) | epoch   | LR (SGD) |
| --------------------- | ------- | -------- |
| 32k                   | 1~91    | 0.1      |
| 48k                   | 92~137  | 0.01     |
| 64k                   | 137~182 | 0.001    |

The results are listed as the table below:

| Model               | pre-processing | data_augmentation  | Author    | best test accuracy |
| ------------------- | -------------- | ------------------ | --------- | ------------------ |
| ResNet20v1_CIFAR10  | subtract_mean  | pad_crop_flip      | He et al. | 91.25%             |
| ResNet20v1_CIFAR10  | std_norm       | random_translation | Kan       | 91.30%             |
| ResNet32v1_CIFAR10  | subtract_mean  | pad_crop_flip      | He et al. | 92.49%             |
| ResNet32v1_CIFAR10  | std_norm       | random_translation | Kan       | 92.16%             |
| ResNet44v1_CIFAR10  | subtract_mean  | pad_crop_flip      | He et al. | 92.83%             |
| ResNet44v1_CIFAR10  | std_norm       | random_translation | Kan       | N/A                |
| ResNet56v1_CIFAR10  | subtract_mean  | pad_crop_flip      | He et al. | 93.03%             |
| ResNet56v1_CIFAR10  | std_norm       | random_translation | Kan       | N/A                |
| ResNet110v1_CIFAR10 | subtract_mean  | pad_crop_flip      | He et al. | 93.39+-.16%        |
| ResNet110v1_CIFAR10 | std_norm       | random_translation | Kan       | 0.9210             |
| ResNet164v1_CIFAR10 | subtract_mean  | pad_crop_flip      | He et al. | N/A                |
| ResNet164v1_CIFAR10 | std_norm       | random_translation | Kan       | 0.9174             |

The main difference between `random_translation` and `pad_crop_flip` is that the former supply with a new `fill_mode='nearest'`.
Among the model that both He et al. and me have the results, our results only outperform He's on ResNet20v1_CIFAR10, and are not as good as He claims on ResNet32v1_CIFAR10 and ResNet110v1_CIFAR10.
Models listed below are further used as benchmarks for SENet counterpart:

- ResNet20v1_CIFAR10
- ResNet32v1_CIFAR10
- ResNet110v1_CIFAR10
- ResNet164v1_CIFAR10
