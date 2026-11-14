# Shot Cabinet

Open-source alternative to **CleanShot X** for local screenshot annotation and PNG export: arrows, outlines, labels, cropping and opaque redaction. Built for support replies, bug reports and project launches. Open `index.html` in a current Chromium browser, choose an image, annotate it and export a PNG. No account, server, build step or upload is required. MIT licensed. The name is provisional pending publication checks.

## Use it

1. Download and extract the package, then open `index.html`. Or serve this directory with `python3 -m http.server 8000`.
2. Choose, drop or paste a PNG, JPEG or WebP. Try the synthetic example if you have no screenshot handy.
3. Drag arrows, outlines or a crop; enter label text and click to place it. Use Redact to replace sensitive pixels with black.
4. Choose padding, background and filename; export PNG and inspect the downloaded image before sharing.

Images are limited to 20 MB and 12 megapixels. Undo retains at most five edits within a 64 MB budget. Redaction clears all undo history; later edits cannot undo past that boundary. This does not erase the original file, earlier downloads, or browser/OS memory. Redaction is manual: cover the entire sensitive area. Closing or refreshing loses the edit session.

Drawing requires pointer input. Desktop Chromium is tested; mobile layout is captured, but touch hardware and other browser engines remain unverified. There is no native screen capture, OCR, video, cloud hosting, collaboration or editable project format.

## Compared with CleanShot X

This project addresses the screenshot **editing and export** workflow associated with CleanShot X. It supplies local arrows, outlines, labels, cropping, opaque redaction and padded PNG export. It does not replace the native capture and sharing suite. No claims of feature parity, performance superiority or affiliation are made. Competitor pricing and current feature inventory have not been verified for this candidate.

## Tests

Node 22 or later:

```sh
npm ci
npx playwright install chromium
npm test
```

`CHROMIUM_PATH` optionally selects an installed Chromium binary. The browser test opens the actual local HTML, exercises horizontal arrows, undo, redaction, text, crop, export and re-import, checks redacted pixels in the re-imported PNG, rejects SVG, and asserts zero HTTP requests and script errors. Screenshots are written to `artifacts/`; exports use a temporary directory and are removed. Dependencies are development-only.

## Distribution path

First publish a downloadable static package and a runnable demo from the owned repository. Put a short “redact a support screenshot” walkthrough and before/after synthetic example in the README. Link this editor from a concrete screenshot-preparation workflow in our own product documentation when relevant. After public publication, evaluate eligible screenshot/privacy tool directories against their contribution policies; no external submission has been made. Track accepted external PRs separately from owned product merges.

## Release status

Locally tested candidate, not a public release. Publication to the independent shot-cabinet repository and name collision review are pending. Evidence: `artifacts/validation.json`. No stars or merged PRs are attributed to this package yet.
