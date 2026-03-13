# 🤖 RAG Pipeline & Chatbot — Built with n8n

A fully automated **Retrieval-Augmented Generation (RAG)** pipeline and AI chatbot built using **n8n**, **OpenAI**, **Pinecone**, and **Google Drive**. This project automatically ingests documents from Google Drive, embeds them into a vector store, and enables an AI chatbot to answer questions based on the uploaded documents.

---

## ✨ Features

- 📂 **Auto document ingestion** — triggers when a new file is added to Google Drive
- 🧠 **OpenAI Embeddings** — converts documents into vector embeddings
- 📦 **Pinecone Vector Store** — stores and retrieves embeddings efficiently
- 💬 **AI Chatbot** — answers questions based on the ingested documents
- 🧵 **Conversation Memory** — remembers context within a chat session
- ⚡ **Fully automated** — no manual steps required after setup

---

## 🏗️ Architecture

The project consists of two workflows:

### Workflow 1 — Document Ingestion Pipeline
```
Google Drive Trigger
      ↓
Download File
      ↓
Default Data Loader
      ↓
OpenAI Embeddings
      ↓
Pinecone Vector Store
```

### Workflow 2 — AI Chatbot
```
Chat Message Received
        ↓
     AI Agent
    ↙    ↓    ↘
Model  Memory  Tool
  ↓      ↓       ↓
OpenAI  Simple  Pinecone
Chat    Memory  Vector Store 2
Model            ↓
             OpenAI Embeddings 2
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation platform |
| [OpenAI](https://openai.com) | Chat model + embeddings |
| [Pinecone](https://pinecone.io) | Vector database |
| [Google Drive](https://drive.google.com) | Document source & trigger |

---

## 🚀 Getting Started

### Prerequisites

- [n8n](https://n8n.io) account (cloud or self-hosted)
- [OpenAI API key](https://platform.openai.com)
- [Pinecone API key](https://www.pinecone.io)
- Google Drive account

### Installation

1. **Clone this repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/n8n-rag-pipeline-chatbot.git
   cd n8n-rag-pipeline-chatbot
   ```

2. **Import workflows into n8n**
   - Open your n8n instance
   - Go to **Workflows** → **Import from file**
   - Import `ingestion-pipeline.json`
   - Import `chatbot-workflow.json`

3. **Set up credentials in n8n**
   - Add your **OpenAI API key** under Credentials
   - Add your **Pinecone API key** under Credentials
   - Connect your **Google Drive** account via OAuth

4. **Configure Pinecone**
   - Create a Pinecone index with dimension **1536** (for OpenAI `text-embedding-ada-002`)
   - Update the Pinecone nodes in both workflows with your index name

5. **Activate both workflows**
   - Toggle the workflows to **Active** in n8n

---

## 📖 How to Use

1. **Upload a document** (PDF, DOCX, TXT) to the connected Google Drive folder
2. The ingestion pipeline **automatically triggers**, embeds the document, and stores it in Pinecone
3. Open the **chat interface** in n8n
4. **Ask questions** about the uploaded document — the AI will respond with relevant answers!
---

## 🔮 Future Improvements

- [ ] Support for more file types (CSV, HTML, etc.)
- [ ] Add a web-based frontend for the chatbot
- [ ] Support multiple knowledge bases / Pinecone namespaces
- [ ] Add Slack or WhatsApp integration for the chatbot
- [ ] Implement user authentication for the chat interface

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Fork the repo
- Create a new branch (`git checkout -b feature/your-feature`)
- Commit your changes
- Open a Pull Request

---

## 👨‍💻 About

Built by **Rubab Batool** as part of learning n8n and AI automation.

⭐ **If you found this useful, please give it a star!**
