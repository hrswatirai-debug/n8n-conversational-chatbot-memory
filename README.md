# 🤖 Conversational Chatbot with Session Memory — n8n + OpenAI

![n8n](https://img.shields.io/badge/Built%20with-n8n-orange?style=flat-square)
![OpenAI](https://img.shields.io/badge/Model-GPT--4o--mini-412991?style=flat-square&logo=openai)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

> A production-ready conversational AI chatbot built using n8n's visual workflow 
> automation platform, powered by OpenAI GPT-4o-mini with persistent session memory.

---

## 📌 Overview

This workflow implements a fully functional AI chatbot with:
- **Public chat interface** accessible via webhook URL
- **Session-based memory** retaining the last 10 messages per conversation
- **GPT-4o-mini** as the language model for fast, cost-efficient responses
- **No-code/low-code** architecture built entirely in n8n

Built as part of the **Black Elephant AI Learning Ecosystem** — an applied AI 
initiative focused on real-world Generative AI and Agentic AI deployments.

---

## 🏗️ Workflow Architecture
[Chat Trigger] ──► [AI Agent] ──► [Chat Response]
▲
┌────────┴─────────┐
[OpenAI GPT-4o-mini]   [Simple Memory]
(last 10 messages)
---

## 🧩 Nodes Used

| Node | Type | Purpose |
|---|---|---|
| When chat message received | Chat Trigger | Public entry point, creates chat UI |
| AI Agent | Langchain Agent | Orchestrates LLM + memory |
| OpenAI Chat Model | LLM | GPT-4o-mini for response generation |
| Simple Memory | Window Buffer Memory | Maintains session context (10 messages) |
| Chat | Response Node | Returns AI output to user |

---

## ⚙️ Tech Stack

- **Workflow Engine:** [n8n](https://n8n.io) (self-hosted via Docker)
- **LLM:** OpenAI GPT-4o-mini
- **Memory:** n8n Window Buffer Memory (session-scoped)
- **Deployment:** Docker (local), portable to any n8n cloud instance
- **Interface:** n8n built-in public chat UI

---

## 🚀 Getting Started

### Prerequisites
- Docker installed and running
- n8n running locally or on a server
- OpenAI API key

### 1. Start n8n via Docker
```bash
docker run -d --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

### 2. Import the Workflow
1. Open **http://localhost:5678**
2. Click **"+"** → **New Workflow**
3. Click the **⋮ menu** (top right) → **Import from file**
4. Select `workflow.json` from this repo
5. Click **Save**

### 3. Configure OpenAI Credentials
1. Click the **OpenAI Chat Model** node
2. Under **Credential** → **Create new**
3. Paste your **OpenAI API Key**
4. Click **Save**

### 4. Activate & Test
1. Toggle the **Active** switch → ON ✅
2. Click the **Chat Trigger** node to get your public chat URL
3. Open the URL and start chatting!

---

## 🧠 How Session Memory Works

Each conversation is tracked using a unique `sessionId` passed by the Chat Trigger. 
The Window Buffer Memory node stores the last **10 message exchanges**, giving the 
bot contextual awareness within a session. Memory resets when a new session begins.

---

## 📁 Repository Structure

2.Conversation-Chatbot/
├── workflow.json        # n8n workflow export (importable)
├── assets/              # Screenshots and diagrams
│   └── workflow-screenshot.png
└── README.md            # This file
---

## 🔑 Environment Variables / Credentials Required

| Credential | Where to get it |
|---|---|
| OpenAI API Key | https://platform.openai.com/api-keys |

---

## 📌 Part of Black Elephant AI Learning Ecosystem

This project is **#7 in a series** of applied AI workflows built to demonstrate 
real-world Generative AI and Agentic AI use cases.

| # | Project | Stack |
|---|---|---|
| 1 | FastAPI + Ollama Text Generation | FastAPI, Docker, Ollama |
| 2 | Telegram with FAQ Bot |Telegram, OpenAI,  Zapier|
| 3 | AI Recruiting Agent | make.com, OpenAI, Google sheets, G-Drive, pdf.co, HTTP, Google Cloud |
| 4 | Industry-Grade Legal AI Agent | n8n, OpenAI, Telegram |
| 5 | VoiceFlow Trading AI Assistant | Voiceflow, Upstox |
| 6 | Simple_Chatbot | n8n, OpenAI, Docker |
| 7 | Conversational Chatbot with Memory | n8n, OpenAI, Docker |

---

## 👩‍💻 Author

**Swati Rai**  
AI Entrepreneur & Applied AI Consultant  
[LinkedIn](https://www.linkedin.com/in/swati-rai-049a8315) • [GitHub](https://github.com/hrswatirai-debug)

---

## 📄 License

This project is licensed under the MIT License.

## 📁 Repository Structure
