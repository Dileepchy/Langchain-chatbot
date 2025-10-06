# 🤖 Simple LangChain Chatbot with Groq (Streamlit App)

## 📝 Description
A beginner-friendly chatbot app built with **Streamlit** (shiny web interface ✨), **LangChain** (LLM workflow magic 🧙), and **Groq** (ultra-fast inference ⚡). This app shows off core LangChain concepts (prompt templates, chains, streaming responses) while using Groq's speed for near-instant chat replies!

## ✨ Features
- Choose between 2 popular open-source models 🧠:
  - `llama3-8b-8192` (Meta Llama 3 8B)
  - `gemma2-9b-it` (Google Gemma 2 9B)
- Real-time **streaming responses** (watch the bot "type" as it generates text 🖊️)
- Session-persistent chat history 📜
- One-click "Clear Chat" to reset the conversation 🧹
- Pre-built example prompts to get started quickly 💡
- Clean, intuitive web interface 🖥️

## 📋 Prerequisites
1. **Python 3.8+** 🐍: Install a recent Python version (check with `python --version`).
2. **Groq API Key** 🔑: Get a free key from the [Groq Console](https://console.groq.com/) (no credit card needed for the free tier! 🎉)

## 🚀 Installation & Setup

### 1. Clone the Repository 📂
```bash
git clone https://github.com/Dileepchy/Langchain-chatbot.git
cd Langchain-chatbot
```

*(If this is a single-file app: save the code as `app.py` in a new empty folder!)*

### 2. Install Dependencies 📦
Create a `requirements.txt` file in your folder with this content:
```txt
streamlit
langchain
langchain-groq
```

Install the dependencies via using uv:
```bash
uv add -r requirements.txt
```

### 3. Run the App ▶️
```bash
streamlit run app.py
```

The app will open automatically in your default browser (usually at `http://localhost:8501` 🌐)!

## 📖 How to Use
1. **Enter Your Groq API Key** 🔑:
   - Open the sidebar (left side of the app ↔️).
   - Paste your Groq API key into the "GROQ API Key" field (it's hidden/password-protected—*only stored for your current session*, not saved permanently! 🔒).

2. **Select a Model** 🧠:
   - Choose either `llama3-8b-8192` or `gemma2-9b-it` from the "Model" dropdown.

3. **Start Chatting!** 💬
   - Type a question/prompt in the chat input at the bottom and press Enter.
   - The chatbot will stream its response in real time (watch the text appear! 🖊️).

4. **Manage the Conversation** 🧹:
   - Use the "Clear Chat" button in the sidebar to reset your chat history.
   - Try the pre-made prompts under the "💡 Try these examples" section for quick testing!

## 🧩 Code Overview
Quick breakdown of the core logic:
1. **Streamlit Setup** ✨: Configures the page (title, icon) and sidebar for settings/API key input.
2. **Chat History** 📜: Uses Streamlit's `session_state` to store user/assistant messages (persists only for your active app session).
3. **LangChain + Groq Integration** ⚡:
   - `ChatGroq`: LangChain's wrapper for Groq's API (initializes the LLM with your key, model choice, and temperature 🌡️).
   - `ChatPromptTemplate`: Defines a system message (sets the assistant's "personality" 🤖) and a placeholder for user input.
   - **Chain**: Combines prompt → LLM → `StrOutputParser` (simplifies LLM output to plain text 📄) into one smooth workflow.
4. **Streaming** 🖥️: Uses `chain.stream()` to show the assistant's response *as it generates* (no waiting for the full reply! ⏳).

## 📌 Notes
- **API Key Security** 🔒: Your Groq API key is **not saved** by the app—you’ll need to re-enter it if you close/restart the app.
- **Groq Free Tier** 🎉: Groq's free tier has generous limits for testing! Check [Groq's Pricing](https://groq.com/pricing/) for details.
- **Context Windows** 📏: Both models use an 8192-token context window (check Groq's docs for model updates! 🆕).

## 🛠️ Built With
- [Streamlit](https://streamlit.io/) – For the no-code/low-code web interface ✨
- [LangChain](https://www.langchain.com/) – For orchestrating the LLM workflow 🧙
- [Groq](https://groq.com/) – For ultra-fast LLM inference via their LPUs ⚡
