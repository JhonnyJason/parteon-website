# Parteon Website - Overview

## Purpose
This is the Website of a PreSeed Project - So the purpose is to communicate the General Project Idea in a nice smooth way.
The General purpose of the Project itself is to create a virtualization Layer on top of Real Estate "investments" which unifies the handling of, investment, ownership and property adding flexibility and ease of use.
## Website concept
- Source content: `plan/prospectus.pdf` (6 Canva slides, dark navy + gold, serif display headings).
- Site = one page of full-screen "slides" that snap on scroll; each slide = background image + content overlay.
- Portrait (mobile): content first, backgrounds possibly not loaded at all.
- Built in steps: 1) slide skeleton with content + scroll-snap, 2) optimized lazy images, 3) interactivity polish, 4) SEO extras.

## Structure (step 1 skeleton + step 2 backgrounds done)
- One module per slide: `heroslidemodule`, `homeslidemodule`, `businessmodelslidemodule`, `tokenisationslidemodule`, `longtermslidemodule`, `investmentslidemodule`, `visionslidemodule` (pug + styles.styl), included in order from `index/indexbody.pug`.
- `globalstyles`: theme colors (navy/gold/cream), fonts (DM Serif Display + Nunito, self-hosted in `ressources/font`), `.slide` base with CSS scroll-snap on `html`.
- Fit-to-screen: root font-size scales with min(height, width) in landscape, with width in portrait (portrait slides may scroll).
- Backgrounds: `ressources/img/<slide>-bg[-small].{avif,webp}` (photo + gold arc cut from the PDF, transparent, over a CSS gradient). Set per slide with the `slide-bg()` mixin from `globalstyles`, landscape only; `slidebgmodule` adds `.bg-on` one screen ahead (lazy). Hero has `.bg-on` statically. See `slidebgmodule/README.md`.
- Icons: inline `<symbol>`s in `svgiconsmodule/svgicons.pug`, used via `svg: use(href="#svg-...")`, coloured with `color`. Masks/filters go in `#svgicon-definitions`.
- SEO: head tags in `page-heads/index/document-head.pug` (canonical, Open Graph, twitter card, JSON-LD Organization), domain https://parteon.ch hardcoded there and in `ressources/seo/` (robots.txt, sitemap.xml). `img/og-image.jpg` is the prospectus cover cropped to 1200×630. Favicons in `ressources/favicon`, no manifest (not needed for a non-app site).
- Slide-in: `slideinmodule` adds `.shown` to a slide once; children of `.slide-in-right` / `.slide-in-up` containers move in (CSS in `globalstyles`). Used on home and businessmodel (staggered list items), tokenisation, longterm, investment (two whole blocks). See `slideinmodule/README.md`.
