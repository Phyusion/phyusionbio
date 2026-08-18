# phyusionbio.com

Static single-page site for Phyusion Bio, built from the Phyusion Bio design system.

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | The entire site — markup, styles, and the portfolio ticker script are inlined. |
| `logo-teal.svg` | Wordmark in teal (`#175A69`) — used on the white page background. |
| `logo.svg` | Same wordmark in white, for dark backgrounds. |
| `favicon.png` | Browser / apple-touch icon. |
| `.nojekyll` | Serves files verbatim; skips GitHub's Jekyll processing. |

External dependencies loaded at runtime: Google Fonts (Quicksand, IBM Plex Sans, IBM Plex Mono)
and the Typeform embed (`embed.typeform.com`) behind the "Get in touch" button.

## Design tokens

Defined as CSS custom properties at the top of `index.html`:

```
--teal-900 #0C3540   --teal-800 #10454F   --teal-700 #175A69
--teal-200 #BEE0E7   --teal-100 #E3F1F4   --coral    #F77B62
```

Display type is Quicksand, body is IBM Plex Sans, and eyebrow/label/button type is IBM Plex Mono.

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. A plain file open (`file://`) works too, but the Typeform
embed behaves better over HTTP.

## Deployment

`.github/workflows/deploy.yml` publishes the repository root to GitHub Pages. It runs on every
push to the **default branch** (matched dynamically, so renaming the branch does not break it)
and can also be run by hand from the Actions tab. The first run enables Pages itself via
`configure-pages` with `enablement: true`, so no manual setup is needed.

If the run fails at the "Setup Pages" step, enable it once by hand: **Settings -> Pages ->
Source -> GitHub Actions**. Workflow write permissions must also be allowed under
**Settings -> Actions -> General**.

The published URL is https://phyusion.github.io/phyusionbio/. To serve the site from
`phyusionbio.com` instead, add a `CNAME` file containing the domain and point the DNS records at
GitHub Pages.

## Editing content

- **Headline** — the `<h1>` in `index.html`.
- **Portfolio ticker** — the `companies` array in the inline script at the bottom of the file.
- **Contact form** — the `data-tf-slider` ID on the CTA button (currently `aekt7slB`).
