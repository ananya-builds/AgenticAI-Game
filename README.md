# AgenticAI-Game

A simple, lightweight sandbox project exploring how Large Language Models (LLMs) can act as decision-making agents in reinforcement learning environments. The LLM is prompted to choose actions, not trained. This repository implements a progressive roadmap where each tier introduces a new core challenge—from basic perception to long-horizon memory and planning.

---

## What's Inside?

* **`tier0.py`**: A baseline script that sets up a 4x4 `FrozenLake-v1` game via Gymnasium, serializes the board state into a text prompt and queries a Google Gemini Flash model to choose valid actions (`0 = Left, 1 = Down, 2 = Right, 3 = Up`). It includes clean error handling and step-by-step logging.
* **`requirements.txt`**: Lists the essential project dependencies:
  * `gymnasium` (Reinforcement learning environments)
  * `python-dotenv` (Secure local environment variable handling)
  * `google-genai` (Official Google GenAI SDK)
* **`.gitignore`**: Keeps local junk out of version control, cleanly ignoring your secret `.env` file, virtual environments (`venv/`), Python bytecode caches and editor configurations.

---
 
## 🚀 Quick Start
 
1. Clone this repository and open the project folder in your editor (e.g., VS Code).
2. _(Optional)_ Create and activate a Python virtual environment to keep dependencies isolated.
3. Install the dependencies with `pip install -r requirements.txt`.
4. Get a Gemini API key from Google AI Studio.
5. Create a `.env` file in the project folder and add your key as `GEMINI_API_KEY=your_key_here`.
6. Run `python tier0.py` and watch the agent play FrozenLake.

Your `.env` file is git-ignored, so your key stays local.
 
---

## 🗺️ Project Roadmap

Each tier adds one new difficulty.

- **✅ Tier 0: FrozenLake**
  - Proves the perception → LLM decision → action loop runs end to end, with logging.

- **⏭️ Tier 1: 2048 / Snake**
  - Single-step reasoning on a static grid. Focus is turning board state into prompts the LLM reasons over well.

- **⬜ Tier 2: Sokoban**
  - Multi-step planning where wrong moves can leave you stuck. Adds self-critique, retry-on-stuck and lightweight search to fix where naive "next move" prompting fails.

- **⬜ Tier 3: Atari Pong / Breakout**
  - Real-time play with pixel-based state. Needs a perception layer and a fast heuristic for reflexes, with the LLM handling higher-level strategy.

- **⬜ Tier 4: Pokémon (PyBoy)**
  - Hours-long playthroughs that need persistent memory, goal decomposition and context management. Retrieval-based (RAG-style) memory applies directly.

- **⬜ Tier 5: Battlesnake / generals.io _(optional)_**
  - Competitive multi-agent play that requires opponent modelling. Reuses the Tier 1–2 framework as a side track.