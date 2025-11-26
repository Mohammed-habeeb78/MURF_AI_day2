# 💼 Day 5: AI Voice Agent Challenge - Simple FAQ SDR + Lead Capture Agent

This project implements a sophisticated AI Sales Development Representative (SDR) using the LiveKit Agent SDK. The agent, named **'Sarah,'** is designed to handle frequently asked questions (FAQ) about the fictional "Abhishek Store's" offerings while simultaneously engaging in a natural conversation to qualify and capture essential lead information.

This solution was built as part of the **10 Days of Voice Agents** challenge.

## ✨ Features

* **FAQ Retrieval:** Loads product/service information from a `store_faq.json` file and uses it as a knowledge base for answering user questions.
* **Lead Qualification:** The agent is instructed to naturally gather key lead details (Name, Email, Use Case, etc.) during the conversation.
* **Function Calling (Tools):**
    * `update_lead_profile`: Used immediately to capture and update lead data as the user provides it.
    * `submit_lead_and_end`: Called when the user concludes the conversation, serializing the final lead profile into a `leads_db.json` file.
* **Fast TTS:** Utilizes the Murf Falcon TTS API (`murf.TTS`) for fast, human-like voice responses, enhancing the real-time conversation experience.
* **Tech Stack:** LiveKit Agents SDK, Google Gemini 2.5 Flash (LLM), Deepgram (STT), Murf (TTS), Silero (VAD).

## 🚀 How to Run

### Prerequisites

1.  **Python:** Ensure you have Python 3.9+ installed.
2.  **LiveKit Server:** A running LiveKit server is required.
3.  **API Keys:** Set up your environment variables for all required services (LiveKit, Murf, Deepgram, Google/Gemini).

### Setup Steps

1.  **Clone the Repository (or setup the files):**
    * `agent.py` (your provided code)
    * `store_faq.json` (will be generated if missing)
    * `.env.local` (for API keys)

2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    # requirements.txt should contain: livekit-agents, python-dotenv, pydantic, livekit-plugins-murf, livekit-plugins-deepgram, livekit-plugins-google, livekit-plugins-silero, livekit-plugins-noise-cancellation
    ```

3.  **Configure Environment Variables**

    Create a file named `.env.local` and populate it with your keys:

    ```env
    LIVEKIT_URL="ws://localhost:7880"
    LIVEKIT_API_KEY="YOUR_API_KEY"
    LIVEKIT_API_SECRET="YOUR_API_SECRET"
    
    # Text-to-Speech (TTS)
    MURF_API_KEY="YOUR_MURF_API_KEY"
    
    # Speech-to-Text (STT)
    DEEPGRAM_API_KEY="YOUR_DEEPGRAM_API_KEY"
    
    # Large Language Model (LLM)
    GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
    ```

4.  **Start the Agent:**

    ```bash
    python agent.py
    ```

## 🧠 Agent Behavior & Flow

1.  **Initial Greeting:** The agent "Sarah" will welcome the user.
2.  **FAQ Handling:** The user asks a question (e.g., "How much is the course?"). Sarah answers using the `STORE_FAQ_TEXT`.
3.  **Lead Capture:** After answering, Sarah transitions into a qualification question (e.g., "What are you trying to build?").
4.  **Tool Use:** When the user replies with their **name** or **email**, the LLM intelligently calls the `update_lead_profile` tool to save the data immediately.
5.  **Closing:** When the user says "thanks, that's all," the LLM calls `submit_lead_and_end`.
6.  **Database:** The final lead profile is appended to `leads_db.json`.

---
