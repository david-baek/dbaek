# David Baek's website

Personal academic website at [dbaek.org](https://dbaek.org), built with Hugo.
The visual design is adapted from [Jay Wang's website](https://zijie.wang/), with attribution in the footer.

## Edit featured publications

Edit **`data/publications.json`**. Entries appear in array order on both the homepage and CV.

- `title`, `authors`, `venue`, `summary`, and `award`: displayed paper information. Authors support Markdown, including `**bold**`.
- `paper_url`, `code_url`, `x_url`: paper, code, and announcement links. Leave optional links empty (`""`) to hide them.
- `bibtex`: the citation shown by the expandable BibTeX control. In JSON, use `\n` for line breaks inside the string.
- `id`: a unique, stable identifier, also used as the card's HTML anchor.
- `image`: the public URL of the thumbnail; `image_alt`: a short accessible description.

### Replace the placeholder images

Place your images in **`static/images/publications/`**. Current placeholders are:

| Paper | Placeholder file |
| --- | --- |
| Performative Misalignment | `performative-misalignment.svg` |
| Scaling Laws for Scalable Oversight | `scalable-oversight.svg` |
| Any-Depth Alignment | `any-depth-alignment.svg` |
| D-FUSEr | `d-fuser.svg` |

For example, add `static/images/publications/scalable-oversight.png`, then change that entry in `data/publications.json` to:

```json
"image": "/images/publications/scalable-oversight.png",
"image_alt": "Scaling of oversight success with supervisor capability"
```

Use PNG, JPEG, WebP, or SVG. A 750 × 420 image (roughly 16:9) works well; it displays at 250 × 140 on desktop without cropping. Do not include `static` in the image URL. Replacing an SVG with another SVG at the same path requires no data edit.

These featured publications are independent of the starter examples in `content/publication/`. Their shared rendering template is `layouts/partials/featured-publications.html`.

## Edit other content

- **Homepage intro and news:** `layouts/landing/index.html`.
- **Notes:** `content/notes.md`, served at `/notes/`.
- **Interactive CV:** `data/cv.json`, served at `/cv/`. Entries with `description` expand and collapse; entries without one display as simple rows. The initial content comes from `static/uploads/resume.pdf`.
- **Downloadable CV:** replace `static/uploads/resume.pdf` separately when updating your résumé.
- **CV page layout and controls:** `layouts/partials/cv.html`.
- **Shared Notes/CV layout:** `layouts/personal/single.html`.
- **Style adjustments:** `static/css/home.css`; reference styles remain in `static/css/reference-*.css`.
- **Theme navigation:** `config/_default/menus.yaml`.

## Build and deploy

Use Hugo **extended 0.136.5** (matching `.github/workflows/publish.yaml`) and Go for Hugo modules.

```sh
hugo server
# Production check without changing the tracked public/ directory:
hugo --minify --destination /tmp/dbaek-site-preview
```

The GitHub Pages workflow builds and deploys on pushes to `main`. Edit source files, not the legacy generated files in `public/`.
