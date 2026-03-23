# 💬 ConvoPro-GenAI

A production-ready **Conversational AI** backend built with a clean, modular architecture — featuring an LLM factory pattern, service layer, and persistent conversation memory.

> **Purpose:** Build a scalable conversational AI system that can swap LLM providers, manage conversation history, and handle multiple services — all from a single clean codebase.

---

## 🏗️ Project Architecture

```
ConvoPro-GenAI/
├── config/              ← App configuration & environment settings
├── db/                  ← Database models & conversation persistence
├── llm_factory/         ← LLM provider abstraction (swap models easily)
├── services/            ← Business logic & conversation services
├── main.py              ← Application entry point
├── env_templates.txt    ← Environment variable templates
└── requirements.txt
```

---

## ⚙️ How It Works

```
User sends message
        ↓
main.py → routes to services/
        ↓
services/ → fetches conversation history from db/
        ↓
llm_factory/ → selects LLM provider (Groq / OpenAI / Gemini)
        ↓
LLM generates response with full context
        ↓
Response saved to db/ → returned to user
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Language** | Python 3.11 |
| **LLM Providers** | Groq · OpenAI · Gemini (via factory pattern) |
| **Database** | SQLite / PostgreSQL |
| **Configuration** | python-dotenv |
| **Architecture** | Factory Pattern · Service Layer · Repository Pattern |

---

## 📂 Module Breakdown

### `llm_factory/`
The core innovation of this project — an LLM abstraction layer.
- Defines a base LLM interface
- Implements providers: Groq, OpenAI, Gemini
- Swap any LLM with zero changes to business logic
- Handles API keys, model names, and parameters per provider

```python
# Example usage
llm = LLMFactory.create("groq")       # uses Groq
llm = LLMFactory.create("openai")     # swap to OpenAI — nothing else changes
response = llm.complete(prompt)
```

### `services/`
Business logic layer — keeps LLM calls separate from app logic.
- Conversation management service
- Message history handling
- Context window management
- Response formatting

### `db/`
Persistent conversation storage.
- Conversation models
- Message history CRUD
- Session management
- Query helpers

### `config/`
Centralized configuration management.
- Environment variable loading
- Model configuration
- App-wide settings

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11
- At least one LLM API key (Groq is free) → https://console.groq.com

### Installation

```bash
# Clone the repo
git clone https://github.com/ayushRajak19/ConvoPro-GenAI.git
cd ConvoPro-GenAI

# Create virtual environment
py -3.11 -m venv .venv
.venv\Scripts\activate      # Windows
source .venv/bin/activate   # Mac/Linux

# Install dependencies
pip install uv
uv pip install -r requirements.txt
```

### Environment Setup

Copy the template and fill in your keys:
```bash
copy env_templates.txt .env    # Windows
cp env_templates.txt .env      # Mac/Linux
```

Edit `.env`:
```env
GROQ_API_KEY=your_groq_key_here
OPENAI_API_KEY=your_openai_key_here   # optional
LLM_PROVIDER=groq                      # groq | openai | gemini
DATABASE_URL=sqlite:///convopro.db
```

### Run

```bash
python main.py
```

---

## 💡 Key Concepts Implemented

```
Factory Pattern      → Create any LLM without changing calling code
Service Layer        → Business logic separated from LLM and DB
Repository Pattern   → Database access abstracted from services
Conversation Memory  → Full history passed with every LLM call
Context Management   → Trim history when context window fills up
Provider Agnostic    → Works with Groq, OpenAI, Gemini interchangeably
```

---

## 🎯 What I Learned Building This

- How to implement the Factory design pattern for LLM providers
- Why separating services from LLM calls makes code maintainable
- How conversation memory works and why context windows matter
- How to persist and retrieve chat history from a database
- How to manage environment configs cleanly across environments

---

## 🔗 Related Projects

| Project | Description |
|---|---|
| [Repo Copilot](https://github.com/ayushRajak19/repos-copilot-cb) | Ask anything about any GitHub codebase using RAG |
| [Astra RAG Learn](https://github.com/ayushRajak19/astra-rag-learn) | Full-stack RAG application with agents |
| [AI Resume Screener](#) | Match resumes to jobs using GenAI *(coming soon)* |

---

## 🚀 Tech Badges

![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat&logo=python)
![Groq](https://img.shields.io/badge/Groq-LLM-orange?style=flat)
![OpenAI](https://img.shields.io/badge/OpenAI-Compatible-green?style=flat&logo=openai)
![SQLite](https://img.shields.io/badge/SQLite-Database-blue?style=flat&logo=sqlite)
![Architecture](https://img.shields.io/badge/Pattern-Factory%20%2B%20Service-purple?style=flat)

---

## 👨‍💻 Author

**Ayush Rajak** — Aspiring GenAI Engineer

Building real AI products to land my first job in the GenAI space.

[![GitHub](https://img.shields.io/badge/GitHub-ayushRajak19-black?style=flat&logo=github)](https://github.com/ayushRajak19)

---

⭐ *Star this repo if it helped you understand conversational AI architecture!*
