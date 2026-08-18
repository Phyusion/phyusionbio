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
and can also be run by hand from the Actions tab.

### One-time setup

Pages must be switched on once by a repository admin: **Settings -> Pages -> Source ->
GitHub Actions**. The workflow asks `configure-pages` to create the site automatically
(`enablement: true`), but the built-in `GITHUB_TOKEN` is not permitted to create a Pages site and
fails with `Resource not accessible by integration`. Once Pages is on, that step is a no-op.

After enabling, re-run the latest workflow from the Actions tab (or push any commit) to publish.

The site is served at https://phyusion.github.io/phyusionbio/. To use `phyusionbio.com` instead,
add a `CNAME` file containing the domain, set the custom domain under Settings -> Pages, and point
the DNS records at GitHub Pages.

## Editing content

- **Headline** — the `<h1>` in `index.html`.
- **Portfolio ticker** — the `companies` array in the inline script at the bottom of the file.
- **Contact form** — the `data-tf-slider` ID on the CTA button (currently `aekt7slB`).
