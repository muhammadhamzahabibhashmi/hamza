# Techno Zone

**Live:** https://www.technozoneisb.online
**Repository:** private
**Role:** design, build, content structure, technical SEO, deployment

![Techno Zone home page](../assets/screenshots/technozone-home.png)

## What it is

Techno Zone has been installing security and communication systems out of Rawalpindi since 2009 — CCTV, access control, fire alarms, biometric attendance, telephone exchanges, video intercom, conference systems, gate automation, solar, and general order supply for corporate, industrial and government clients.

Their problem was search. Someone looking for CCTV installation in Islamabad types exactly that, and a single services page listing a dozen things doesn't rank for any of them. So the site is built the other way round: a landing page per service, each one written about that service in that city, with the site's own structure pointing at them.

## Why a generator instead of a framework

The site is mostly content. Twelve service pages plus about, projects, products, areas served, contact and the legal pages — all sharing one header, footer, WhatsApp bar and schema block. Hand-maintaining that means the phone number is wrong on page nine the first time it changes.

But it also didn't need React. Pulling in a framework to render static text would have added a build step to the deploy pipeline and a JavaScript bundle to a site whose visitors are often on mobile data.

So it's a small Node generator with no dependencies. Pages are described as data in `build/content-services.js` and `build/content-pages.js`, and `node build/generate.js` renders them into static HTML that gets committed to the repo along with the regenerated sitemap. Hosting doesn't change — Vercel keeps serving files, and there's no build step in the deploy at all.

A few pages are deliberately hand-maintained rather than generated, because they diverged enough from the template to be worth it. Those are listed explicitly in the generator so the sitemap still covers them.

## One source of truth

Everything a crawler or a customer reads about the business comes from a single config object: the canonical origin, brand and alternate names, founding date, landline, WhatsApp number, email, street address, city, region, areas served, OG image and logo.

Every value in it is either verified from existing site content or was supplied by the owner. Nothing is invented — no made-up years of experience, no invented project counts, no review schema for reviews that don't exist. The WhatsApp number is on the site because the business gave it; there's no mobile line listed because there isn't one.

## Technical SEO

- one indexable landing page per service, each with its own title, description, canonical and OG image
- LocalBusiness schema carrying the real address, hours and service area, with Service nodes per page
- generated `sitemap.xml` covering both generated and hand-maintained routes
- `robots.txt` with an absolute sitemap URL, plus an `llms.txt` describing the business for language models
- an areas-served page for the surrounding towns, and internal links from every service page back into the set
- a real 404 document rather than a redirect to home

There's a keyword map and an audit trail in the repo tracking which page owns which query, so two pages never end up competing for the same term.

## Front end

Dark theme, hand-written CSS, no framework. A product rail that scrolls continuously, a services slider, a sticky WhatsApp button and a top bar carrying the number so calling is always one tap away. Images are all client-supplied equipment and installation photos, processed into web formats with sizes set so nothing shifts as the page loads.

## Stack

Node.js (custom static generator) · HTML · CSS · vanilla JavaScript · JSON-LD · Vercel
