# Hamza Habib Hashmi

Full Stack Developer building modern web applications, AI-powered products, and scalable digital experiences.

Welcome to my GitHub profile! I have a diverse skill set in various cutting-edge technologies. Below is a showcase of some of the projects I've worked on.

---

## About Me

👨‍💼 **Profession:** Solutions Architect  
🔧 **Skills:** Python, Flask, Rust, AWS, Microsoft Cloud, C#, Java, TFLite, C++, Docker, Kubernetes, AWS Lambda, Generative AI, Computer Vision, Image Processing, Electron.js

I specialize in:
- Developing scalable, secure, and efficient solutions tailored to client needs.
- Creating innovative AI models and integrating them into practical applications.
- Enhancing user experience through cutting-edge web and mobile technologies.
- Leading cross-functional teams to deliver high-impact projects on time and within budget.
- Implementing cloud infrastructure and DevOps practices to optimize performance and reduce costs.
- **Technologies:** Python, Node.js, Next.js, Express, Rust, React.js, Microsoft Cloud, Power Automate, C#, Ruby on Rails, Java, TFLite, C++, Docker, Kubernetes, AWS Lambda, Generative AI, Computer Vision, Image Processing, Electron.js

**Recent front-end and product work:** React · Next.js · TypeScript · Three.js · GSAP · Framer Motion · Tailwind · Prisma · Supabase · Vercel

---

## Achievements

- Successfully deployed over 200 models from POC/MVP to production, demonstrating expertise in transforming innovative ideas into robust, scalable solutions.
- Achieved a 30% increase in sales efficiency and reduced manual intervention through automation.
- Improved early detection rates and patient outcomes with innovative AI technology in healthcare.
- Reduced operational costs to $1 per 1000 requests by leveraging AWS Lambda and scalable infrastructure.
- Enhanced customer satisfaction and reduced return rates with advanced virtual try-on solutions.
- Increased user engagement and transaction volume by implementing innovative features in blockchain projects.
- Streamlined the sales process and improved conversion rates with automated outreach workflows.
- Led cross-functional teams to deliver high-impact projects on time and within budget.

---

## Recent Projects

### Loudhouse Marketing

Loudhouse is an agency in Islamabad that runs a deliberately small book of clients. The brief was a site people would watch rather than read, so most of the build went into motion: the landing scene puts the brand up on Times Square billboards, the About route plays as a film you scrub with the scrollbar, and a speaker model pulls itself apart across Services and Work.

Behind all that it's an ordinary MERN app. Contact submissions get validated, written to MongoDB and mailed on. Two further routes sit on top of Groq, one running the site assistant and one walking a visitor through four questions before suggesting what to buy.

Getting the About sequence usable on phones took the longest. Painting frames to a canvas instead of seeking a video solved the stutter on desktop but made things worse on mobile, because a decoded frame sits in memory uncompressed. At 1080×1920 the full set came to around 1.5 GB. Dropping to every second frame and decoding at the size the canvas actually paints brought it down to roughly 139 MB.

**Tech Stack:** React 18, Vite, Three.js, React Three Fiber, GSAP ScrollTrigger, Framer Motion, Lenis, Express, MongoDB/Mongoose, Nodemailer, Groq API, Vercel

**Key Work:** front end and the whole motion layer, the speaker built in code rather than modelled, the frame pipeline and its memory fix, Express routes plus the serverless versions for leads and chat, per-route metadata and structured data, and a folder of Puppeteer scripts for checking smoothness, reduced motion and overflow.

**Repository:** private · [Full write-up →](projects/loudhouse.md)

![Loudhouse](assets/screenshots/loudhouse-home.png)

---

### Formynex

A storefront for animated website templates. Instead of selling from static previews, all 44 entries in the catalogue link to something you can actually scroll through yourself, and there's no card payment at the end: buyers collect what they like in a drawer, then an agent prices the licence with them.

It came to me as a plain Vite SPA serving an empty root div on every URL, with the one canonical tag in `index.html` pointing at a completely different domain. Every template page was announcing itself as a copy of something else. I added an SSR pass and a prerender step so each route ships finished HTML, and moved every title, description and canonical into a single module that the build script and the browser both read from. Preview media stays unmounted until its card gets close to the viewport, and anything off screen stops playing.

