# Loudhouse Marketing

**Repository:** private
**Role:** full stack. Front end, motion, API, search, deploy.

![Loudhouse home page](../assets/screenshots/loudhouse-home.png)

## The brief

Loudhouse is a small agency in Islamabad. They keep their client list short on purpose, put a reference number on every job, and won't sign a project off until whatever number they agreed to move has moved.

That positioning ruled out anything template-shaped. An agency whose whole pitch is getting people to look at things can't have a website nobody looks at. So the site is put together as a run of scenes: the landing page opens on Times Square with Loudhouse up on the billboards, About plays as a film you scrub with the scrollbar, Services and Work share a speaker that comes apart as you move down the page, and Cases is laid out like a file someone left on a desk.

Underneath the presentation it's a working app. The contact form validates, saves to MongoDB and sends mail. An assistant answers questions about the agency. A short quiz works out which services a visitor is actually after.

## How it's put together

npm workspaces, with a Vite client and an Express server sharing a repo.

The server runs as a normal Express process in development and as serverless functions in production, so the client carries a thin `api/` folder holding the deployed handlers. Three routes do the work: `/api/leads`, `/api/chat`, `/api/recommend`. Routing on the front is React Router, with a Vercel rewrite sending anything that isn't an asset or an API path back to `index.html`.

## The About sequence

This ate most of the schedule.

What I wanted was a film you control with the scrollbar. Scroll forward and it advances, scroll back and it rewinds, stop anywhere and it holds on that exact frame. The obvious approach is to set `video.currentTime` and let the browser seek, but browsers don't agree on what that means. Ask for the same timestamp twice and you can get two different pictures, and some engines quietly snap to the nearest keyframe instead of the frame you asked for.

So the video never plays. A build script pulls the 4K master apart into WebP stills with a manifest, and a canvas draws whichever still belongs to the current scroll offset. ScrollTrigger sets a target index, a requestAnimationFrame loop eases toward it rather than jumping, and the real HTML sections fade in on top of the pinned canvas.

That was fine on a laptop and hopeless on a phone. Each still was being kept as a decoded `ImageBitmap`, and a decoded bitmap is raw pixels: no compression at all. 181 stills at 1080 by 1920, four bytes a pixel, works out somewhere near 1.5 GB. The tab spent its life allocating and reclaiming instead of drawing. Two changes sorted it, neither of which touched the artwork:

- on small screens, use every second still. Over the shorter scrub distance that's still about a frame per 4vh of travel, which nobody notices.
- decode to the size the canvas is going to paint at, not the size the file happens to be.

That landed around 139 MB, call it a tenfold cut. Desktop keeps all 226 frames and its full pixel ratio, because there the resize only ever shrinks something that was about to be shrunk anyway. If the browser reports a preference for reduced motion the sequence doesn't run at all.

## The speaker

The speaker on Services and Work is generated in code rather than loaded as a model. Rounded box geometry, standard materials, and every part registered by name so it can be moved on its own.

It gets built once and used twice. On Work it disassembles under scroll. On Services it turns slowly on its own as a background object. Same geometry both times, different lighting and different animation wrapped around it. Doing it this way meant no `.glb` to download and no round trip through Blender every time a panel needed to sit somewhere else.

## The two AI routes

Both proxy Groq from the server, so the key stays out of the browser.

The **assistant** is handed a prompt containing everything it may talk about and instructed to work from that alone. Anything off topic gets a short refusal and a nudge back toward services, process or starting a project. It answers in a sentence or two by default and only goes longer when somebody asks it to, which matters because the brand voice is blunt and a chatbot that rambles would undercut it. Incoming history gets cleaned first: roles filtered, each message clipped, the whole thing capped at ten turns.

The **recommender** runs a short interview. Four questions maximum, each one built from what came before, then a suggested stack of services. It replies in JSON rather than prose so the interface can render proper option chips on the way through and a real result at the end, with a written brief that has to describe the visitor's own situation back to them rather than filling space.

## Search

There's no helmet library. A site this size needs a title, a description, a canonical, some Open Graph tags and one block of structured data kept in step with the current route, so there's a small hook that writes those in and marks everything it creates so it can tidy up when the route changes.

Beyond that: sitemap, robots, a couple of permanent redirects for URLs that changed name, and long cache headers on the frame folders since those filenames never change once they're written.

## Checking motion

Motion is difficult to judge by looking at it, especially on the machine you built it on. So `tools/` holds a set of Puppeteer scripts that drive the real site and report back: frame timing under scroll, whether the loader hands over to the hero cleanly, whether anything overflows sideways at any width, whether reduced motion genuinely turns the sequences off, how two viewports differ, and what the console says. Most of the mobile work above came out of those numbers rather than out of how the page felt.

## Stack

React 18 · Vite · React Router · Three.js · React Three Fiber · Drei · GSAP ScrollTrigger · Framer Motion · Anime.js · Lenis · Express · MongoDB · Mongoose · Nodemailer · Groq · Puppeteer · Vercel
