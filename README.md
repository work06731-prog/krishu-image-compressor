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

## Deploy to Vercel

1. Open https://vercel.com/new and import `work06731-prog/krishu-image-compressor`.
2. Keep **Root Directory** at the repository root (`./`). Do not select `dist` as the root.
3. Click **Deploy**. The root `vercel.json` selects the Other framework preset, skips installation/build commands, and publishes `dist` automatically.
4. Open the URL Vercel returns. No API keys or environment variables are required.

If the repository was already imported, redeploy the latest `main` commit. Keep the root directory at `./`; remove any old framework or build overrides if needed. Future pushes to the connected production branch can be deployed by Vercel's Git integration.

The GitHub Pages workflow was removed because this project now targets Vercel. The app remains usable as a local static website.

Configuration reference: https://vercel.com/docs/project-configuration/vercel-json

## Limits and tradeoffs

PNG uses lossless browser encoding and ignores the quality slider; use WebP or resize to reduce PNG size. Exact reduction depends on the source; it cannot be promised. JPEG and lossy WebP re-encoding can lose detail. A target size may reduce dimensions and is not guaranteed.

Limits: 50 images, 25 MB per image, 200 MB source data per batch and 40 megapixels per image. Device memory can impose lower limits. Processing is sequential. HEIC, SVG, GIF, animated PNG and animated WebP are unsupported; animated inputs are rejected rather than silently flattened. Browser encoders may change color profiles and remove metadata. Retained originals preserve their metadata. Neither preservation of HDR nor print-DPI metadata is guaranteed.

No image data leaves the device. Theme preference is the only value stored in localStorage. Refreshing clears the queue. The ZIP uses stored entries because images are already compressed.

## Files

- `dist/index.html`: interface
- `dist/style.css`: responsive styles
- `dist/app.js`: compression, previews, downloads, ZIP writer
- `vercel.json`: automatic Vercel deployment settings

## License

MIT. See LICENSE.
