# Gaussian Image Steganography presentation

Slidev presentation for **Gaussian Image Steganography via Parameter-Domain Keyed Embeddings**, SIGGRAPH Asia 2026 Technical Communications.

Use Node.js 24:

```sh
npm ci
npm run dev
```

The reviewed [presentation PDF](public/TC147_Slidev_10_slides.pdf) is included in `public/`.

```sh
npm run build
npm run preview
```

The build uses `/prsentation_gaussian_steganography/` as its base path and omits speaker notes. GitHub Actions builds and deploys `dist/` to GitHub Pages on a push to `main` or a manual workflow run. Configure the repository's Pages publishing source as **GitHub Actions**.
