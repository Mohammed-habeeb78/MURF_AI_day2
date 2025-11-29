🎙️ Project "Aurek": The Voice Game Master Agent

<!-- Professional Header & Tagline -->

A zero-latency, tool-driven AI Game Master for voice-only D&D adventures.
Leveraging high-speed TTS and robust LLM function calling for immersive, continuous storytelling.

🛡️ Status & Tech Badges

Status

Model Stack

Speech Providers

Framework









Project State: Active Development

Domain: Real-Time Conversational AI (CAI)





📜 Table of Contents

🌟 Quick Overview

🛠️ Technology Stack

🧠 Architectural Deep Dive

⚙️ Key Tool Functions

🚀 Setup and Installation

💡 Usage Example

🗺️ Roadmap

🌟 Quick Overview

The "Aurek" agent operates as a highly responsive, low-magic fantasy Game Master for the Brinmere Mini-Arc. The agent’s core strength lies in its ability to decouple narrative voice from game logic.

Feature

Description

Persona

'Aurek' — Calm, mysterious narrator with persistent memory.

Game Logic

Handled by specialized Python functions, preventing LLM drift or hallucination of game state.

State Persistence

Managed via the Userdata dataclass (Journal, Inventory, current_scene).

Voice UX

Optimized for zero-latency turn-taking; every GM response strictly ends with the prompt: "What do you do?"

🛠️ Technology Stack

Component

Technology

Technical Role in the Agent Pipeline

Framework

livekit-agents

Core pipeline for audio streaming, conferencing, and job management.

LLM

google.LLM (Gemini 2.5 Flash)

Mandatory Tool Router. Interprets player intent and routes execution to the correct Python function.

TTS (Output)

murf.TTS (Murf Falcon)

Critical low-latency performance. Converts the GM's response text to ultra-fast audio.

STT (Input)

deepgram.STT (Nova-3)

Provides highly accurate transcription of spoken player actions.

State Manager

Python dataclasses

Manages the session's memory (Userdata) across all turns for continuity.

VAD / Turns

silero.VAD

Detects silence to accurately determine the end of the player's spoken turn.

🧠 Architectural Deep Dive

The agent adheres to a strict Tool-Calling Architecture to ensure predictable, deterministic gameplay.

Player Input 🗣️: Player speaks an action (e.g., "I will take the box").

Transcription & Turn End 📝: Deepgram & VAD process the audio and confirm the turn is over.

LLM Intent & Tool Call 🤖: Gemini 2.5 Flash receives the text and generates the tool call: player_action(action="take the box").

Tool Execution (Game Engine) 💻: The Python function player_action executes the game logic:

Fuzzy Matching resolves "take the box" to the internal key (inspect_box).

State Update is performed (add_journal, update current_scene).

A clean text block of the result and the next scene is returned.

GM Narration ✨: The LLM receives the text block, applies the 'Aurek' persona, and prepends a dramatic flair to the scene description.

Low-Latency Output 🔊: Murf Falcon renders the final narrative to audio, closing the loop back to the player.

⚙️ Key Tool Functions

The agent's logic is defined by these five custom function_tool implementations:

Function

Description

Technical Role

start_adventure

Resets the game state and delivers the opening narration.

Initialization

get_scene

Returns the current descriptive text and available choices to the player.

Context Retrieval

player_action

The Core Engine. Resolves player input against defined actions, updates the Userdata state, and handles scene transitions.

State Transition

show_journal

Presents the current inventory, key facts, and recent choices made.

Reference & Debugging

restart_adventure

Hard reset of the session, including all history and inventory.

System Reset

🚀 Setup and Installation

Prerequisites

Python 3.9+ environment.

Install LiveKit Agents and dependencies: pip install livekit-agents livekit-plugins-deepgram livekit-plugins-murf livekit-plugins-silero

Environment Configuration

Create a file named .env.local in the project root and populate it with your API credentials. Note the explicit requirement for Murf and Deepgram keys.

LIVEKIT_URL="ws://<your-livekit-url>"
LIVEKIT_API_KEY="<your-api-key>"
LIVEKIT_API_SECRET="<your-api-secret>"

MURF_API_KEY="<your-murf-api-key>"
DEEPGRAM_API_KEY="<your-deepgram-api-key>"
# Google key may be optional depending on your LiveKit setup
GOOGLE_API_KEY="<your-gemini-api-key>"


Running the Agent

Start the worker and connect it to your LiveKit room infrastructure:

python game_master_agent.py


The worker will wait for a job and can be invited into any LiveKit room you create.

💡 Usage Example

Once the agent joins the room, the player begins the session with:

Player Speaks

LLM Tool Called

Agent Response

"Start the adventure, I'm Elara."

start_adventure(player_name="Elara")

[Aurek's voice]: "Greetings Elara... You awake on the damp shore of Brinmere... What do you do?"

"I inspect the box."

player_action(action="inspect the box")

[Aurek's voice]: "You chose 'inspect_box'. The box is warm... Inside is a folded scrap of parchment... What do you do?"

"Show my journal."

show_journal()

[Aurek's voice]: "Journal entries: None. Inventory: None. What do you do?"

🗺️ Roadmap

Future enhancements planned to evolve this agent from a mini-arc demo into a full conversational RPG platform:

✅ Multi-speaker NPC Voices: Assigning unique Murf voices to named NPCs (e.g., 'Joe' for a tavern keeper, 'Jane' for a quest giver).

🔄 Dynamic World Generation: Replacing the static WORLD dictionary with a dynamic LLM-driven scene generation system, constrained by genre rules.

⚔️ Simple Combat System: Implementing dice-roll mechanics using tools to resolve conflict (e.g., roll_d20(modifier)).

🌐 Firestore Integration: Persistent player profiles and long-term campaign tracking via cloud storage.
