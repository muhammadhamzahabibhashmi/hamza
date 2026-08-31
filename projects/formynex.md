# Formynex

**Live:** https://formynex.site
**Repository:** private
**Role:** full stack — front end, SSR pipeline, SEO, deployment

![Formynex home page](../assets/screenshots/formynex-home.png)

## What it is

Formynex is a shop for animated website templates. The whole argument of the product is that you shouldn't have to buy from a screenshot — every template in the catalogue has a live demo you can open, scroll and try on your phone before deciding.

There are 44 templates at the moment, sorted by category and by how they move: scroll-driven, three-dimensional, canvas-drawn, single-file. Those counts come from the catalogue data rather than being written into the copy, so they can't go stale.

Templates are sold one to one, priced per licence in a conversation, so there's no checkout. Instead visitors build a shortlist in a selection drawer and hand it over to an agent. That decision shapes the whole funnel — the conversion surface is a message, not a payment.

![Template catalogue](../assets/screenshots/formynex-templates.png)

## The SEO rebuild

The site was originally a plain Vite SPA. Every URL served the same empty `<div id="root">`, and the one canonical tag in `index.html` was hard-coded to a different hostname entirely. So every template page was telling search engines it was a duplicate of a page on another domain.

The fix was a real prerender step. The build now runs four stages: a client build, an SSR build, a prerender script, then a demo copy step. The prerenderer renders every route to actual HTML — the homepage, one file per catalogue entry, and a real 404 document — and writes robots.txt, sitemap.xml and the web manifest at fixed paths.

The important part is that all of it derives from one `seo.ts` module that both the prerenderer and the client route handler import. The metadata in the served HTML and the metadata after a client-side navigation come from the same function, so they can't drift apart when someone adds a template.

The JSON-LD is built the same way: one Organization entity with an `@id`, referenced by every other node rather than repeated inline. Nothing in it invents ratings, prices, licence terms or compatibility claims — `sameAs` is omitted entirely because the business has no social profiles to point at, and a fabricated one is worse than none.

## Previews without wrecking the page

Every card carries an animated preview — GIF, animated WebP or MP4 — which is a lot of media to put in a grid.

The preview component holds off mounting its media until an intersection observer says the card is coming into range, and a video that has scrolled out of view is paused rather than left running behind the fold. A skeleton holds the exact aspect ratio until the media decodes so nothing shifts, and a file that fails falls back to its poster, then to a neutral placeholder, instead of a broken frame. Under `prefers-reduced-motion` it shows the static poster instead of playing anything.

## Analytics that stay honest

There's a GA4 layer, but nothing fires unless a measurement ID is supplied at build time. Without it every export is an inert no-op — no script injected, no request leaving the browser, no third-party JavaScript loaded onto animation-heavy pages that have a Core Web Vitals budget to keep.

The measurement ID is account data only the site owner holds. Hard-coding a placeholder would produce a site that looks instrumented and silently reports nothing, so the gate is deliberate. The event names match the KPI framework, so key events can be configured in GA4 later without renaming anything.

## Build tooling

A few scripts that came out of problems rather than being planned:

- **responsive audit** — shoots every route at 320, 768 and 1440 and flags horizontal overflow
- **contrast checker** — runs the palette against WCAG ratios
- **brand assets** — generates the logo, OG image and favicons from masters so they stay in sync
- **tile builders** — compose the promotional tiles for specific templates
- **demo copy** — moves the standalone template demos into the build output, served `noindex` so they never compete with the catalogue pages in search

## Deployment

Vercel, with headers set per path: immutable year-long caching on previews and posters, a shorter cache and explicit content types on the sitemap and robots, `noindex` on the demo directory, and the usual `nosniff` / `X-Frame-Options` / referrer policy across everything.

## Stack

React 18 · TypeScript · Vite · Tailwind CSS · Framer Motion · React Router · Lucide · Vite SSR · Sharp · FFmpeg · Vercel
