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

## Files

| File | What |
|---|---|
| `index.html` | the entire site — open it in a browser, no build step |
| `og.png` | the 1200x630 card shown when the link is shared |
| `docs/` | independent diligence on the investor deck |

**Before the domain goes live:** the Open Graph tags reference `og.png` relatively.
Once you have a domain, make them absolute (`https://yourdomain.com/og.png`) —
some scrapers, WhatsApp among them, will not resolve a relative image.
