# 📄 Chat With PDF (Local AI)

Chat With PDF is a full-stack application that allows users to upload PDF files and interact with them using **local AI models**.  
The project uses **Ollama** for local LLM inference, **Qdrant** as the vector database, **Valkey** for caching/queueing, and **Clerk** for authentication.

![Demo Preview](https://github.com/tarunkumar-sys/chat_with_pdf/blob/main/public/demo/demo.png)

---

## ✨ Features

- 🔐 Authentication with **Clerk**
- 📄 Upload and chat with PDF documents
- 🤖 Local AI using **Ollama**
- 🧠 Vector search powered by **Qdrant**
- ⚡ Fast caching with **Valkey**
- 🐳 Docker-based infrastructure
- 🌐 Full-stack Next.js app

---

## 🧱 Tech Stack

- **Frontend / Backend:** Next.js (App Router)
- **Authentication:** Clerk
- **LLM Runtime:** Ollama (local)
- **Vector Database:** Qdrant
- **Cache / Queue:** Valkey
- **Package Manager:** npm
- **Containerization:** Docker

---

## 📦 Prerequisites

Make sure you have the following installed:

- Node.js `>=18`
- Docker & Docker Compose
- Ollama
- npm

---

## 🧠 Install Ollama (Local AI)

Install Ollama:

```bash
curl -fsSL https://ollama.com/install.sh | sh
````

Pull a model (example):

```bash
ollama pull llama3
```

Start Ollama (usually auto-starts):

```bash
ollama serve
```

Ollama will be available at:

```
http://localhost:11434
```

---

## 🐳 Run Required Services (Docker)

### 1️⃣ Qdrant (Vector Database)

```bash
docker run -d \
  --name qdrant \
  -p 6333:6333 \
  -p 6334:6334 \
  qdrant/qdrant
```

### 2️⃣ Valkey (Cache)

```bash
docker run -d \
  --name valkey \
  -p 6379:6379 \
  valkey/valkey
```

Verify containers:

```bash
docker ps
```

Expected output (example):

```bash
qdrant   0.0.0.0:6333-6334->6333-6334/tcp
valkey   0.0.0.0:6379->6379/tcp
```

---

## 🔐 Clerk Authentication Setup

1. Create an account at **[https://clerk.com](https://clerk.com)**
2. Create a new application
3. Copy your keys

Create a `.env.local` file in the project root:

```env
# Clerk
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_xxxxxxxxx
CLERK_SECRET_KEY=sk_test_xxxxxxxxx

# App
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Qdrant
QDRANT_URL=http://localhost:6333

# Valkey
VALKEY_URL=redis://localhost:6379

# Ollama
OLLAMA_BASE_URL=http://localhost:11434
OLLAMA_MODEL=llama3
```

---

## 📥 Installation

Clone the repository:

```bash
git clone https://github.com/tarunkumar-sys/chat_with_pdf.git
cd chat_with_pdf
```

Install dependencies:

```bash
npm install
```

---

## 🚀 Running the App

Start the full development environment:

```bash
npm run dev:full
```

The application will be available at:

```
http://localhost:3000
```

---

## 🧪 Troubleshooting

### Containers stopped?

Restart them:

```bash
docker start qdrant valkey
```

### Ollama not responding?

Check status:

```bash
ollama list
```

Restart:

```bash
ollama serve
```

### Port conflicts?

Ensure these ports are free:

* `3000` – App
* `6333` – Qdrant
* `6379` – Valkey
* `11434` – Ollama

---

## 📄 License

MIT License

