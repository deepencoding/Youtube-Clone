# 🎬 YouTube Clone

**Stack**: TypeScript • Next.js • React • tRPC • Firestore • GCP • Docker
[🚀 Live Demo](https://yt-web-client-543501541359.asia-south2.run.app/)

---

## 🚀 Project Overview

A full-stack, server-side–rendered YouTube-style application built with modern web technologies and scalable cloud infrastructure. It supports seamless video upload, automatic transcoding, metadata management, and smooth playback—enhancing user engagement and platform usability.

---

## 🎯 Key Features

- **Full‑stack Next.js architecture** with TypeScript, React, and tRPC for seamless SSR and API handling.
- **Scalable, event-driven video pipeline** using Dockerized FFmpeg and Google Cloud Pub/Sub, supporting concurrent uploads and low-latency transcode.
- **Real-time metadata and media storage** with Firestore and Cloud Storage for consistent data and improved UX.
- **Production-ready deployment** on Cloud Run for both API and transcoder services, with automatic scaling and high reliability.

---

## 🏗️ Architecture Diagram

```
[ User ] → Next.js Web UI (React/tRPC) → tRPC API → Cloud Run
→ Upload → Firestore metadata & Cloud Storage (raw video)
→ Pub/Sub → Cloud Run transcode service (FFmpeg in Docker)
→ Cloud Storage (HLS segments & thumbnails) → Firestore metadata update
```

---

## 🔧 Tech Stack

| Layer                    | Technology & Tools                                               |
|--------------------------|------------------------------------------------------------------|
| **Frontend**             | Next.js (app router), React, tRPC, Tailwind CSS (optional)       |
| **Backend / API**        | tRPC (Next.js), Firestore, Cloud Storage, Pub/Sub                |
| **Video Processing**     | FFmpeg (Docker), Cloud Run, Pub/Sub event-driven pipeline        |
| **Cloud Infrastructure** | Google Cloud Firestore, Storage, Pub/Sub, Cloud Run              |
| **Containerization**     | Docker images for API and transcoder services                    |

---

## 🧪 Getting Started (Local)

1. **Clone the repo**

```bash
git clone https://github.com/deepencoding/Youtube-Clone.git
cd Youtube-Clone
```

1. **Install dependencies**

```bash
npm install
# or yarn / pnpm
```

1. **Set up GCP credentials**

Create a `.env.local` with:

```.env
NEXT_PUBLIC_FIRESTORE_PROJECT_ID=your-gcp-project
FIRESTORE_CLIENT_EMAIL=…
FIRESTORE_PRIVATE_KEY=…
NEXT_PUBLIC_STORAGE_BUCKET=…
NEXT_PUBLIC_PUBSUB_TOPIC=…
```

1. **Run development server**

```bash
npm run dev
```

Then open [localhost](http://localhost:3000).

1. **Run transcoder locally**

```bash
cd services/transcoder
docker build -t yt-transcoder .
docker run yt-transcoder
```

Make sure your Pub/Sub emulator or real GCP topic is accessible.

## 🧩 Production Setup

1. **Containerize** using the provided Dockerfiles for both root and `services/transcoder`.
2. **Deploy** two Cloud Run services:
   1. `youtube-clone-api` – for Next.js API and SSR functions.
   2. `youtube-clone-transcoder` – for continuous transcoding from Pub/Sub.
3. **Enable Pub/Sub** topic for `video-uploaded` and configure the transcoder subscription.
4. **Configure Firestore rules** for secure data access.
5. (Optional) **Add Cloud Scheduler** and Pub/Sub retry policies for resilience.

## 📈 Impact & Performance

- The event-driven pipeline significantly reduces latency and supports high-concurrency uploads.
- Using Firestore & Cloud Storage improves metadata consistency and user experience.
- Deploying on Cloud Run enables automated scaling and ensures maintainable production-grade infrastructure.

## 🤝 Contributing

1. Fork this repo
2. Create a feature branch (`git checkout -b feature/xyz`)
3. Make your changes (with tests)
4. Submit a PR against `main`
5. Await review and merge

Please adhere to the project's code style and write clear, concise commits.

## 🧾 License

This project is open‑source under the **MIT License**. See [LICENSE](./LICENSE) for details.

## 🕹️ Try It Yourself

Check out the [**live demo**](https://yt-web-client-543501541359.asia-south2.run.app/) and dive into the [GitHub repo](https://github.com/deepencoding/Youtube-Clone).

## 🙋‍♂️ Author

**@deepencoding** – passionate about real-time video processing and scalable web apps. Feel free to connect on \[Twitter/GitHub]!
