# Gaussian Image Steganography presentation

Native Slidev presentation for **Gaussian Image Steganography via Parameter-Domain Keyed Embeddings**, SIGGRAPH Asia 2026 Technical Communications.

The 16 slides use `slides.md` and Vue components with editable HTML text, tables, charts, and process diagrams. Individual figures, photographs, author portraits, logos, and a fitting video live in `public/assets/`.

## Development

Use Node.js 24:

```sh
npm ci
npm run dev
```

Space or the right arrow reveals the next step, then advances to the next slide. The left arrow steps back. The title slide appears immediately. Slide 2 is a click-controlled introduction. Slide 6 plays the fitting illustration on its first click and pauses at the final frame when the clean fit is discussed.

Click counts by slide: `0, 6, 3, 3, 5, 3, 4, 5, 4, 5, 3, 6, 4, 4, 4, 1`.

## PDF export

```sh
npm run export
cp public/TC147_slides.pdf public/TC147_Slidev_10_slides.pdf
```

The export uses Slidev and Chromium. If Chromium is not installed, run `npx playwright install chromium`, or pass `--executable-path` to an installed Chromium-based browser. The PDF contains one complete page per slide, with focus dimming removed and a still image in place of the video. `TC147_Slidev_10_slides.pdf` is a compatibility copy for the existing project-page link.

## Build and deployment

```sh
npm run build
npm run preview
```

The build uses `/prsentation_gaussian_steganography/` as its base path and omits speaker notes. GitHub Actions builds and deploys `dist/` to GitHub Pages on a push to `main` or a manual workflow run. The repository's Pages publishing source is **GitHub Actions**.

## Figures and sources

The slide text and numerical results follow the [paper and supplementary material](https://complightlab.com/publications/gaussian_steganography/). The original method diagrams and evaluation examples are reused as individual figure assets. Source photographs in the visual comparison are by Christian Widell and Christian J. Leuner. Related-work examples are attributed on Slide 3. Author portraits, institutional logos, and the project QR code come from the reviewed presentation materials.

The fitting clip is a teaching illustration of parameter updates toward a target image. It is separate from the reported 256- and 4,096-Gaussian evaluations.

No speaker scripts or Microsoft Office files are included in the published presentation.
