# Background

I build web applications end to end. The interface, the API behind it, and whatever it takes to get the thing live and findable.

I came into this through machine learning rather than through web work. Several years of computer vision, speech and model deployment: getting models off a notebook and onto edge devices, into containers, behind serverless endpoints, and keeping what they cost to run within reason. That's why I'm comfortable with the infrastructure end of a product, and it's why the AI features I put into web apps now tend to be wired in properly instead of bolted on the side.

These days the work is mostly client products and sites. React and Next.js on the front, Node and Python behind, and the performance and search work that decides whether anyone finds any of it.

Based in Islamabad.

## Front end

React and Next.js are the default, TypeScript wherever the project allows it. App Router and the older Next setups both, and plain Vite when a framework would only be in the way.

Motion is a real part of what I do rather than decoration on top. GSAP with ScrollTrigger for anything driven by scroll position, Framer Motion at the component level, Lenis for smoothing. I've built scroll-scrubbed frame sequences, pinned scenes with content fading over them, and procedural Three.js work through React Three Fiber, including a speaker assembled entirely in code so there's no model file to download.

The time doesn't go into making motion work. It goes into making it survive a phone. Decoded bitmaps and full-resolution frames will quietly consume a gigabyte on a handset, and getting out of that is a matter of stride, decode size, and being willing to drop things. I test reduced-motion behaviour on everything I build, because a sequence you can't turn off is an accessibility problem wearing a nice coat.

Layout: CSS Modules or Tailwind depending on the project, responsive from 320 upward, and automated shots at several widths that flag horizontal overflow rather than my dragging a window around and hoping.

## Back end

Express and Node for most APIs, Python and Flask when the work sits close to a model. Mongoose with MongoDB, Prisma and Drizzle with Postgres, Supabase where auth and storage coming along for the ride is worth it.

JWT and session cookies, hashing, validation and sanitisation at the boundary. Anything touching an LLM runs server side so keys never reach a browser, with history trimmed and capped before it's forwarded, and structured JSON coming back when the client needs to render something specific rather than a paragraph of text.

Integration work over the years: Groq, OpenAI-compatible APIs, Nodemailer, web-push, Power Automate, Go High Level, Calendly, Cal.com.

## Deployment

Vercel for most web projects. Serverless functions, rewrites and redirects, cache and security headers per path, environment config per stage. Docker and Compose where there's a Python worker or a GPU path alongside the web app. Kubernetes and Kubeflow, plus Lambda for burst inference, from the infrastructure years.

Given the choice I'll take the pipeline with the fewest moving parts the project can stand. One site I finished recently is a generator committing plain HTML, so its deploy is a file copy with nothing in it that can fail.

## Search and performance

A bigger slice of my work than it usually is for a developer, largely because I keep being handed sites where nobody did it.

Prerendering or SSR so routes return real HTML instead of an empty div. Titles, descriptions and canonicals per route, derived from one source that the build and the client both read so they can't disagree. Structured data with entities referenced rather than repeated. Generated sitemaps and robots, real 404 documents, and a keyword map so two pages don't end up fighting each other for the same query.

I won't put a claim in structured data that the business can't stand behind. No invented ratings, no review markup where there are no reviews, no social profiles that don't exist.

On performance: mounting heavy media on intersection, pausing video that's left the screen, reserving aspect ratio so nothing jumps, immutable caching on assets whose names never change, and keeping third-party JavaScript off pages with a budget to hold. That last one includes gating analytics behind a real measurement ID, so a site doesn't end up shipping a tracking script that reports to nobody.

## Machine learning

Vision and image work: segmentation, virtual try-on, single-image 3D reconstruction, detection models. Speech: STT and TTS pipelines tuned for use in real time rather than in a demo. Model work with TFLite, quantisation and C++ preprocessing to hit frame-rate targets on hardware that isn't a workstation. LoRA fine-tuning on the generative side.

On serving: RAG retrieval, function calling, and getting inference costs down to a number a business can actually live with.

## Languages and tools

TypeScript, JavaScript, Python, C#, Java, C++, Rust, SQL

React, Next.js, Vite, Three.js, GSAP, Framer Motion, Tailwind, Node, Express, Flask, Prisma, Drizzle, Mongoose

MongoDB, Postgres, Neon, Supabase

Docker, Kubernetes, AWS, Vercel, Microsoft Cloud

Puppeteer, Playwright, Vitest, FFmpeg, Sharp

## How I work

I read the code before I change it. Most of what's on this profile arrived half-built, and the useful move is nearly always finding the one wrong assumption sitting underneath, a canonical aimed at somebody else's domain, frames held at a resolution nothing paints at, rather than starting again from an empty folder.

I check things by running them. The motion projects have Puppeteer scripts that drive the real site and report frame timing, overflow and console errors, because motion is exactly the kind of work that looks fine on the machine it was built on and nowhere else.

And I don't put numbers on a client's site that the client can't stand behind.

[Back to the portfolio](README.md) · [LinkedIn](https://www.linkedin.com/in/muhammad-hamza5)
