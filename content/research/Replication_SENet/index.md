---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Replication of SENet"
summary: ""
authors: [Kan Huang]
tags: [Replication, SENet, Computer Vision]
categories: []
date: 2022-11-22T17:00:00+08:00
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

url_code: "https://github.com/AI-Huang/SENet-tf"
url_pdf: "https://arxiv.org/abs/1709.01507"
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

This is a replication of the work SENet ([J. Hu, et al., Squeeze-and-Excitation Networks](https://arxiv.org/abs/1709.01507)). My codes:

- Implement the SENet module;
- Apply the SENet module to the ResNet;
- Train the ResNet with SENet on CIFAR-10;
- Use the re-trained benchmark results of ResNet on CIFAR-10 for comparative evaluation.

For statistical validation, each group of experiment has been run for 5 times.

J. Hu et al.'s experiment group uses pad, crop and flip augmentation, while I use random tranlation augmentation. Both groups use standard deviation normalization. Number in the brackets of test accuracy are the difference from the ResNet backbone to the SE-ResNet counterpart.

| Model               | Author       | best test accuracy    |
| ------------------- | ------------ | --------------------- |
| ResNet20v1_CIFAR10  | Kan          | 91.30%                |
| ResNet32v1_CIFAR10  | Kan          | 92.16%                |
| ResNet110v1_CIFAR10 | Kan          | 92.10%                |
| ResNet164v1_CIFAR10 | Kan          | 91.74%                |
| SE-ResNet20 (γ=16)  | Kan          | 91.70% (+0.4)         |
| SE-ResNet32 (γ=16)  | Kan          | 92.44% (+0.28)        |
| SE-ResNet110 (γ=16) | Kan          | 86.56% (-5.54)        |
| SE-ResNet164 (γ=16) | Kan          | 55.25% (-36.49)       |
| SE-ResNet110 (γ=16) | J. Hu et al. | 5.21 (94.79%) (+1.16) |
| SE-ResNet164 (γ=16) | J. Hu et al. | 4.39 (95.61%) (+1.07) |

Experiments on SE-ResNet20 and SE-ResNet32 show that SE module works well on enhancing the backbone network. But due to the backbone's performance limitation (e.g., ResNet20), such enhancement is relatively limited. Training on SE-ResNet110 and SE-ResNet164 doesn't converge, I'm still figuring out why.
