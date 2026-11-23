# ✈️ Multi-Model AI Agent & Airline AI Assistant

[![Python Version](https://img.shields.io/badge/python-3.10%20%7C%203.11-blue.svg)](https://www.python.org/)
[![Gradio](https://img.shields.io/badge/Gradio-UI-orange.svg)](https://gradio.app/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o%20%7C%20DALL--E%20%7C%20TTS-green.svg)](https://openai.com/)
[![SQLite](https://img.shields.io/badge/Database-SQLite3-lightgrey.svg)](https://www.sqlite.org/)
[![Ollama](https://img.shields.io/badge/Local%20LLM-Ollama-purple.svg)](https://ollama.ai/)

A practical AI project exploring multiple language models, tool integrations, and interactive interfaces, culminating in an end-to-end **Multimodal Airline AI Assistant**.

---

## 📌 Overview

This project brings together core modern AI capabilities across dedicated notebooks:

* **`ai_models.ipynb`**: Experimenting with different frontier and open LLMs (OpenAI, Google Gemini, Groq, Grok).
* **`ollama_test.ipynb`**: Testing local, privacy-focused open-source models offline using Ollama.
* **`tool_calling.ipynb`**: Integrating external tools and function calling with AI models to perform real-world actions.
* **`gradio.ipynb`**: Designing interactive, user-friendly web interfaces for AI applications.
* **`Airline_AI_Assistant.ipynb`**: The flagship end-to-end multimodal project combining all the techniques above into a functional travel assistant.

---

## ✈️ Airline AI Assistant

The **Airline AI Assistant** is an intelligent, multimodal travel planning agent designed to help users search and plan trips through a conversational web interface.

### How It Works Behind the Scenes

1. **Trip Planning Conversation:**  
   The user chats naturally with the assistant (e.g., *"I want to fly from Berlin to Paris"*).

2. **Private Database Retrieval (Tool Calling):**  
   Behind the scenes, the AI model identifies the departure and destination cities and calls a custom database tool. It queries a private SQLite database (`airline_database.db`) to retrieve available flight routes, ticket prices, and airline operators.

3. **Destination Image Generation:**  
   For any queried destination, an AI image generation model creates a vibrant, customized artwork representing the destination city and its landmarks.

4. **Voice Audio Delivery:**  
   The assistant's response is converted into natural spoken audio using a Text-to-Speech (TTS) model with automatic playback.

5. **Unified Gradio Web Interface:**  
   The user receives the full multimodal experience in one interactive screen: the conversational chat history, the generated destination visual, and the voice response.

---

## 🏛️ Architecture Flow

```mermaid
flowchart TD
    User([User / Traveler]) -->|Asks travel question| UI[Gradio Web Interface]
    
    UI --> LLM[AI Model / Assistant]
    
    subgraph Actions [Behind the Scenes]
        LLM -->|Tool Calling| DB[(Private Airline Database)]
        DB -->|Returns flight price & airline| LLM
        
        LLM -->|Generates prompt| ImageGen[AI Image Generator]
        LLM -->|Converts response to voice| TTS[Text-to-Speech Engine]
    end
    
    LLM -->|Text Response| UI
    ImageGen -->|Destination Artwork| UI
    TTS -->|Spoken Audio| UI
```

---

## ⚙️ Quick Setup

1. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure API Keys:**
   Copy `.env.example` to `.env` and add your keys:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   GOOGLE_API_KEY=your_google_api_key_here
   GROQ_API_KEY=your_groq_api_key_here
   ```

3. **Run:**
   Open [**`Airline_AI_Assistant.ipynb`**](Airline_AI_Assistant.ipynb) in your notebook editor and run the cells to launch the Gradio web assistant.
