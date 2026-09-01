# Techno Zone

**Live Demo:** https://www.technozoneisb.online
**Repository:** private
**Role:** design, build, content structure, technical search work, deploy.

![Techno Zone home page](../assets/screenshots/technozone-home.png)

## The business

Techno Zone have been putting in security and communication systems out of Rawalpindi since 2009. CCTV, access control, fire alarms, biometric attendance, telephone exchanges, video intercom, conference rooms, gate automation, solar, and general procurement, mostly for corporate, industrial and government clients.

Their problem was search. Somebody who needs cameras for a warehouse in Islamabad types roughly that, and one page listing a dozen services satisfies nobody looking for any of them. So the site got turned inside out: a page per service, each written about that service in that city, with the navigation and internal links pointing at them properly.

## Why a generator and not a framework

Almost all of it is copy. Twelve service pages plus about, projects, products, areas served, contact and the legal pages, every one of them sharing a header, a footer, a WhatsApp bar and a block of structured data. Maintain that by hand and the phone number will be wrong on page nine within a month.

But it didn't need React either. Bringing in a framework to render static text buys you a build step that can fail and a bundle to download, on a site whose visitors are frequently on mobile data in a car park.

So there's a small generator with no dependencies at all. Content sits as data in `build/content-services.js` and `build/content-pages.js`, `node build/generate.js` renders it, and the resulting HTML gets committed alongside a regenerated sitemap. Hosting doesn't change and the deploy pipeline has nothing in it to break.

A handful of pages drifted far enough from the template that generating them stopped being worthwhile, so those stay hand-written. They're named explicitly in the generator, which is how they still make it into the sitemap.

## Everything from one object

The canonical origin, the brand and the names people also search for, the year they started, the landline, the WhatsApp number, the email, the street, the city, the region, the areas covered, the social image and the logo. All of it, once, in one place.

Every one of those values either came out of the existing site or came from the owner directly. There's no invented decade of experience, no round number of installations, no review markup for reviews nobody left. The WhatsApp number appears because the business gave it to me. There's no mobile line listed because there isn't one.

## The search work

Twelve indexable service pages, each with its own title, description, canonical and social image. LocalBusiness markup carrying the real address, hours and coverage area, with Service nodes hanging off the individual pages. A generated sitemap covering the hand-written routes as well as the rendered ones. Robots with an absolute sitemap reference, and an `llms.txt` describing the business for models that go looking for one. A page for the surrounding towns, links running between the services so none of them sits on its own, and a proper 404 document rather than a bounce to the homepage.

There's a keyword map in the repo recording which page owns which query. Mostly that exists so two pages never end up quietly competing for the same phrase, which is the usual way this sort of site goes wrong.

## The front end

Dark, hand-written CSS, no framework. A product rail that runs continuously, a slider for the services, a WhatsApp button that follows you down the page, and the landline sitting in the top bar so calling is always one tap. Every photograph is the client's own equipment and installation work, converted to web formats with dimensions set so the layout doesn't shift while it loads.

## Stack

Node.js (custom generator) · HTML · CSS · vanilla JavaScript · JSON-LD · Vercel
