# SAASH

Brand website and product portfolio for SAASH — at-home light-therapy devices.

## The site

`index.html` is the entire website. One self-contained file: hash-routed pages,
all product imagery embedded as base64 WebP, no build step, no dependencies.
The only external request is Google Fonts. Open it in a browser and it runs.

**Pages** — home, devices, one page per device (Blemish, Cold Sore, AI LED Mask,
Cryo, Carry), technology, the house, contact, and nine policy pages.

### Deploying

GitHub Pages: Settings → Pages → Source `main`, folder `/ (root)`. Live in a minute.
Netlify or Vercel: connect the repo, leave the build command empty, publish directory `.`.

### Editing

| Line | What |
|---|---|
| `DEVICES` | names, prices, specs, taglines — everything product-related |
| `FILM_SRC` | paste a `data:video/mp4;base64,…` URI and the home film goes live |
| `POLICIES` | the nine legal and help pages |
| `:root` | colour tokens (light theme below it) |
| `ASSETS` | base64 images — one long line, skip past it |

### Before launch

- Policy pages carry a **"Draft · pending legal review"** marker. They need a
  UAE-qualified lawyer before going live; removing the marker is one line in `pDoc`.
- Contact and newsletter forms validate and confirm in the browser but **do not
  send anywhere yet**. Wire a form endpoint into `wire()` near the bottom.
- No device holds regulatory clearance. The site states this throughout and takes
  reservations rather than orders. Do not remove those notices before clearance.

## docs/

Independent diligence on the investor deck — two adversarial passes, eleven
research agents, all claims verified against public sources. Start with
`SAASH_Verdict_Summary.pdf` (3 pages).

## Deploying to Vercel

1. vercel.com → **Add New → Project** → import `moneyladder911/Saash`
2. Framework preset **Other**. Leave the build command empty and the output
   directory as the repository root. There is nothing to build.
3. Deploy. You get a `*.vercel.app` URL in under a minute.

**Then do one thing.** Open `index.html` and make the two share-image tags
absolute — `og:image` and `twitter:image` — using the URL Vercel gave you:

```html
<meta property="og:image" content="https://your-project.vercel.app/og.png">
<meta name="twitter:image" content="https://your-project.vercel.app/og.png">
```

LinkedIn, Slack and Twitter resolve a relative image. WhatsApp does not, and
that is often how a link actually reaches an investor.

## Files

| File | What |
|---|---|
| `index.html` | the whole site — routing, styles and copy, ~86 KB |
| `assets/` | product renders, textures and the share card, cached for a year |
| `og.png` | the 1200×630 card shown when the link is shared |
| `vercel.json` | cache headers only |
| `docs/` | independent diligence on the investor deck |

## Editing

| Constant | What it controls |
|---|---|
| `FORM_ENDPOINT` | paste a Formspree or Netlify URL and both forms POST to it |
| `SOCIALS` | add profile URLs and the footer names become links |
| `HERO_SRC` | an image or video here replaces the wordmark hero |
| `FILM_SRC` | a video here adds a film section below the hero |
| `DEVICES` | names, prices, specs, taglines |
| `FAQ` / `POLICIES` | the questions page and the nine legal and help pages |

## Before launch

- Policy pages carry a **"Draft · pending legal review"** marker. They need a
  UAE-qualified lawyer; removing the marker is one line in `pDoc`.
- `FORM_ENDPOINT` is empty, so forms validate and confirm but send nothing.
- No device holds regulatory clearance. The site says so throughout and takes
  reservations rather than orders. Do not remove those notices before clearance.
