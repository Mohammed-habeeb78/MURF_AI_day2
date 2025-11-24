# 💚 AI Voice Agents Challenge | Day 3: Health & Wellness Voice Companion

This project is the submission for Day 3 of the AI Voice Agents Challenge, focusing on creating a supportive, high-performance voice companion for health and wellness tracking.

The agent is designed to handle sensitive and structured input, providing an empathetic, real-time voice interface for users to log their daily activities and vitals.

---

## 🚀 Key Features

* **Real-Time Conversational Interface:** Utilizes LiveKit Agents to facilitate a fluid, bi-directional voice conversation.
* **Supportive & Empathetic Tone:** The agent's voice (powered by Murf Falcon TTS) and conversational design aim to be encouraging and non-judgmental.
* **Structured Data Capture (Vitals & Activity):** The agent accurately extracts structured data from natural speech, such as:
    * **Vitals:** Blood pressure readings, heart rate, sleep duration, etc.
    * **Activity:** Workout type, duration, intensity, or steps taken.
* **Ultra-Low Latency TTS:** Integrated the **Murf Falcon TTS API** to achieve **sub-150ms Time-to-First-Audio (TTFA)**, crucial for maintaining an engaging and responsive companion experience.
* **Data Persistence & Logging:** Successfully captures and logs all reported health metrics into a structured format (e.g., CSV or JSON), ready for dashboard visualization or analysis.

---

## ⚙️ Technology Stack

| Component | Technology / Library | Purpose |
| :--- | :--- | :--- |
| **Agent Framework** | LiveKit Agents | Orchestration and handling of real-time voice sessions. |
| **Text-to-Speech (TTS)** | Murf Falcon API | High-speed, low-latency voice synthesis for an empathetic voice. |
| **ASR / NLP** | [Specify your ASR/NLP here, e.g., LLM/Custom Model] | Real-time speech transcription and extraction of structured health data. |
| **Language** | Python | Core agent logic, data processing, and persistence. |

---

## 🏃 Getting Started

### Prerequisites

* Python 3.8+
* A Murf AI API Key (for Falcon TTS)
* A LiveKit Server running or access to a LiveKit Cloud project.

### Installation

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/Mohammed-habeeb78/MURF_AI_day3.git](https://github.com/Mohammed-habeeb78/MURF_AI_day3.git)
    cd MURF_AI_day3
    ```

2.  **Set up the Virtual Environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### Configuration

Create a file named `.env` in the root directory and populate it with your API keys and LiveKit server details:

```env
# LiveKit Server Configuration
LIVEKIT_URL="wss://<your-livekit-server-url>"
LIVEKIT_API_KEY="<your-livekit-api-key>"
LIVEKIT_API_SECRET="<your-livekit-api-secret>"

# Murf Falcon TTS Configuration
MURF_API_KEY="<your-murf-falcon-api-key>"
Running the Agent
Start the agent using the following command:

Bash

python agent.py
The agent will connect to your LiveKit server and be ready to accept voice connections for health logging.

📁 Project Structure
MURF_AI_day3/
├── agent.py               # Main Companion Agent logic and LiveKit setup
├── requirements.txt       # Project dependencies
├── .env.example           # Template for environment variables
├── logs/                  # Directory for saving health/activity logs
│   └── health_metrics.json 
└── README.md              # This file
🤝 Contribution
Feel free to open issues or submit pull requests. Suggestions for new health metrics or logging features are welcome!

🙏 Credits
Challenge Organizers: Murf AI & LiveKit

Challenge Link: https://github.com/murf-ai/ten-days-of-voice-agents-2025/blob/main/challenges/Day%203%20Task.md
