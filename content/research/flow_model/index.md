---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Image Compression with Flow Models"
summary: ""
authors: []
tags: []
categories: []
date: 2021-05-18T16:58:00+08:00

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

url_code: ""
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

- Found new approaches of using flow models to do compression tasks for image‐like data. Wrote processing and feature extracting functions for 80K+ target data. Tested VQ‐VAE and basic Real NVP model to build unsupervising learning baselines;
- Based on open source codes, wrote hundreds lines of extra codes to restore Real NVP Compression model introduced by the SOTA papers. Did experiments with different feature extractors on the 80K+ 2D data; it turned out that the permutations of pixels will influence the results;
- Found Glow model’s learning potential; transplanted it from TensorFlow to PyTorch;
- Conclusion: flow models have great potential on distribution transformation, but better permutated data is also necessary.
