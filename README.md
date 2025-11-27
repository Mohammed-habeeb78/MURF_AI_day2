# 🏦 ICICI Bank Fraud Alert Voice Agent (SQLite Backend)

This project is a solution for Day 6 of the **Ten Days of Voice Agents Challenge** by Murf and LiveKit. It implements an AI Voice Agent that simulates a **Fraud Detection Specialist** from ICICI Bank.

The agent, named 'Alex', calls a customer to verify a high-risk transaction. It follows a strict security protocol, authenticates the customer's identity, reviews the transaction, and updates a backend database based on the customer's confirmation.

## 🚀 Agent Workflow & Logic

The agent follows a strict, sequential security protocol enforced by its internal instructions and the use of dedicated tools.

1.  **Greeting & Initial Query:** Greets the user and asks for their first name.
2.  **Customer Lookup:** Calls the `lookup_customer(name)` tool to find a pending fraud case.
3.  **Identity Verification:** Asks the user for their unique **Security Identifier**.
    * **Success:** Continues to the transaction review.
    * **Failure:** Politely ends the call and advises the customer to contact the bank's main line.
4.  **Transaction Review:** Explains the suspicious transaction (amount, merchant, time) found in the database.
5.  **Resolution:** Asks the crucial question: "Did you make this transaction?"
    * **YES:** Calls `resolve_fraud_case('confirmed_safe')`.
    * **NO:** Calls `resolve_fraud_case('confirmed_fraud')` (which simulates blocking the card).
6.  **Professional Close:** Provides a final update and ends the call.

## 🛠️ Project Setup

### 1. Prerequisites

* Python 3.9+
* LiveKit and Murf API Keys

### 2. Environment Variables

Create a file named `.env.local` in the project root and populate it with your credentials:

```bash
# LiveKit Credentials
LIVEKIT_URL="wss://<your_livekit_url>"
LIVEKIT_API_KEY="<your_api_key>"
LIVEKIT_API_SECRET="<your_api_secret>"

# Murf API Key (used for high-speed TTS)
MURF_API_KEY="<your_murf_api_key>"

# Deepgram API Key (used for STT)
DEEPGRAM_API_KEY="<your_deepgram_api_key>"

# Google API Key (used for LLM)
GOOGLE_API_KEY="<your_google_api_key>"
