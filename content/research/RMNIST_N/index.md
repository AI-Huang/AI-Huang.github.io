---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "RMNIST/N: Train MNIST dataset with only TEN samples"
summary: ""
authors: []
tags: []
categories: [Deep Learning, Data Augmentation]
date: 2022-08-09T22:02:00+08:00

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
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

[RMNIST/N](https://cognitivemedium.com/rmnist) is a dataset that reduces MNIST with N examples for each digit class. In this way, RMNIST/1 has 1 training example for each digit, for a total of only 10 training examples. This article presents how a digits recognizer can be trained on only ten samples from the whole MNIST dataset. Data augmentation is used during the training. Ablation study is also made.
