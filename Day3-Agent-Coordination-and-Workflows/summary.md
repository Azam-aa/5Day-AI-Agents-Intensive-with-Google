# 🧠 Day 3 Summary — Context Engineering: Sessions & Memory

## 📘 Overview
Day 3 focuses on **Context Engineering** — the next step beyond Prompt Engineering.  
It’s about how AI agents **remember, learn, and personalize** across interactions by managing **Sessions** (short-term memory) and **Memory** (long-term knowledge).

In simple terms:
> Context Engineering helps AI *think continuously*, not just respond once.

---

## 🧩 1. Context Engineering

### 🧠 Technical Definition:
A system for **dynamically assembling, managing, and pruning** all the information that goes into a model’s context window — including prompts, memory, and external data.

### 💬 Simple Meaning:
It’s like a chef preparing all the right ingredients before cooking — making sure the AI only uses what it needs at that moment.

### 🔍 Key Functions:
- **Assemble:** Collect relevant info (system prompt, examples, history, memory).
- **Summarize:** Condense old info to save space.
- **Inject:** Add necessary data into the model’s input before every response.

### 🧱 Components Managed by Context Engineering:
- System Instructions  
- Tool Definitions  
- Few-Shot Examples  
- Session History  
- Long-Term Memory  
- External Data (like from RAG systems)

---

## 🧩 2. Sessions

### 🧠 Technical Definition:
A **Session** is a container for a single continuous conversation, storing short-term data, events, and state.

### 💬 Simple Meaning:
It’s like a “chat tab” — it remembers what’s going on *right now* but forgets when closed.

### 🗂️ What It Stores:
- **Events:** user inputs, model replies, tool calls, and results  
- **State:** temporary working memory (e.g., user cart, progress)

### ⚙️ Session Storage:
Handled by systems like **Vertex AI Agent Engine Sessions** or **Redis/Spanner** for persistence.

### 🔁 Managing Long Conversations:
1. **Sliding Window:** Keep the latest N turns.  
2. **Token Limit:** Keep only recent messages within token budget.  
3. **Recursive Summarization:** Periodically summarize older turns.  
4. **Trigger-Based:** Compact when event/time/count thresholds are reached.

#### Example (ADK):
```python
from google.adk.apps import App
from google.adk.plugins.context_filter_plugin import ContextFilterPlugin

app = App(
    name='hello_world_app',
    root_agent=agent,
    plugins=[ContextFilterPlugin(num_invocations_to_keep=10)]
)

