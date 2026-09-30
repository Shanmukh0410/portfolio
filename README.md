# Portfolio — Bala Sreerangam

Cloud platform engineer. Personal site, served as a single static page.

**Live:** https://shanmukh0410.github.io *(update if the repo name changes)*

## What's here

| File | Purpose |
|---|---|
| `index.html` | The whole site — markup, styles, WebGL scene and content in one file |
| `Bala_Sreerangam_Resume.pdf` | Resume, also embedded in the page as base64 for one-click download |
| `.nojekyll` | Tells GitHub Pages to serve files as-is rather than running Jekyll |

No build step and no dependencies to install. Three.js loads from a CDN at runtime; everything else is inline.

## Running it locally

```bash
python -m http.server 8000
```

Then open http://localhost:8000. Opening `index.html` directly from the filesystem works too — the resume download falls back to a blob download when there's no server.

## Structure

- **Case studies** — seven systems, each with a hand-drawn SVG architecture diagram rendered from node/edge data in `DIA`
- **Timeline** — employment history, rendered from `EXP`
- **Pipelines** — two scroll-triggered build sequences from `SEQ`
- **Platform** — 28 clickable AWS services, copy in `SVC`
- **Resume** — full text on the page, plus PDF download and copy-as-text

The background is one continuous Three.js scene: nine infrastructure layers stacked down the Y axis, with the camera descending through them as the page scrolls.

## Editing

Content lives in JavaScript data structures near the top of the `<script>` block — `DIA`, `CASES`, `EXP`, `SEQ`, `LAYERS`, `SVC`. Change those rather than the markup.

To replace the embedded resume, re-encode the PDF and swap the `window.__RESUME_B64` string:

```bash
python -c "import base64;print(base64.b64encode(open('Bala_Sreerangam_Resume.pdf','rb').read()).decode())"
```

## Notes

Client names are deliberately omitted. The work was done for enterprise customers under confidentiality, so the site describes sectors and scale instead.
