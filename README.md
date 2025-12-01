# 🎭 AI Voice Agent Challenge: Day 10 - Improv Battle Host

This project is the final submission for the LiveKit and Murf AI "10 Days of Voice Agents Challenge," focusing on creating an engaging, voice-first AI host for an improv game.

The agent, **"Improv Battle Host,"** guides a player through a series of short, challenging improv scenarios, providing real-time reactions and a final summary.

## ✨ Features

* **Voice-First Interaction:** Built on the LiveKit Agents SDK for seamless, low-latency, real-time voice conversation.
* **High-Energy Host Persona:** Uses a detailed system prompt and dedicated tools to act as a witty, encouraging, and clear TV show host.
* **Dynamic Improv Game Flow:** Manages session state (rounds, player name, scenarios) using a Pydantic `Userdata` class.
* **Scenario Management:** Presents pre-seeded, engaging scenarios and avoids repetition.
* **Performance Feedback:** Utilizes a lightweight heuristic (`_host_reaction_text`) to generate varied, tone-specific (supportive, neutral, critical) feedback after each player performance.
* **Show Summary:** Produces a final recap and a personalized profile of the player's improv style upon completion.
* **Fast TTS Integration:** Uses the **Murf Falcon TTS API** for the fastest possible text-to-speech output, ensuring the host's responses feel immediate and natural.

## 🛠️ Technology Stack

* **Agent Framework:** LiveKit Agents SDK
* **LLM (Large Language Model):** Google Gemini 2.5 Flash
* **TTS (Text-to-Speech):** Murf Falcon (using `murf.TTS`)
* **STT (Speech-to-Text):** Deepgram Nova-3
* **Voice Activity Detection (VAD):** LiveKit's Multilingual Turn Detector & Silero VAD
* **Noise Cancellation:** LiveKit's BVC

## 🔧 Core Tools Exposed to the LLM

The `GameMasterAgent` uses the following tools to manage the show flow:

| Tool Name | Description | Used By Host When... |
| :--- | :--- | :--- |
| `start_show` | Initializes the game session, player name, and max rounds. | The user says "start show" or similar. |
| `next_scenario` | Advances to the next round if rounds are remaining. | The user says "next" or after a reaction if the host prompts for the next scene. |
| `record_performance` | Saves the player's transcribed improv, generates a host reaction, and checks for the end of the game. | The user stops speaking after receiving a scenario (handled by the LiveKit runtime plumbing). |
| `summarize_show` | Generates a final recap and player profile. | The maximum number of rounds has been reached. |
| `stop_show` | Allows for graceful early exit. | The user explicitly asks to end the show. |

## 🚀 Getting Started

1.  **Set up your environment variables** in a `.env.local` file (or similar), including API keys for LiveKit, Murf, Deepgram, and Google.

    ```bash
    LIVEKIT_URL="..."
    LIVEKIT_API_KEY="..."
    LIVEKIT_API_SECRET="..."
    MURF_API_KEY="..."
    DEEPGRAM_API_KEY="..."
    GOOGLE_API_KEY="..."
    ```

2.  **Run the agent** using the LiveKit CLI:

    ```bash
    lk-agents run --entrypoint 'your_file_name:entrypoint'
    ```
