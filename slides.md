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
download: ./TC147_Slidev_10_slides.pdf
exportFilename: TC147_Slidev_10_slides
htmlAttrs:
  lang: en
lineNumbers: false
layout: none
clicks: 0
---

<PptSlide src="slides/slide-01.svg" :page="1" title="Gaussian Image Steganography via Parameter-Domain Keyed Embeddings" />



---
layout: none
title: Hide information in Gaussian parameters — not pixels
clicks: 0
---

<PptSlide src="slides/slide-02.svg" :page="2" title="Hide information in Gaussian parameters — not pixels" />



---
layout: none
title: 'System overview: from clean fit to keyed recovery'
clicks: 3
---

<PptSlide src="slides/slide-03.svg" :page="3" title="System overview: from clean fit to keyed recovery" :regions='[{"x":50,"y":571,"w":393,"h":72,"at":1,"label":"Fit the clean carrier"},{"x":450,"y":571,"w":394,"h":72,"at":2,"label":"Select keyed edits"},{"x":850,"y":571,"w":398,"h":72,"at":3,"label":"Render and decode"}]' />



---
layout: none
title: The key selects edits; decoding reads changes against the clean fit
clicks: 5
---

<PptSlide src="slides/slide-04.svg" :page="4" title="The key selects edits; decoding reads changes against the clean fit" :regions='[{"x":77,"y":309,"w":540,"h":94,"at":1,"label":"Keyed assignment"},{"x":77,"y":405,"w":540,"h":95,"at":2,"label":"Fine-tune selected parameters"},{"x":77,"y":501,"w":548,"h":99,"at":3,"label":"Embedded Gaussian parameters"},{"x":707,"y":242,"w":532,"h":238,"at":4,"label":"Three decoder inputs"},{"x":708,"y":513,"w":531,"h":85,"at":5,"label":"Read parameter changes"}]' />



---
layout: none
title: Three carrier channels, cost-aware keyed assignment
clicks: 3
---

<PptSlide src="slides/slide-05.svg" :page="5" title="Three carrier channels, cost-aware keyed assignment" :regions='[{"x":620,"y":216,"w":614,"h":147,"at":1,"label":"Assignment constraints"},{"x":620,"y":380,"w":614,"h":151,"at":2,"label":"Fine-tuning objectives"},{"x":53,"y":541,"w":1181,"h":125,"at":3,"label":"Editing and recovery summary"}]' />



---
layout: none
title: Small parameter edits keep the rendering close to the clean fit
clicks: 0
---

<PptSlide src="slides/slide-06.svg" :page="6" title="Small parameter edits keep the rendering close to the clean fit" />



---
layout: none
title: 'Fixed 8-bit payload: controlled fits and held-out natural images'
clicks: 0
---

<PptSlide src="slides/slide-07.svg" :page="7" title="Fixed 8-bit payload: controlled fits and held-out natural images" />



---
layout: none
title: Boundary tests clarify what the current method supports
clicks: 0
---

<PptSlide src="slides/slide-08.svg" :page="8" title="Boundary tests clarify what the current method supports" />



---
layout: none
title: Gaussian parameters can carry a small keyed payload
clicks: 0
---

<PptSlide src="slides/slide-09.svg" :page="9" title="Gaussian parameters can carry a small keyed payload" />



---
layout: none
title: Thank you
clicks: 0
---

<PptSlide src="slides/slide-10.svg" :page="10" title="Thank you" :links='[{"x":951.849343832021,"y":405.40293963254595,"w":210.24,"h":210.24,"href":"https://complightlab.com/publications/gaussian_steganography/","label":"Open the project page"},{"x":870.0586876640419,"y":615.70687664042,"w":360.0,"h":26.88,"href":"https://complightlab.com/publications/gaussian_steganography/","label":"Open the project page"}]' />
