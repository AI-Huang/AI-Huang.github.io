---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Seq2Seq QQ Chatbot"
summary: ""
authors: []
tags: [software development, chatbot]
categories: []
date: 2019-02-15T16:02:00+08:00

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

- Built a chatbot on the QQ platform with the Coolq Framework. Implemented the following functions
- chatbot: built an application interface for the Seq2Seq model, gave the chatbot the ability to response for users’ input;
- dictionary command: using Web crawler, the chatbot can return word’s meaning;
- translate command: using Google translate library, the chatbot can retrive the translation for users’ input;
- sticker command: the chatbot could query the SQL database to find stickers that users demand;
- Other features: group members’ same words repeater; weather querying; banning user’s chat; search image by image.

[The Chatbot's dialogue robot model]({{< relref "/research/seq2seq_chatbot" >}}).
