# Background

I build web applications end to end — the interface, the API behind it, and whatever it takes to get the thing live and found.

My route into it was through machine learning. I spent several years on computer vision, speech and model deployment: getting models off a notebook and onto edge devices, into containers, behind serverless endpoints, and keeping the cost of running them sane. That work is why I'm comfortable with the infrastructure side of a product and why AI features in the apps I build now tend to be wired properly rather than bolted on.

These days most of my work is client products and sites: React and Next.js front ends, Node and Python back ends, and the performance and SEO work that decides whether anyone sees them.

Based in Islamabad, Pakistan.

---

## Front end

React and Next.js are what I reach for, in TypeScript where the project allows it. I'm comfortable in both the App Router and older Next setups, and with plain Vite when a framework would be overhead.

Motion is a real part of my work rather than a garnish. GSAP with ScrollTrigger for scroll-driven sequences, Framer Motion for component-level animation, Lenis for smooth scrolling. I've built scroll-scrubbed frame films, pinned scenes with cross-fading content, and procedural Three.js scenes with React Three Fiber — including an exploded 3D speaker built entirely in code so there's no model to download.

The part that takes the time isn't making motion work, it's making it survive contact with a phone. Decoded bitmaps and full-resolution frames will eat a gigabyte of memory on a handset without complaining, and the fix is usually stride, decode size and knowing what to drop. I check reduced-motion behaviour on everything — a scroll film that can't be turned off is an accessibility problem, not a feature.

Layout work: CSS Modules or Tailwind depending on the project, responsive from 320 up, and automated checks that shoot every route at several viewports and flag horizontal overflow rather than trusting a resize by hand.

## Back end

Express and Node for most APIs, Python and Flask where the work is model-adjacent. Mongoose with MongoDB, Prisma and Drizzle with PostgreSQL, Supabase where auth and storage come along with it.

Auth with JWT and session cookies, password hashing, input validation and sanitisation at the boundary. AI integrations run server-side so keys stay off the client, with history capped and truncated before anything is forwarded, and structured JSON responses when the client needs to render something specific rather than a paragraph.

Third-party integration work: Groq, OpenAI-compatible APIs, Nodemailer, web-push, Power Automate, Go High Level, Calendly and Cal.com.

## Deployment

Vercel for most web projects — serverless functions, rewrites and redirects, per-path cache and security headers, environment configuration per stage. Docker and Docker Compose where a project has a Python worker or GPU path alongside the web app. Kubernetes and Kubeflow, and AWS Lambda for burst inference, from the ML infrastructure work.

I generally prefer a deploy pipeline with as few moving parts as the project allows. One recent site is a static generator committing plain HTML, so the deploy is a file upload with no build step to break.

## SEO and performance

This is a bigger part of my work than it usually is for a developer, mostly because I keep inheriting sites where it was never done.

Technical SEO: prerendering or SSR so routes serve real HTML rather than an empty div, per-route titles, descriptions and canonicals derived from one source that both the build and the client import so they can't drift, JSON-LD with entities referenced by `@id` rather than repeated, generated sitemaps and robots, real 404 documents, and keyword-to-URL mapping so pages don't compete with each other.

I don't put claims in schema that the business can't back — no invented ratings, no review markup for reviews that don't exist, no social profiles that aren't there.

Performance: lazy-mounting heavy media on intersection, pausing off-screen video, reserving aspect ratio so nothing shifts, immutable caching on content-addressed assets, and keeping third-party JavaScript off pages with a Core Web Vitals budget — including gating analytics behind a real measurement ID so the site doesn't ship an inert tracking script.

## Machine learning

Computer vision, image processing and generative imaging: segmentation, virtual try-on, single-image 3D reconstruction, detection models. Speech: STT and TTS pipelines tuned for real-time use. Model work with TFLite, quantisation and C++ preprocessing to hit frame-rate targets on edge hardware, and LoRA fine-tuning for generative models.

On the serving side: RAG retrieval, LLM function calling, and getting inference cost down to something a business can actually run.

## Languages and tools

TypeScript, JavaScript, Python, C#, Java, C++, Rust, SQL

React, Next.js, Vite, Three.js, GSAP, Framer Motion, Tailwind, Node.js, Express, Flask, Prisma, Drizzle, Mongoose

MongoDB, PostgreSQL, Neon, Supabase

Docker, Kubernetes, AWS, Vercel, Microsoft Cloud

Puppeteer, Playwright, Vitest, FFmpeg, Sharp

---

## How I work

I read the existing code before changing it. Most of the projects above are things I inherited part-built, and the useful move is usually finding the one wrong assumption underneath — a canonical pointing at the wrong host, frames held at full resolution — rather than rewriting from scratch.

I check work by running it. The motion projects have Puppeteer scripts that drive the real site and report frame timing, overflow and console errors, because motion is exactly the kind of thing that looks fine on the machine it was built on.

I don't put numbers on a site that the owner can't stand behind.

---

[Back to portfolio](README.md) · [LinkedIn](https://www.linkedin.com/in/muhammad-hamza5)
