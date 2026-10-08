# 🎬 Kids Video AI Pipeline

> An end-to-end autonomous AI agent that generates educational children's cartoon videos from a simple topic, using self-hosted n8n, GigaChat, and Magic Hour.

![n8n](https://img.shields.io/badge/n8n-Self--Hosted-orange)
![Docker](https://img.shields.io/badge/Docker-Container-blue)
![AI Agents](https://img.shields.io/badge/AI-Agents-purple)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📖 Overview

This project is a fully automated **AI Agent pipeline** that:

1. Accepts a simple topic (e.g., "colors", "numbers", "animals").
2. Generates a complete Arabic cartoon script with 6 scenes using **GigaChat**.
3. Converts each scene into an English video generation prompt.
4. Generates a 5-second animated video using **Magic Hour API**.
5. Returns the final video URL, ready for YouTube.

The entire system runs **self-hosted** on Docker, with no dependency on external cloud platforms.

---

## 🏗️ Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Chat Input  │────▶│   AI Agent   │────▶│    Tool:     │
│  (n8n Chat)  │     │     (n8n)    │     │   Script     │
└──────────────┘     └──────────────┘     │  Generator   │
                                          └──────────────┘
                                                 │
                                                 ▼
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Final      │◀────│  Magic Hour  │◀────│    Tool:     │
│  Video URL   │     │   Video API  │     │   Video      │
└──────────────┘     └──────────────┘     │  Generator   │
                                          └──────────────┘
```

---

## ✨ Key Features

- ✅ **Real AI Agent** with autonomous tool selection
- ✅ **OAuth 2.0 auto-refresh** for GigaChat (30-min token rotation)
- ✅ **Sub-workflow architecture** for modular tools
- ✅ **Polling loops** for asynchronous video generation
- ✅ **Custom SSL certificates** handling inside Docker
- ✅ **Retry logic** for API rate limits
- ✅ **100% self-hosted** – data never leaves your machine

---

## 🛠️ Tech Stack

| Layer | Technology |
|:---|:---|
| **Orchestration** | n8n (self-hosted) |
| **Containerization** | Docker |
| **AI Agent** | n8n AI Agent Node |
| **LLM** | GigaChat 2 Pro (Sber) |
| **Video Generation** | Magic Hour API (LTX 2.5) |
| **Authentication** | OAuth 2.0 |
| **Languages** | JavaScript, JSON |

---

## 🚀 Quick Start

### Prerequisites

- Docker Desktop installed
- GigaChat API access ([developers.sber.ru](https://developers.sber.ru))
- Magic Hour API key ([magichour.ai](https://magichour.ai))

### Installation

**1. Clone the repository:**

```bash
git clone https://github.com/YOUR_USERNAME/kids-video-ai-pipeline.git
cd kids-video-ai-pipeline
```

**2. Start n8n with Docker:**

```bash
docker run -it --rm --name n8n -p 8081:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

**3. Import workflows:**

- Open n8n at `http://localhost:8081`
- Go to **Workflows** → **Import from File**
- Import all JSON files from the `workflows/` folder

**4. Configure credentials in n8n:**

- Add your **GigaChat Authorization Key**
- Add your **Magic Hour API Key**

**5. Test the pipeline:**

Open the AI Agent workflow and send:

```
أنشئ حلقة عن الألوان
```

Watch the magic happen! ✨

---

## 📁 Project Structure

```
kids-video-ai-pipeline/
│
├── README.md                    # This file
├── LICENSE                      # MIT License
├── .gitignore                   # Git ignore rules
│
├── workflows/                   # n8n workflow JSON files
│   ├── ai-agent-main.json
│   ├── script-generator.json
│   └── video-generator.json
│
├── docs/                        # Documentation
│   ├── setup-guide.md
│   └── architecture.md
│
└── screenshots/                 # Screenshots and demos
    ├── workflow.png
    └── video-demo.mp4
```

---

## 🎓 What I Learned

Through this project, I gained practical experience in:

- Building **AI agents** with autonomous tool selection
- Managing **OAuth 2.0** token lifecycles in a production pipeline
- Handling **asynchronous API patterns** (queue + polling loops)
- **Docker** networking and SSL certificate management
- **Prompt engineering** for bilingual output (Arabic + English)
- **Sub-workflow architecture** for modular automation

---

## 🗺️ Roadmap

- [x] AI Agent with Chat Trigger
- [x] Script Generator Tool (GigaChat)
- [x] Video Generator Tool (Magic Hour)
- [ ] Text-to-Speech integration (TTS)
- [ ] Automatic YouTube upload
- [ ] Agent memory for multi-episode continuity

---

## 👤 Author

**Rawad Amir Skef**

- GitHub: [@YOUR_USERNAME](https://github.com/YOUR_USERNAME)
- LinkedIn: [Your Profile](https://linkedin.com/in/YOUR_PROFILE)
- Email: rskef@mail.ru
- Telegram: [@Rawad138](https://t.me/Rawad138)

---

## 📄 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

---

⭐ If you found this project useful, please give it a star!
