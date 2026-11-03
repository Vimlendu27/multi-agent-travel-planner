# ✈️ Multi-Agent AI Travel Planning System

### Intelligent Travel Planning using LangGraph, MCP, Supervisor Agent, Guardrails & Human-in-the-Loop

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?logo=python" />
  <img src="https://img.shields.io/badge/LangGraph-Agent%20Orchestration-green" />
  <img src="https://img.shields.io/badge/MCP-Model%20Context%20Protocol-purple" />
  <img src="https://img.shields.io/badge/Database-PostgreSQL-blue?logo=postgresql" />
  <img src="https://img.shields.io/badge/Frontend-Streamlit-red?logo=streamlit" />
  <img src="https://img.shields.io/badge/LLM-Groq-orange" />
</p>

---

# 📌 1. Project Overview

The **Multi-Agent AI Travel Planning System** is an intelligent application designed to automate travel planning through collaborative AI agents.

This project extends the Multi-Agent Travel Planning System developed in Part 1 and Part 2 by introducing advanced agent orchestration, request validation, and human approval mechanisms.

The application uses **LangGraph, Large Language Models (LLMs), and Model Context Protocol (MCP)** to coordinate multiple specialized AI agents.

A centralized **Supervisor Agent** understands user requirements, dynamically selects the required agents, and manages the overall execution workflow.

The system also implements Input Guardrails, Shared State Management, Human-in-the-Loop (HITL), and PostgreSQL-based Persistent Memory.

The goal is to build an intelligent, interactive, and extensible AI-powered travel planning application.

---

# 📚 2. Project Series & Previous Implementations

This project is the third part of a Multi-Agent AI development series.

## Part 1 – Multi-Agent Travel Planning System

**GitHub Repository:**

