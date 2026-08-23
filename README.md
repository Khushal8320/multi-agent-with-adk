# 🤖 Google ADK Multi-Agent Application

A beginner-friendly **multi-agent AI application built with Google's Agent Development Kit (ADK)** and Gemini models.

This project demonstrates how a **root/coordinator agent** can understand a user's request and delegate specific tasks to specialized sub-agents or tools.

## 🚀 Project Overview

The application contains a main **Root Agent** that coordinates three types of requests:

* 👋 Greetings → `greeting_agent`
* 👋 Farewells → `farewell_agent`
* 🌤️ Weather requests → `get_weather` tool

The goal of this project is to understand the fundamentals of **Agentic AI, tool calling, and multi-agent orchestration** using Google ADK.

## 🏗️ Architecture

```text
                         User
                          │
                          ▼
                    ┌─────────────┐
                    │ Root Agent  │
                    └──────┬──────┘
                           │
              ┌────────────┼────────────┐
              │            │            │
              ▼            ▼            ▼
       Greeting Agent  Farewell Agent  Weather Tool
              │            │            │
              ▼            ▼            ▼
         say_hello     say_goodbye   get_weather
              │            │            │
              └────────────┴────────────┘
                           │
                           ▼
                        Response
```

## ✨ Features

### 🤖 Root Agent

The root agent acts as the main coordinator.

It analyzes the user's request and determines whether to:

* Delegate a greeting to the greeting agent
* Delegate a farewell to the farewell agent
* Use the weather tool
* Respond appropriately to unsupported requests

### 👋 Greeting Agent

The greeting agent handles simple greetings such as:

```text
Hello
Hi
Hey
Hello Khushal
```

It uses the `say_hello` tool to generate the response.

### 👋 Farewell Agent

The farewell agent handles messages such as:

```text
Goodbye
Bye
See you later
Goodbye Khushal
```

It uses the `say_goodbye` tool.

### 🌤️ Weather Tool

The root agent can call a Python function to retrieve weather information.

Example:

```text
What's the weather in New York?
```

The tool returns a structured response containing the weather status and report.

## 🛠️ Technologies Used

* **Python**
* **Google ADK (Agent Development Kit)**
* **Google Gemini**
* **Python-dotenv**
* **Agent Tools**
* **Multi-Agent Orchestration**
* **Function/Tool Calling**

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install google-adk python-dotenv
```

### 4. Configure your API key

Create a `.env` file:

```env
GOOGLE_API_KEY=your_google_api_key
```

**Do not commit your `.env` file to GitHub.**

Add this to `.gitignore`:

```text
.env
.venv/
__pycache__/
```

## ▶️ Running the Application

If your project follows the Google ADK project structure, run:

```bash
adk web
```

Then open the local URL provided by ADK.

Try messages such as:

```text
Hello
```

```text
Hello Khushal
```

```text
Goodbye
```

```text
What's the weather in New York?
```

## 🧠 Key Concepts Learned

This project helped me understand several important concepts in Agentic AI.

### 1. Agents

An agent combines:

```text
Model + Instructions + Tools
```

For example:

```python
Agent(
    model="gemini-3.6-flash",
    name="greeting_agent",
    instruction="Handle greetings.",
    tools=[say_hello]
)
```

### 2. Tools

Tools allow an AI agent to interact with functions and external capabilities.

Example:

```python
def say_hello(name="there"):
    return f"Hello {name}!"
```

The model can decide when the tool should be called.

### 3. Multi-Agent Systems

Instead of making one agent responsible for everything, specialized agents can handle specific tasks.

```text
Root Agent
    │
    ├── Greeting Agent
    ├── Farewell Agent
    └── Weather Tool
```

This approach can make larger AI applications easier to organize and maintain.

### 4. Agent Delegation

The root agent determines which specialized agent should handle a request.

For example:

```text
User: Hello
       ↓
Root Agent
       ↓
Greeting Agent
       ↓
say_hello()
       ↓
Response
```

## 🧪 Example Interaction

```text
User:
Hello Khushal

Root Agent:
Delegates to greeting_agent

Greeting Agent:
Calls say_hello("Khushal")

Response:
Hello Khushal!
```

Another example:

```text
User:
Goodbye

Root Agent:
Delegates to farewell_agent

Farewell Agent:
Calls say_goodbye()

Response:
Goodbye there! Have a great day.
```

## 🔧 Project Structure

```text
google-adk-multi-agent/
│
├── agent.py
├── .env
├── .gitignore
├── requirements.txt
└── README.md
```

## 📚 What I Learned

Through this project, I explored:

* How Google ADK agents are created
* How Gemini models are connected to agents
* How tools/functions can be exposed to agents
* How a root agent can coordinate specialized agents
* How sessions are used in agent applications
* How to debug model/API compatibility issues
* How to structure a simple multi-agent application

## 🚀 Future Improvements

Planned improvements include:

* [ ] Add real-time weather API integration
* [ ] Add more specialized agents
* [ ] Add persistent memory
* [ ] Add web search capabilities
* [ ] Add MCP tools
* [ ] Add a Streamlit interface
* [ ] Add conversation history
* [ ] Deploy the application
* [ ] Add automated testing

## 🎯 Purpose

This project was created as a **learning project to explore Agentic AI and Google ADK**.

The focus is on understanding how AI agents can use tools, delegate tasks, and work together rather than simply generating text.

## 👨‍💻 Author

**Khushal Patel**

Interested in:

* Artificial Intelligence
* Agentic AI
* Generative AI
* Python
* Data Analytics
* AI Automation
* MCP
* Machine Learning

---

⭐ If you found this project useful, feel free to star the repository!
