# 🗣️ Active Recall Coach: Teach-the-Tutor Voice Agent (Day 4 Challenge)

A voice-powered AI coach built using LiveKit Agents and Murf Falcon TTS, designed to improve learning retention through the **Active Recall** method.



## 💡 Concept

This agent implements the **"Teach-the-Tutor"** and **"Active Recall"** learning strategies.

1.  **Teach-the-Tutor:** The user explains a concept (e.g., "Photosynthesis") to the AI tutor.
2.  **Active Recall Coach:** The AI analyzes the explanation, provides constructive feedback, and generates targeted, high-value follow-up questions to force the user to *retrieve* information rather than just *recognize* it.

## ✨ Features

* **Conversational Interface:** Utilizes the LiveKit Agents SDK for seamless, low-latency voice interaction.
* **Fast TTS:** Leverages the **Murf Falcon API** for incredibly fast, natural-sounding Text-to-Speech.
* **LLM Analysis:** Uses a powerful Language Model (e.g., GPT-4) to analyze the user's spoken input for correctness, completeness, and clarity.
* **Context Preservation:** Implements LiveKit Handoff (or similar state management) to ensure the agent remembers the user's prior explanation when delivering feedback and follow-up questions.

## 🛠️ Tech Stack

* **Voice Framework:** LiveKit Agents SDK (Python)
* **Text-to-Speech (TTS):** **Murf Falcon API** (The fastest TTS!)
* **Speech-to-Text (STT):** LiveKit STT
* **Core Logic/Analysis (LLM):** OpenAI/Anthropic/etc.
* **Hosting:** LiveKit Cloud / Self-Hosted Server

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/Active-Recall-Coach-Voice-Agent.git](https://github.com/your-username/Active-Recall-Coach-Voice-Agent.git)
    cd Active-Recall-Coach-Voice-Agent
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Set Environment Variables:**
    Create a `.env` file with your credentials:
    ```
    LIVEKIT_URL="ws://your-livekit-url"
    LIVEKIT_API_KEY="your-key"
    LIVEKIT_API_SECRET="your-secret"
    MURF_FALCON_API_KEY="your-murf-key"
    OPENAI_API_KEY="your-openai-key"
    ```
4.  **Launch the Agent:**
    ```bash
    python active_recall_coach.py
    ```
    *(Instructions on how to connect a client (like the LiveKit playground) would follow here.)*

## 🎬 Video Demo

[Link to your YouTube/LinkedIn Video Demo]