[AI Travel Planning System using LangGraph](https://github.com/codewithaarohi/AI-Travel-Planning-System-using-LangGraph)

**Video Tutorial:**

[Build a Real-World Multi-Agent AI System using LangGraph | Multi-Agent AI + Memory + APIs](https://youtu.be/ctHby5vhDqg)

## Part 2 – Multi-Agent Travel Planning System with MCP

**GitHub Repository:**

[AI Travel Planning App using LangGraph and MCP](https://github.com/codewithaarohi/AI-Travel-Planning-App-using-LangGraph-and-MCP)

**Video Tutorial:**

[Build a Real-World Multi-Agent AI System using LangGraph | Multi-Agent AI + Memory + MCP](https://youtu.be/DjMX7o2EeV0)

## Part 3 – Advanced Multi-Agent Architecture

This implementation introduces:

- Supervisor Agent for dynamic agent selection and orchestration.
- Input Guardrails for request validation and safety checks.
- Human-in-the-Loop for itinerary approval and modifications.
- Shared State Management for agent communication.
- PostgreSQL-based Persistent Memory.
- Advanced workflow management using LangGraph.

---

# 🏗️ 3. System Architecture

The application follows a Supervisor-based Multi-Agent Architecture.

The Supervisor Agent acts as the central coordinator and dynamically manages specialized agents according to user requirements.

## High-Level Architecture Diagram

```mermaid
flowchart TD
    A["User Request"] --> B["Input Guardrails"]

    B -->|Valid Request| C["Supervisor Agent"]
    B -->|Invalid Request| X["Blocked Request"]

    C --> D["LangGraph Orchestrator"]

    D --> E["Flight Agent"]
    D --> F["Hotel Agent"]
    D --> G["Weather Agent"]
    D --> H["Budget Agent"]
    D --> I["Itinerary Agent"]

    E --> J["MCP Integration"]
    F --> J
    G --> J

    J --> K["External APIs"]

    E --> L["Shared State"]
    F --> L
    G --> L
    H --> L
    I --> L

    L --> M["Human-in-the-Loop"]

    M -->|Approve| N["Final Response Agent"]
    M -->|Request Changes| C

    N --> O["Final Travel Plan"]

    L <--> P[("PostgreSQL Persistent Memory")]
```

## Architecture Components

| Component | Responsibility |
|---|---|
| User Interface | Collects travel requirements |
| Input Guardrails | Validates incoming requests |
| Supervisor Agent | Coordinates specialized AI agents |
| LangGraph | Manages workflow and agent execution |
| Flight Agent | Searches flight information |
| Hotel Agent | Finds hotel options |
| Weather Agent | Retrieves weather forecasts |
| Budget Agent | Analyzes estimated expenses |
| Itinerary Agent | Creates day-wise travel plans |
| MCP | Connects agents with external tools |
| Shared State | Shares information between agents |
| Human-in-the-Loop | Provides user approval and modification |
| Final Response Agent | Generates the final travel plan |
| PostgreSQL | Stores conversations and persistent checkpoints |

---

# ✨ 4. Key Features

| Feature | Description |
|---|---|
| Multi-Agent Architecture | Multiple specialized agents handle individual travel tasks. |
| Supervisor Agent | Dynamically selects and coordinates required agents. |
| Input Guardrails | Validates requests and blocks invalid inputs. |
| Human-in-the-Loop | Allows users to approve or modify generated itineraries. |
| LangGraph Orchestration | Manages agent workflows and execution paths. |
| MCP Integration | Connects AI agents with external tools and services. |
| Shared State Management | Enables information sharing between agents. |
| PostgreSQL Memory | Maintains persistent conversations and workflow state. |
| Flight Search | Retrieves flight information using AviationStack MCP. |
| Web Search | Uses Tavily for travel research. |
| Weather Information | Retrieves weather information through Weather MCP. |
| Streamlit Interface | Provides an interactive travel planning experience. |

---

# 🤖 5. Specialized AI Agents

The system uses multiple specialized agents, each responsible for a specific task.

| Agent | Responsibility |
|---|---|
| Supervisor Agent | Understands user intent and coordinates agents. |
| Flight Agent | Searches flights, airlines, routes, and fares. |
| Hotel Agent | Searches hotels and compares prices and amenities. |
| Weather Agent | Retrieves weather forecasts and climate information. |
| Budget Agent | Calculates estimated travel expenses. |
| Itinerary Agent | Generates personalized day-wise travel plans. |
| Final Response Agent | Generates the final approved travel recommendations. |

---

# 🔄 6. End-to-End Execution Workflow

Example User Request:

```text
Plan a complete 7-day trip to Japan,
including flights, hotels and sightseeing
within a budget of ₹2,00,000.
```

The application follows the workflow below:

### Step 1 – User Input

The user submits a travel request through the Streamlit interface.

### Step 2 – Input Guardrails

The system validates the incoming request based on relevance, safety, and required travel information.

Invalid requests are blocked before starting the agent workflow.

### Step 3 – Supervisor Agent

The Supervisor Agent understands the user's intent and identifies which specialized agents are required.

### Step 4 – Specialized Agent Execution

- Flight Agent collects flight information.
- Hotel Agent searches hotel options.
- Weather Agent retrieves weather forecasts.
- Budget Agent analyzes estimated expenses.
- Itinerary Agent prepares a day-wise travel plan.

### Step 5 – MCP Tool Integration

Agents interact with external tools and services through MCP.

### Step 6 – Shared State Management

Each agent updates its results in the shared state so other agents can access the required information.

### Step 7 – Human-in-the-Loop

The generated itinerary is presented to the user.

The user can:

- Approve the generated itinerary.
- Request changes or modifications.

If changes are requested, the workflow routes back to the relevant agents.

### Step 8 – Final Response

The Final Response Agent generates the approved travel plan using the collected information.

### Step 9 – Persistent Memory

PostgreSQL stores conversation history and workflow checkpoints.

---

# 🛠️ 7. Technology Stack

| Category | Technology |
|---|---|
| Programming Language | Python |
| LLM Provider | Groq |
| Agent Framework | LangGraph |
| LLM Framework | LangChain |
| Tool Integration | Model Context Protocol (MCP) |
| Web Search | Tavily API |
| Flight Information | AviationStack API |
| Weather Information | OpenWeatherMap API |
| Database | PostgreSQL |
| Persistent Memory | LangGraph Checkpointer |
| Frontend | Streamlit |
| Backend Integration | Python APIs |

---

# 📋 8. Prerequisites

Before running the application, ensure the following tools are installed:

- Python 3.10 or later
- PostgreSQL
- Git
- Visual Studio Code (recommended)
- UV Package Manager
- Required API credentials

---

# 🚀 9. Installation & Setup Guide

Follow these steps to configure and run the application locally.

## Step 1 – Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL

cd multi-agent-travel-planner
```

## Step 2 – Create a Python Virtual Environment

```bash
python -m venv langgraph_env3
```

Activate the environment on Windows:

```powershell
langgraph_env3\Scripts\activate
```

## Step 3 – Install Dependencies

Install the required Python packages:

```bash
pip install langgraph langchain langchain-openai langchain-groq langchain-community langchain-tavily psycopg[binary] psycopg_pool python-dotenv tavily-python requests streamlit
```

Install PostgreSQL checkpoint dependencies:

```bash
pip install -U "psycopg[binary,pool]" langgraph-checkpoint-postgres
```

## Step 4 – Install and Configure PostgreSQL

Download PostgreSQL:

https://www.postgresql.org/download/

During installation, note your:

- PostgreSQL username
- PostgreSQL password
- PostgreSQL port number

Create the application database:

```sql
CREATE DATABASE langgraph_memory_demo;
```

## Step 5 – Configure Environment Variables

Create a `.env` file in the project root directory.

Add the following configuration:

```env
GROQ_API_KEY=your_groq_api_key

TAVILY_API_KEY=your_tavily_api_key

AVIATIONSTACK_API_KEY=your_aviationstack_api_key

OPENWEATHERMAP_API_KEY=your_openweathermap_api_key

DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost:5433/langgraph_memory_demo
```

**Important:**

- Replace all placeholder values with your actual credentials.
- Update the PostgreSQL port according to your configuration.
- Never commit your `.env` file to GitHub.
- Keep all API credentials secure.

---

# 🔑 10. API Configuration

Generate API keys from the following providers:

| API Provider | Purpose | Official Website |
|---|---|---|
| Groq | LLM inference | https://console.groq.com |
| Tavily | Web search | https://www.tavily.com/ |
| AviationStack | Flight information | https://aviationstack.com/ |
| OpenWeatherMap | Weather information | https://openweathermap.org/ |

---

# 🔌 11. MCP Server Configuration

The application uses MCP servers to connect specialized AI agents with external tools and services.

## 11.1 AviationStack MCP Server

**GitHub Repository:**

https://github.com/Pradumnasaraf/aviationstack-mcp

### Clone the MCP Repository

Open PowerShell:

```powershell
E:

cd E:\Multi_agent_system_with_MCP

git clone https://github.com/Pradumnasaraf/aviationstack-mcp.git

cd aviationstack-mcp
```

### Install UV Package Manager

Check UV installation:

```bash
uv --version
```

Install UV:

```bash
pip install uv
```

If installation fails, use PowerShell:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

### Configure AviationStack API Key

Create a `.env` file inside the AviationStack MCP project directory:

```env
AVIATION_STACK_API_KEY=your_aviationstack_api_key
```

### Install Dependencies

```bash
uv sync
```

This command creates the virtual environment and installs the required project dependencies.

### Activate the Environment

```powershell
.venv\Scripts\activate
```

### Start AviationStack MCP Server

```bash
uv run -m aviationstack_mcp mcp run
```

Alternatively:

```bash
python -m aviationstack_mcp mcp run
```

The MCP server will start and wait for incoming client requests.

Keep the server running while using the application.

To stop the server:

```bash
CTRL + C
```

## 11.2 Weather MCP Server

Generate an API key from:

https://openweathermap.org/

Install the required dependencies:

```bash
pip install mcp requests
```

Configure the API key in your application's `.env` file:

```env
OPENWEATHERMAP_API_KEY=your_openweathermap_api_key
```

Start the Weather MCP Server using the configured server entry point in the project.

---

# ▶️ 12. Run the Application

After configuring the environment, database, API keys, and MCP servers, start the Streamlit application.

From the project root directory:

```bash
streamlit run frontend.py
```

Streamlit will start the application and display a local URL in the terminal.

Open the URL in your browser to access the travel planning interface.

---

# 💬 13. Example User Prompts

Try the following prompts to test the application:

**Example 1 – International Travel**

```text
Plan a complete 7-day trip to Japan,
including flights, hotels and sightseeing
within a budget of ₹2,00,000.
```

**Example 2 – Budget Travel**

```text
Plan a 4-day trip to Dubai for two people
with flight and hotel recommendations
within ₹1,00,000.
```

**Example 3 – Travel Modification**

```text
Change the hotel recommendation to a
more affordable option while keeping
the overall travel budget unchanged.
```

---

# 🛡️ 14. Guardrails & Human-in-the-Loop

## Input Guardrails

Input Guardrails validate incoming user requests before starting the agent workflow.

They help ensure:

- Request relevance.
- Input validity.
- Safety and policy compliance.
- Required travel information.

Invalid or unsupported requests are blocked before agent execution.

## Human-in-the-Loop (HITL)

Human-in-the-Loop introduces user approval into the AI workflow.

Users can review the generated itinerary and choose:

**Approve:**
The approved itinerary proceeds to the Final Response Agent.

**Request Changes:**
The workflow routes back to the relevant agents to regenerate or modify the requested information.

This provides better user control and reliability.

---

# 🗄️ 15. Memory & State Management

PostgreSQL is used for persistent memory and workflow checkpoint storage.

The application uses persistent storage to support:

- Conversation history.
- Agent workflow state.
- Execution checkpoints.
- Workflow continuation where configured.

Shared State enables agents to exchange information during execution, while PostgreSQL provides persistence across application sessions.

---

# 📁 16. Project Structure

```text
multi-agent-travel-planner/
│
├── README.md
├── requirements.txt
├── .env
│
├── agents.py
├── config.py
├── frontend.py
├── graph.py
├── mcp_client.py
├── state.py
├── weather_mcp_server.py
│
└── ...
```

---

# 🔮 17. Future Enhancements

The following improvements can extend the application towards production deployment:

- Docker-based application containerization.
- Kubernetes and Azure Kubernetes Service (AKS) deployment.
- CI/CD automation using Azure DevOps.
- Infrastructure provisioning using Terraform.
- Application monitoring using Azure Monitor.
- Distributed tracing and agent execution observability.
- Advanced retry and failure-handling mechanisms.
- Additional real-world travel API integrations.

---

# 🎯 18. Project Objective

The primary objective of this project is to design and implement a real-world Agentic AI application using multi-agent orchestration, LLMs, MCP, and persistent memory.

It demonstrates how multiple specialized AI agents can collaborate, use external tools, share information, and interact with humans to solve complex real-world tasks.

---

# 👨‍💻 19. Author

**Vimlendu Shekhar Rai**

Generative AI Engineer | Azure | DevOps | Agentic AI | LangGraph | MCP | LLM | RAG | Kubernetes | Terraform

---

⭐ If you find this project useful, consider giving this repository a star!

---