**Tech Stack:** React 18, TypeScript, Vite, Tailwind, Framer Motion, React Router, Vercel

**Key Work:** catalogue and filtering, the selection drawer with its localStorage layer, the prerender pipeline, sitemap and robots output, structured data, the lazy preview component, a script that shoots every route at three widths to catch overflow, and a contrast check over the palette.

**Live Demo:** https://formynex.site · **Repository:** private · [Full write-up →](projects/formynex.md)

![Formynex](assets/screenshots/formynex-home.png)

---

### Techno Zone

Techno Zone have been fitting CCTV, access control, fire alarms, exchanges and solar around Rawalpindi since 2009. Their problem was visibility. People search for one service in one city, and a page listing eleven of them won't rank for any. So each service got a page of its own, written around the phrase somebody would actually type.

For a site that's almost entirely copy, React would have been overhead. I wrote a small generator instead, no dependencies. Page content lives in data files, `node build/generate.js` turns it into HTML, and the output gets committed to the repo, which keeps deploys down to a file copy. Phone numbers, address and service names all resolve from one object, so changing the landline is a one-line edit rather than twenty.

**Tech Stack:** Node.js (custom generator), HTML, CSS, vanilla JavaScript, Vercel

**Key Work:** the generator and its content model, design and front end, twelve service pages, LocalBusiness and Service markup, sitemap and robots, WhatsApp and call hooks, and processing the client's equipment photography for the web.

**Live Demo:** https://www.technozoneisb.online · **Repository:** private · [Full write-up →](projects/technozone.md)

![Techno Zone](assets/screenshots/technozone-home.png)

---

### XLIME GEAR

Thirteen screens for a football kit brand that lets teams design their own strip: shop, product pages, the kit builder, cart and checkout, accounts, bulk ordering for clubs, and an admin side for handling what comes in. Everything funnels into the builder, where you pick a base kit, set primary and trim colours, upload a crest and finish with a quote request instead of a payment, since club orders get priced job by job.

Packaging it turned into its own piece of work. The client had no way to run a dev server, so all thirteen pages went into a single HTML file, each one embedded whole next to its screenshot, behind a landing page and a viewer that runs them live inside a device frame. Before calling it finished I had the script decode every embedded page back out and byte-compare it against the source.

**Tech Stack:** HTML, Tailwind, semantic design tokens, Node.js packaging script

**Key Work:** the screen designs and the dark, motion-led system underneath them, the builder flow, the admin views, and the packaging and verification script.

**Status:** design prototype, not deployed · **Repository:** private · [Full write-up →](projects/xlimegear.md)

![XLIME GEAR](assets/screenshots/xlimegear-jersey-builder.png)

---

## Projects

### [Callup.ai](https://callup.ai)
Voice calling agents built using AI transformers, Node.js, Python, and Next.js.

- **Technologies:** Python, Node.js, Express, Next.js
- **Key Features:**
  - Implemented secure multi-layer architecture with Python backend and Express server layer.
  - Enhanced AI call response latency and trained realistic-sounding AI voices.
  - Integrated RAG-based implementation for efficient data retrieval from databases.
  - Enabled function calling from LLM to tailor responses to client needs.
  - Achieved significant improvements in response time and voice quality, providing a competitive edge.

![Callup.ai](public/callupai.png)

#### results
Voice sample: [airesults.mp3](public/airesults.mp3)

<audio controls>
    <source src="public/airesults.mp3" type="audio/mp3">
    Your browser does not support the audio tag.
</audio>


---

### AI Disease Detection Using Eye Scans
AI model to detect infections and stomach-related diseases from eye scans.

- **Technologies:** Java, Python, TFLite, C++
- **Key Features:**
  - Developed an AI model to analyze eye scans and detect diseases.
  - Implemented compatibility for edge devices to achieve real-time performance at 60 FPS.
  - Utilized TFLite for efficient model deployment on low-power devices.
  - Enhanced healthcare diagnostics through innovative AI technology.
  - Significantly improved early detection rates and patient outcomes.

![AI Disease Detection](public/aidisease.jpeg)

---

### AI Models D-IDs
Created AI-based models with STT and TTS for real-time results.

