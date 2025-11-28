# 🇮🇳 Day 7: AI Food & Grocery Ordering Voice Agent (Indian Context)

This project completes Day 7 of the AI Voice Agent Challenge. It implements a fully functional voice agent for food and grocery ordering, featuring persistent state management using a local **SQLite database** and an Indian-centric product catalog.

The agent, named **"Robin,"** is designed to provide a natural, conversational interface for an e-commerce platform.

## ✨ Features

* **Persistent SQLite Backend:** Uses `order_db.sqlite` to store product catalog, order history, and simulate order updates.
* **Indian Catalog:** Seeded with popular Indian brands and staples (Amul, Tata, Maggi, Basmati Rice, etc.).
* **Comprehensive Cart Management:** Tools for searching the catalog (`find_item`), managing the cart (`add_to_cart`, `remove_from_cart`, `show_cart`, `update_cart_quantity`).
* **Intelligent Recipe Tooling:**
    * `add_recipe`: Adds pre-defined ingredient lists for common Indian dishes (e.g., "chai", "paneer butter masala").
    * `ingredients_for`: Attempts to infer ingredients for a dish based on catalog tags and can parse **servings/quantity** from the user's request.
* **Real-time Order Tracking Simulation:**
    * The `place_order` tool triggers an **async background task** (`simulate_delivery_flow`) that automatically updates the order status in the DB every 5 seconds (e.g., `received` -> `confirmed` -> `shipped` -> `delivered`).
    * Tools to check status (`get_order_status`), view history (`order_history`), and cancel orders (`cancel_order`).
* **High-Speed TTS:** Leverages the **Murf Falcon** API for low-latency text-to-speech, ensuring a fast and natural user experience.

## 🛠️ Tools & Technologies Used

* **LLM & Orchestration:** LiveKit Agents with Google Gemini 2.5 Flash
* **Text-to-Speech (TTS):** Murf Falcon (for speed and quality)
* **Speech-to-Text (STT):** Deepgram Nova-3
* **Database:** SQLite3 (`order_db.sqlite`)
* **Language:** Python 3.10+
* **Order Simulation:** Python `asyncio`

## 💬 Agent Tools (Key Functions)

The agent has access to the following domain-specific tools, defined as `function_tool`s in the code:

| Function Name | Description |
| :--- | :--- |
| `find_item` | Searches the product catalog by name or tag. |
| `add_to_cart` | Adds a specified item ID and quantity to the user's cart. |
| `remove_from_cart` | Removes an item from the cart. |
| `update_cart_quantity` | Changes the quantity of an item already in the cart. |
| `show_cart` | Displays all items currently in the cart with the total cost. |
| `add_recipe` | Adds all ingredients for a known dish (e.g., 'chai'). |
| `ingredients_for` | Advanced recipe tool using tag-inference and serving parsing. |
| `place_order` | Finalizes the purchase, clears the cart, and triggers the async status simulation. |
| `cancel_order` | Cancels an order if it hasn't been delivered yet. |
| `get_order_status` | Checks the real-time status of a placed order. |
| `order_history` | Lists the customer's recent orders. |

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [Your Repo URL]
    cd [your-repo-folder]
    ```

2.  **Set up the environment:**
    * Ensure you have a Python environment ready.
    * Create a `.env.local` file with your API keys:
        ```env
        LIVEKIT_URL="ws://localhost:7880"
        LIVEKIT_API_KEY="your_api_key"
        LIVEKIT_API_SECRET="your_api_secret"
        MURF_API_KEY="your_murf_api_key"
        DEEPGRAM_API_KEY="your_deepgram_api_key"
        ```

3.  **Run the agent:**
    ```bash
    python food_agent_sqlite.py
    ```
    *(The agent will automatically seed the `order_db.sqlite` file on the first run.)*

4.  **Connect:** Use the LiveKit Egress or a custom client to connect to the running agent.

---
