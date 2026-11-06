---
theme: default
title: Gaussian Image Steganography via Parameter-Domain Keyed Embeddings
info: SIGGRAPH Asia 2026 Technical Communications.
author: Tong Wu, Runze Cheng, Xiaoyue Fan, Kaan Akşit
canvasWidth: 1280
aspectRatio: 16/9
colorSchema: light
transition: fade
drawings:
  enabled: false
fonts:
  provider: none
  sans: Helvetica, Arial
  serif: Georgia
  mono: Courier New
download: ./TC147_slides.pdf
exportFilename: TC147_slides
htmlAttrs:
  lang: en
lineNumbers: false
layout: none
clicks: 0
---

<PptImage src="slides/slide-01.png" :page="1" title="Gaussian Image Steganography via Parameter-Domain Keyed Embeddings" />

---
layout: none
title: "What is steganography?"
clicks: 0
---

<PptImage src="slides/slide-02.png" :page="2" title="What is steganography?" />

---
layout: none
title: "Where can hidden information live?"
clicks: 0
---

<PptImage src="slides/slide-03.png" :page="3" title="Where can hidden information live?" />

---
layout: none
title: "One image represented by 2D Gaussian parameters"
clicks: 0
---

<PptImage src="slides/slide-04.png" :page="4" title="One image represented by 2D Gaussian parameters" />

---
layout: none
title: "An image can be represented by 2D Gaussians"
clicks: 0
---

<PptImage src="slides/slide-05.png" :page="5" title="An image can be represented by 2D Gaussians" />

---
layout: none
title: "Fitting Gaussians to the target image"
clicks: 0
---

<PptImage src="slides/slide-06.png" :page="6" title="Fitting Gaussians to the target image" />

---
layout: none
title: "Which parameter changes should carry the message?"
clicks: 0
---

<PptImage src="slides/slide-07.png" :page="7" title="Which parameter changes should carry the message?" />

---
layout: none
title: "Choose the edits, then optimize the parameters"
clicks: 0
---

<PptImage src="slides/slide-08.png" :page="8" title="Choose the edits, then optimize the parameters" />

---
layout: none
title: "Three parameters we can change"
clicks: 0
---

<PptImage src="slides/slide-09.png" :page="9" title="Three parameters we can change" />

---
layout: none
title: "Choose valid edits with lower cost"
clicks: 0
---

<PptImage src="slides/slide-10.png" :page="10" title="Choose valid edits with lower cost" />

---
layout: none
title: "Fine-tuning refines the selected parameter edits"
clicks: 0
---

<PptImage src="slides/slide-11.png" :page="11" title="Fine-tuning refines the selected parameter edits" />

---
layout: none
title: "Read the message from parameter changes"
clicks: 0
---

<PptImage src="slides/slide-12.png" :page="12" title="Read the message from parameter changes" />

---
layout: none
title: "The clean and embedded images look similar"
clicks: 0
---

<PptImage src="slides/slide-13.png" :page="13" title="The clean and embedded images look similar" />

---
layout: none
title: "Cost-aware selection improves recovery over random selection"
clicks: 0
---

<PptImage src="slides/slide-14.png" :page="14" title="Cost-aware selection improves recovery over random selection" />

---
layout: none
title: "The fixed message is recovered from all 112 test images"
clicks: 0
---

<PptImage src="slides/slide-15.png" :page="15" title="The fixed message is recovered from all 112 test images" />

---
layout: none
title: "Thank you"
clicks: 0
---

<PptImage src="slides/slide-16.png" :page="16" title="Thank you" />
