# AI, ML and cloud work

Earlier projects, from the years I spent mostly on machine learning systems and infrastructure rather than product web work. Kept here in full — images and demo media included — because it's still the part of my background clients ask about most.

---

## Callup.ai

**Live:** https://callup.ai

Voice calling agents built on transformer models, with a Python backend behind an Express service layer and a Next.js front end. The split was deliberate: the model work stayed in Python, Express handled auth, routing and the client-facing surface, so neither side had to know much about the other.

Most of the work was latency and voice quality. A calling agent that takes two seconds to respond doesn't sound like a person, so a lot of it was shaving time off the path between speech ending and audio starting. Retrieval is RAG-based so agents can answer from the client's own data, and function calling lets the model trigger real actions during a call rather than just describing them.

**Technologies:** Python, Node.js, Express, Next.js, transformers, RAG

![Callup.ai](../public/callupai.png)

Sample of the generated voice output: [airesults.mp3](../public/airesults.mp3)

---

## Disease detection from eye scans

An AI model that analyses eye scans to detect infections and stomach-related conditions, built to run on edge devices rather than in the cloud — the point was diagnostics in clinics without reliable connectivity.

Getting it to 60 FPS on low-power hardware meant converting to TFLite and quantising, then rebuilding the preprocessing in C++ so the pipeline wasn't the bottleneck. The Java layer handled camera capture and the device-side application.

**Technologies:** Java, Python, TFLite, C++

![AI disease detection](../public/aidisease.jpeg)

---

## Real-time AI avatars (STT/TTS)

Generative models producing synthetic faces and voices with speech-to-text and text-to-speech running in real time. Roop for face work and LoRA fine-tuning for the model training, tuned for output that holds up at conversational speed rather than only in rendered stills.

**Technologies:** Python, Node.js, generative AI, Roop, LoRA

Sample output: [aimodel.mp4](../public/aimodel.mp4)

---

## Virtual try-on

A try-on application for e-commerce — customers see themselves in an outfit before buying. Computer vision for body and garment segmentation, generative imaging for the composite. Built to cut return rates, which is where most of the value in this sits for a retailer.

**Technologies:** generative AI, computer vision, image processing

![Virtual try-on](../public/viton.png)

---

## Email sales automation

Business process automation for a sales team, built on Microsoft Cloud. Power Automate and Copilot ran the workflows, with integrations into Go High Level, Calendly and Cal.com so scheduling and follow-ups happened without anyone copying details between systems, plus a dashboard for monitoring what was in flight.

The reported result was around a 30% improvement in sales efficiency, mostly from removing manual handoffs.

**Technologies:** Microsoft Cloud, Power Automate, Node.js, C#

![Email sales automation](../public/process_aitomation.avif)

---

## 2D image to 3D model

Single-image 3D reconstruction — feed it one photograph, get a detailed 3D model out. Python handled the reconstruction pipeline, with a Ruby on Rails interface for content creators to upload and manage their models.

**Technologies:** Python, generative AI, Ruby on Rails

![2D to 3D model creation](../public/2dto3d.webp)

---

## Kubernetes scaling for a fintech

Backend infrastructure for serving ML models at scale. Docker and Kubernetes for the cluster, Kubeflow for the model deployment and management side, and AWS Lambda for the burst inference path.

The Lambda work is what mattered commercially: it brought inference cost down to roughly $1 per 1000 requests, which changed what the company could afford to offer.

**Technologies:** Docker, Kubernetes, Kubeflow, AWS Lambda

---

## Sales funnel for a digital marketing company

A multi-stage funnel covering prospecting, lead generation and automated outreach, with analytics feeding back into targeting so the list got better over time rather than just bigger.

**Technologies:** Node.js, Python, Microsoft Cloud, Power Automate

---

## Shredded Apes

**Status:** no longer online — the domain has lapsed

A Web3 platform combining staking, raffles, auctions and e-commerce in one ecosystem. Rust backend handling the transaction and security side, React front end, Node and Express in between.

**Technologies:** Node.js, Rust, React.js, Express.js

![Shredded Apes](../public/shreddedapes.png)