- **Technologies:** Python, Node.js, Generative AI
- **Key Features:**
  - Developed high-quality, real-time AI models for STT and TTS.
  - Generated realistic faces and artificial models using generative AI techniques.
  - Implemented Roop and LoRA for enhanced model training and performance.
  - Delivered state-of-the-art AI solutions for various applications.
  - Improved user interaction and engagement with high-fidelity AI models.

#####  result
Video sample: [aimodel.mp4](public/aimodel.mp4)

<video controls>
    <source src="public/aimodel.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

---

### Virtual Try-ons
Virtual try-on application using generative AI and computer vision.

- **Technologies:** Generative AI, Computer Vision, Image Processing
- **Key Features:**
  - Developed virtual try-ons allowing users to see themselves in different outfits.
  - Utilized advanced computer vision and image processing techniques for realistic try-ons.
  - Enhanced user experience with accurate and interactive virtual fitting.
  - Implemented generative AI to generate high-quality try-on images.
  - Increased customer satisfaction and reduced return rates for e-commerce platforms.

![Virtual Try-ons](public/viton.png)

---



### Email Sales Automation for Business Process Automation
Automated sales processes using Microsoft cloud technologies.

- **Technologies:** Microsoft Cloud, Power Automate, Node.js, C#
- **Key Features:**
  - Developed automation workflows using Power Automate and Copilot.
  - Built a user-friendly dashboard for monitoring and managing sales activities.
  - Integrated Go High Level, Calendly, and Cal.com to streamline scheduling and follow-ups.
  - Enhanced efficiency and productivity through business process automation.
  - Achieved a 30% increase in sales efficiency and reduced manual intervention.

![Email Sales Automation](public/process_aitomation.avif)

---

### High Fidelity 2D Image to 3D Model Creation
Transforms a single image into detailed 3D models.

- **Technologies:** Python, Generative AI, Ruby on Rails
- **Key Features:**
  - Developed a high-fidelity 3D creation technology for realistic digital content.
  - Achieved unprecedented realism and accuracy in 3D models from 2D images.
  - Integrated generative AI techniques to enhance model quality and detail.
  - Implemented using Python for backend processing and Ruby on Rails for web interface.
  - Enabled content creators to produce high-quality 3D models efficiently.

![2D to 3D Model Creation](public/2dto3d.webp)

---

### Kubernetes for Vertical Scaling for a Fintech Company
Implemented scalable backend infrastructure.

- **Technologies:** Docker, Kubernetes, Kubeflow, AWS Lambda
- **Key Features:**
  - Built a highly scalable backend infrastructure using Docker and Kubernetes.
  - Implemented Kubeflow for efficient ML model deployment and management.
  - Leveraged AWS Lambda to reduce operational costs to $1 per 1000 requests to models.
  - Achieved significant performance improvements and cost savings.
  - Enabled the fintech company to scale operations seamlessly and efficiently.


---

### Sales Funnel for a Digital Marketing Company
Built a comprehensive sales funnel from prospecting and lead generation to automated outreach.

- **Technologies:** Node.js, Python, Microsoft Cloud, Power Automate
- **Key Features:**
  - Developed a multi-stage sales funnel for a digital marketing company.
  - Automated prospecting and lead generation processes to maximize efficiency.
  - Integrated automated outreach workflows to nurture and convert leads.
  - Utilized data analytics to refine targeting and improve conversion rates.
  - Increased lead conversion rates and streamlined the sales process.

---

### Shredded Apes
A complete project involving staking, raffle, auction, and eCommerce ecosystem using Web3 blockchain.

- **Technologies:** Node.js, Rust, React.js, Express.js
- **Key Features:**
  - Developed a comprehensive staking, raffle, and auction platform.
  - Created an eCommerce ecosystem leveraging Web3 blockchain technologies.
  - Built a robust Rust backend to handle complex transactions and ensure security.
  - Delivered a seamless user experience with React.js front-end.
  - Successfully increased user engagement and transaction volume through innovative features.

![Shredded Apes](public/shreddedapes.png)

---

## More

[Background and skills in detail](experience.md)

## Connect with Me

[![GitHub Followers](https://img.shields.io/github/followers/muhammadhamzahabibhashmi?label=Follow&style=social)](https://github.com/muhammadhamzahabibhashmi/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/muhammad-hamza5)
