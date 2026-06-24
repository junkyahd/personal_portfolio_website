# Jake Boersma — Portfolio

Personal portfolio, built with [Astro](https://astro.build) (static). "Working Paper" design — serif/typeset, navy ink, rate-curve motif.

## Run locally

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # static output to ./dist
npm run preview  # preview the built site
```

## Structure

```
src/
  layouts/Base.astro            head + masthead + footer; imports global.css
  components/
    Masthead.astro              nav with active-page highlight
    CurveMark.astro             the rate-curve SVG (variant: "mark" | "figure")
  pages/
    index.astro                 Home (researcher header, about, selected work)
    writing/index.astro         Writing index (reads src/data/writing.js)
    writing/perpetual-rates.astro   CIRCA paper page (full treatment)
    projects.astro
    about.astro
  data/writing.js               writing entries — drives the Writing index
  styles/global.css             all design tokens + styles
public/                          drop resume.pdf and full-paper.pdf here
```

## Add a writing piece

1. Append an entry to `src/data/writing.js`.
2. Create its page under `src/pages/writing/your-slug.astro` (copy `perpetual-rates.astro` as a starting point) and point the entry's `href` at it.

> Later upgrade path: swap the data array for an Astro content collection so pieces are plain markdown. Kept as a simple array here for a zero-config build.

## Before launch — fill these in

- Real links throughout: GitHub, LinkedIn, Résumé (currently `href="#"`). Email is wired to `jake.m.boersma@gmail.com`.
- Drop `resume.pdf` and the CIRCA `full-paper.pdf` into `public/` and link them.
- Set your final domain in `astro.config.mjs` (`site`).

### ⚠️ Verify before the CIRCA page goes public
Confirm against the live CIRCA **v0.2**: the `$469T` notional and `81%` figures, the `15–40%` capital-efficiency range, and the initial-margin wording. These came from working notes, not the live paper.

## Deploy (any static host)

- **Vercel:** push to GitHub → import the repo (framework auto-detected) → deploy. Or run `vercel`.
- **Netlify:** connect the repo (build `npm run build`, publish `dist`), or drag `dist/` onto Netlify Drop.
- **GitHub Pages:** use the Astro Pages guide; set `site`/`base` accordingly.

Add a custom domain in the host dashboard once it's live.
