# Formynex

**Live Demo:** https://formynex.site
**Repository:** private
**Role:** full stack. Front end, rendering pipeline, search, deploy.

![Formynex home page](../assets/screenshots/formynex-home.png)

## The idea

Formynex sells animated website templates, and the argument the whole product rests on is that you shouldn't have to judge one from a still image. Every entry in the catalogue opens something real that you can move around in, on whatever device you happen to be holding.

There are 44 of them at the moment. They're grouped by industry, but also by how they behave: 29 respond to scroll position, 19 use projected geometry rather than a flat image faking depth, 17 draw their scenes per frame in code, and 42 arrive as one file that will sit on any host, with nothing to build first. Those figures get counted from the catalogue itself when the page renders, so nobody has to remember to update a number in the copy.

Nothing gets bought with a card. Visitors put what they like into a drawer and hand that over, and an agent works out licensing and price from there. That one decision shapes everything downstream, because the thing being optimised for isn't a completed checkout, it's a message.

## Fixing what search engines saw

The site arrived as a normal Vite single-page app. Every URL returned the same empty root element, and the sole canonical tag lived in `index.html` pointing at a hostname that wasn't even this site. Nine template pages, all insisting they were duplicates of something else entirely.

The build now runs in four stages: client bundle, server bundle, prerender, then copy the demos into place. The prerender step walks every route and writes real HTML for it, one file per template plus the homepage and a genuine 404 document, and emits robots, sitemap and manifest at the paths crawlers expect.

The part that actually matters is where the text comes from. Titles, descriptions, canonicals and structured data all live in one `seo.ts`, imported by the prerender script and the client router alike. What a crawler is served and what a visitor sees after clicking around cannot disagree, because there's only one function producing either.

Structured data works the same way. The publisher gets described once with an `@id` and everything else refers back to it rather than restating it. There's no rating, no price, no licence term and no compatibility claim in there, because none of that was mine to assert. The `sameAs` array is left out altogether instead of filled with plausible-looking profiles that don't exist.

## Previews, without ruining the page

Every card in the grid carries motion of some kind, GIF or animated WebP or MP4. That's a lot to ask of one page.

Media doesn't get attached to the DOM until an intersection observer reports its card is nearly in view, and a video that leaves the screen gets paused instead of left running underneath the fold. A skeleton holds the right aspect ratio while things decode so nothing jumps, and if a file fails the component drops to its poster, then to a plain placeholder, rather than showing a broken frame. Where the browser asks for reduced motion it never plays anything at all.

## Measurement, honestly

There's a GA4 layer, but it does nothing whatsoever unless a measurement ID gets supplied at build time. Without one, every function it exports returns immediately: no script tag, no network request, no third-party code dropped onto pages that already have a performance budget to keep.

That gate is on purpose. A measurement ID belongs to whoever owns the property, and inventing a placeholder gives you the worst of both worlds, a site that appears to be tracking and silently records nothing. The event names line up with the KPI document, so whoever configures the property later can point key events at them without renaming anything.

## Scripts that exist because something went wrong

- **responsive audit** loads every route at 320, 768 and 1440 and reports anything running off the side
- **contrast check** runs the palette against WCAG ratios rather than trusting how it looks
- **brand assets** regenerates logo, social image and favicons from masters so they can't fall out of step
- **tile builders** compose the promotional artwork for particular templates
- **demo copy** moves the standalone demos into the output, served `noindex` so they never compete with the catalogue pages meant to sell them

## Hosting

Vercel, with rules set per path. A year of immutable caching on previews and posters, a short cache and explicit content types on robots and the sitemap, `noindex` across the demo folder, and the usual nosniff, frame and referrer headers everywhere else.

## Stack

React 18 · TypeScript · Vite · Tailwind · Framer Motion · React Router · Lucide · Vite SSR · Sharp · FFmpeg · Vercel
