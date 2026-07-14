# 🤖 AI Chatbot — Local & Cloud

> Build and run your own AI chatbot using two approaches: **OpenAI's cloud API** or a **fully local open-source LLM** — all wrapped in a clean, ChatGPT-style web UI.

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Streamlit](https://img.shields.io/badge/streamlit-%23FF4B4B.svg?style=for-the-badge&logo=streamlit&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![HuggingFace](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Transformers-orange?style=for-the-badge)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)

---

## 📖 Overview

This project is an educational Jupyter Notebook (`Chatbot.ipynb`) that walks you through building a fully functional AI chatbot web application. It demonstrates two different backend strategies:

| Approach | Model | Use Case |
|---|---|---|
| ☁️ **Cloud (OpenAI API)** | `gpt-4o-mini` | Fast, reliable, requires API key & credits |
| 💻 **Local (Hugging Face)** | `microsoft/Phi-4-mini-instruct` | Free, private, runs on your own hardware (GPU recommended) |

Both produce a **ChatGPT-style interactive web UI** via [Streamlit](https://streamlit.io), and can be exposed to the internet via [localtunnel](https://github.com/localtunnel/localtunnel) — making them easy to demo from Google Colab or any remote server.

---

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| **Language** | Python 3.8+ |
| **Web UI** | Streamlit |
| **Cloud AI** | OpenAI API (`gpt-4o-mini`) |
| **Local AI** | Hugging Face Transformers + PyTorch |
| **Local Model** | Microsoft Phi-4-mini-instruct |
| **Env Management** | python-dotenv |
| **Tunnelling** | localtunnel (Node.js / npm) |
| **Notebook** | Jupyter / Google Colab |

---

## ✨ Features

- 💬 **ChatGPT-style UI** — full conversation history, chat bubbles, live responses
- 🔀 **Dual backends** — swap between cloud OpenAI and fully local Hugging Face model
- 🔐 **Secure API key handling** — keys loaded from `.env`, never hardcoded
- 🌐 **Public URL via localtunnel** — share your running chatbot with anyone instantly
- 🧠 **Persistent chat history** — maintains conversation context across messages
- ⚡ **GPU acceleration** — automatically uses CUDA if available (for local model)

---

## 📋 Prerequisites

- **Python** 3.8 or higher
- **Node.js** (for localtunnel)
- A **GPU** is highly recommended for the local Hugging Face model (CPU will be very slow)
- An **OpenAI API key** (only for the OpenAI version)

---

## 🚀 Setup & Usage

### 1. Clone the Repository

```bash
git clone https://github.com/P2898/Chatbot.git
cd Chatbot
```

---

### ☁️ Option A — OpenAI Cloud Chatbot

#### Step 1: Install dependencies

```bash
pip install openai python-dotenv streamlit
npm install -g localtunnel
```

#### Step 2: Configure your API key

Create a `.env` file in the project root:

```bash
# .env
OPENAI_API_KEY=your_openai_api_key_here
```

> 🔒 **Never share your `.env` file or commit it to GitHub.** It is already listed in `.gitignore`.

#### Step 3: Run the notebook to generate `app_openai.py`

Open `Chatbot.ipynb` in Jupyter or Google Colab and run the cells in the **OpenAI** section. This will write the `app_openai.py` file automatically.

#### Step 4: Launch the app

```bash
streamlit run app_openai.py
```

---

### 💻 Option B — Local Hugging Face Chatbot

#### Step 1: Install dependencies

```bash
pip install transformers torch streamlit
npm install -g localtunnel
```

#### Step 2: Run the notebook to generate `app_huggingface.py`

Open `Chatbot.ipynb` and run the cells in the **Hugging Face** section. This will download the `microsoft/Phi-4-mini-instruct` model and write `app_huggingface.py`.

> ⚠️ The model download (~4GB) may take some time on first run.

#### Step 3: Launch the app

```bash
streamlit run app_huggingface.py
```

---

### 🌐 Accessing via Public URL (localtunnel)

If running on Google Colab or a remote server, use this to get a public URL:

```bash
# Find your public IP (you'll need this to pass localtunnel's password screen)
curl ipv4.icanhazip.com

# In a separate terminal, start the tunnel
npx localtunnel --port 8501
```

You'll receive a URL like `https://some-name.loca.lt`. Open it in your browser and enter the IP from the first command when prompted.

> ⚠️ **Stop the Streamlit cell when done** to avoid keeping the server running unnecessarily.

---

## 📁 Project Structure

```
Chatbot/
├── Chatbot.ipynb       # Main notebook — generates both apps and runs them
├── .env.example        # Template for environment variables (copy to .env)
├── .gitignore          # Prevents sensitive files from being committed
└── README.md           # This file
```

> `app_openai.py` and `app_huggingface.py` are **generated** by running the notebook cells — they are not committed to the repo.

---

## 🔐 Security Notes

- API keys must **always** be stored in a `.env` file, never hardcoded in code
- The `.env` file is git-ignored — use `.env.example` as a reference template
- The `HF_TOKEN` (Hugging Face token) is optional for public models, but can be set as a Colab secret if needed

---

