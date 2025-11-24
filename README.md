# ☕ AI Voice Agents Challenge | Day 2: Coffee Shop Barista Agent

This project is the submission for Day 2 of the AI Voice Agents Challenge, focusing on building a high-performance, real-time voice agent capable of handling complex coffee orders.

The agent simulates a complete drive-thru or counter ordering experience, designed for low latency and natural, human-like interaction.

---

## 🚀 Key Features

* **Real-Time Conversational Flow:** Built on LiveKit Agents for handling bi-directional streaming audio.
* **Ultra-Low Latency TTS:** Utilizes the **Murf Falcon TTS API** to achieve **sub-150ms Time-to-First-Audio (TTFA)**, ensuring the conversation feels instant and lag-free.
* **Complex Order Handling:** Successfully processes natural language requests for custom drinks, including size, type (Latte, Espresso), milk, syrups, and temperature.
* **Barge-In and Interruption Management:** The agent is configured to handle user interruptions and mid-sentence corrections gracefully.
* **Automated Data Persistence:** Finalized orders are processed and automatically saved to the backend as structured **JSON files** in the `/orders` directory, ready for integration with a Point of Sale (POS) or Kitchen Display System (KDS).

---

## ⚙️ Technology Stack

| Component | Technology / Library | Purpose |
| :--- | :--- | :--- |
| **Agent Framework** | LiveKit Agents | Orchestration and handling of real-time voice sessions. |
| **Text-to-Speech (TTS)** | Murf Falcon API | High-speed, low-latency voice synthesis. |
| **ASR / NLP** | [Specify your ASR/NLP here, e.g., OpenAI/Local LLM] | Real-time speech transcription and intent processing. |
| **Language** | Python | Core agent logic and state management. |

---

## 🏃 Getting Started

### Prerequisites

* Python 3.8+
* A Murf AI API Key (for Falcon TTS)
* A LiveKit Server running or access to a LiveKit Cloud project.

### Installation

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/Mohammed-habeeb78/MURF_AI_day2.git](https://github.com/Mohammed-habeeb78/MURF_AI_day2.git)
    cd MURF_AI_day2
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
The agent will connect to your LiveKit server and be ready to accept voice connections (e.g., from the LiveKit Playground or a custom client).

📁 Project Structure
MURF_AI_day2/
├── agent.py               # Main Barista Agent logic and LiveKit Agent setup
├── requirements.txt       # Project dependencies
├── .env.example           # Template for environment variables
├── orders/                # Directory where finalized JSON orders are saved
│   └── 2025-11-24_order_1.json 
└── README.md              # This file
🤝 Contribution
Feel free to open issues or submit pull requests. All feedback is welcome!

🙏 Credits
Challenge Organizers: Murf AI & LiveKit

Challenge Link: https://github.com/murf-ai/ten-days-of-voice-agents-2025/blob/main/challenges/Day%202%20Task.md
