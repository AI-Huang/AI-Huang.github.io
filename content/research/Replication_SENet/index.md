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
