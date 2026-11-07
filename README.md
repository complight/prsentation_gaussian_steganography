# Gaussian Image Steganography presentation

Slidev presentation for **Gaussian Image Steganography via Parameter-Domain Keyed Embeddings**, SIGGRAPH Asia 2026 Technical Communications. Updated 6 November 2026 with the latest 16-slide presentation.

Use Node.js 24:

```sh
npm ci
npm run dev
```

The browser viewer shows each slide's final state as a 1920 × 1080 image, preserving the 16:9 PowerPoint composition. Use the arrow keys or Slidev controls to move through all 16 slides.

The [PowerPoint download](public/TC147_slides.pptx) retains the original editable slides, animations and embedded media, with speaker notes removed. The PowerPoint link in Slidev's navigation controls downloads this file.

The [presentation PDF](public/TC147_slides.pdf) contains the same 16 final slide states and is available through Slidev's PDF download control. `public/TC147_Slidev_10_slides.pdf` is a compatibility copy of this PDF so existing project-page links continue to work.

```sh
npm run build
npm run preview
```

The build uses `/prsentation_gaussian_steganography/` as its base path and omits speaker notes. The public assets contain only slide images and the presentation downloads. GitHub Actions builds and deploys `dist/` to GitHub Pages on a push to `main` or a manual workflow run. Configure the repository's Pages publishing source as **GitHub Actions**.
