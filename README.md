# 🛍️ Darren: Voice E-commerce Agent (Amex Shop)

This project is a submission for Day 9 of the **AI Voice Agent Challenge**, focusing on building a fully functional, transactional **E-commerce Voice Agent**.

Named "Darren" after the friendly, helpful shopkeeper archetype, this agent assists customers in browsing the product catalog, managing their shopping cart, and placing orders using only voice commands.

## ✨ Features

* **Product Catalog:** Manages a simple, Indian-themed catalog (Amex Shop) with items like T-shirts, Mugs, Hoodies, and Mobile Phones.
* **Conversational Shopping:** Allows users to search the catalog, add items to the cart by name, ID, or ordinal reference (e.g., "the second phone").
* **Cart Management:** Tools to view and clear the current session's shopping cart.
* **Order Placement:** Simulates a checkout process by placing and persisting the order to a local `orders.json` file.
* **Voice-First Design:** Optimized for short, clear spoken turns, powered by high-speed Text-to-Speech (TTS).

## 🚀 Technical Stack & Challenge Fulfillment

| Component | Technology Used | Rationale |
| :--- | :--- | :--- |
| **Agent Framework** | **LiveKit Agents (Python SDK)** | Provides the core real-time voice infrastructure and LLM tool orchestration. |
| **Text-to-Speech (TTS)** | **Murf Falcon** (via `livekit.plugins.murf`) | Chosen for its **speed and naturalness**, a key requirement of the challenge. |
| **Large Language Model (LLM)** | **Google Gemini 2.5 Flash** (via `livekit.plugins.google`) | Provides the reasoning and tool-calling capabilities. |
| **Speech-to-Text (STT)** | **Deepgram Nova-3** (via `livekit.plugins.deepgram`) | Used for accurate transcription of customer voice input. |
| **E-commerce Protocol** | **Custom Merchant Layer & Tools** | Implements the core logic inspired by the **Agentic Commerce Protocol (ACP)** principles. |

## 🛠️ Setup and Installation

### 1. Environment Variables

Create a file named `.env.local` in the root directory and populate it with your API keys:

```ini
# LiveKit Server Details
LIVEKIT_URL="wss://<your-livekit-host-url>"
LIVEKIT_API_KEY="<your-livekit-api-key>"
LIVEKIT_API_SECRET="<your-livekit-api-secret>"

# Murf TTS API Key
MURF_API_KEY="<your-murf-api-key>"

# Deepgram STT API Key
DEEPGRAM_API_KEY="<your-deepgram-api-key>"

# Google LLM API Key
GEMINI_API_KEY="<your-gemini-api-key>"
2. Dependencies
Install the necessary Python packages:

Bash

pip install -r requirements.txt
# (Assuming requirements.txt contains: livekit-agents, python-dotenv, livekit-plugins-murf, 
# livekit-plugins-deepgram, livekit-plugins-google, livekit-plugins-silero)
3. Run the Agent
Execute the agent script using the LiveKit CLI:

Bash

livekit-agent run voice_ecom_agent.py
4. Connect to the Room
Once the agent is running, connect a client (e.g., the LiveKit Voice Agent Demo UI) to the specified LiveKit room to interact with Ramu Kaka.

👥 Agent Architecture
The agent uses a standard LiveKit Agent pipeline:

Audio Input: Customer's voice is processed by Deepgram STT.

LLM Reasoning: The transcript is sent to Gemini 2.5 Flash, which decides whether to use one of the custom e-commerce tools or to generate a spoken response.

Tool Execution: If a tool like add_to_cart or show_catalog is called, the Python function executes and returns a summary string.

Voice Output: The final text response is synthesized using Murf Falcon TTS for rapid, high-quality audio output back to the customer.
