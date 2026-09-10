# Krishu Image Compressor

A free, private, dependency-free image compression website. No API key, backend, account, analytics, external fonts or CDN requests.

## Features

- Drag/drop, multiple file selection and image paste
- JPG, PNG and static WebP input; JPG/PNG/WebP output where the browser supports encoding
- Balanced, smallest-size and high-quality presets; adjustable lossy quality
- Aspect-ratio-preserving maximum dimensions; no upscaling
- Best-effort target size: quality search followed by dimension reduction
- JPG background color for transparent images
- Original retention when compression would increase size, without undoing requested changes
- Side-by-side comparison, individual downloads and dependency-free ZIP downloads
- Per-image errors, batch progress, cancellation between images
- Responsive layout, accessible labels, keyboard controls, light/dark theme

## Run

Open `dist/index.html` in a modern browser. Everything runs locally, even offline after downloading the project. Alternatively, run `python -m http.server 8080 --directory dist` and visit http://localhost:8080.

## Publish to GitHub Pages

Push this repository, then open **Settings → Pages → Source → GitHub Actions**. The included workflow publishes the `dist` folder on pushes to `main`, or when manually run. GitHub hosting availability depends on your account and repository settings.

## Limits and tradeoffs

PNG uses lossless browser encoding and ignores the quality slider; use WebP or resize to reduce PNG size. Exact reduction depends on the source; it cannot be promised. JPEG and lossy WebP re-encoding can lose detail. A target size may reduce dimensions and is not guaranteed.

Limits: 50 images, 25 MB per image, 200 MB source data per batch and 40 megapixels per image. Device memory can impose lower limits. Processing is sequential. HEIC, SVG, GIF, animated PNG and animated WebP are unsupported; animated inputs are rejected rather than silently flattened. Browser encoders may change color profiles and remove metadata. Retained originals preserve their metadata. Neither preservation of HDR nor print-DPI metadata is guaranteed.

No image data leaves the device. Theme preference is the only value stored in localStorage. Refreshing clears the queue. The ZIP uses stored entries because images are already compressed.

## Files

- `dist/index.html`: interface
- `dist/style.css`: responsive styles
- `dist/app.js`: compression, previews, downloads, ZIP writer
- `.github/workflows/pages.yml`: optional Pages deployment

## License

MIT. See LICENSE.
