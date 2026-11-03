# ✈️ Multi-Agent AI Travel Planning System
### Built with LangGraph, MCP, Supervisor Agent, Guardrails & Human-in-the-Loop

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![LangGraph](https://img.shields.io/badge/Framework-LangGraph-green)](https://www.langchain.com/langgraph)
[![MCP](https://img.shields.io/badge/Integration-MCP-purple)](https://modelcontextprotocol.io/)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue)](https://www.postgresql.org/)

## 📌 Project Overview

This project extends the Multi-Agent AI Travel Planning System developed in Part 1 and Part 2 by introducing advanced agent orchestration and workflow management capabilities.

The system leverages **LangGraph, Model Context Protocol (MCP), and Large Language Models (LLMs)** to build an intelligent travel planning application powered by multiple specialized AI agents.

A centralized **Supervisor Agent** dynamically understands user requests, selects the appropriate agents, and coordinates their execution.

The application also implements **Input Guardrails** for request validation and **Human-in-the-Loop (HITL)** for user approval and itinerary modifications.

The complete solution integrates external APIs, MCP servers, PostgreSQL-based persistent memory, and a Streamlit web interface to deliver an intelligent and interactive travel planning experience.

---

## 📚 Project Series & Previous Implementations

This project is part of a three-part Multi-Agent AI development series.

### Part 1: Multi-Agent Travel Planning System

**GitHub Repository:**  
[AI Travel Planning System using LangGraph](https://github.com/codewithaarohi/AI-Travel-Planning-System-using-LangGraph)

**Video Tutorial:**  
[Build a Real-World Multi-Agent AI System using LangGraph | Multi-Agent AI + Memory + APIs](https://youtu.be/ctHby5vhDqg)

### Part 2: Multi-Agent Travel Planning System with MCP

**GitHub Repository:**  
[AI Travel Planning App using LangGraph and MCP](https://github.com/codewithaarohi/AI-Travel-Planning-App-using-LangGraph-and-MCP)

**Video Tutorial:**  
[Build a Real-World Multi-Agent AI System using LangGraph | Multi-Agent AI + Memory + MCP](https://youtu.be/DjMX7o2EeV0)

### Part 3: Advanced Multi-Agent Architecture

This implementation introduces:

- Supervisor Agent for dynamic agent selection and orchestration.
- Input Guardrails for request validation and safety checks.
- Human-in-the-Loop for itinerary approval and modifications.
- Shared State Management for agent communication.
- Persistent Memory using PostgreSQL.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| Multi-Agent Architecture | Specialized agents handle individual travel planning tasks. |
| Supervisor Agent | Dynamically coordinates and manages agent execution. |
| Input Guardrails | Validates user requests and blocks invalid or irrelevant inputs. |
| Human-in-the-Loop | Allows users to review, approve, or request itinerary changes. |
| LangGraph Orchestration | Manages agent workflows and execution paths. |
| MCP Integration | Connects AI agents with external tools and services. |
| PostgreSQL Memory | Stores conversations and persistent workflow state. |
| Flight Search | Retrieves flight information through AviationStack MCP. |
| Web Search | Uses Tavily for travel research and information retrieval. |
| Weather Information | Retrieves weather forecasts through the Weather MCP Server. |
| Streamlit Interface | Provides an interactive travel planning experience. |

---

## 🏗️ Architecture Overview

The application follows a Supervisor-based Multi-Agent Architecture.

**Workflow:**

User Request → Input Guardrails → Supervisor Agent → Specialized AI Agents → Shared State → Human Approval → Final Response

### Specialized Agents

- **Flight Agent:** Searches flight information, routes, airlines, and fares.
- **Hotel Agent:** Searches hotels and compares prices and amenities.
- **Weather Agent:** Retrieves weather forecasts and climate information.
- **Budget Agent:** Analyzes estimated travel expenses and budget constraints.
- **Itinerary Agent:** Generates personalized day-wise travel plans.
- **Supervisor Agent:** Coordinates agents and manages workflow execution.

---

## 🛠️ Technology Stack & Dependencies

| Category | Technology |
|---|---|
| Programming Language | Python |
| Agent Framework | LangGraph |
| LLM Framework | LangChain |
| LLM Provider | Groq |
| Web Search | Tavily API |
| Flight Information | AviationStack API |
| Weather Information | OpenWeatherMap API |
| Tool Integration | Model Context Protocol (MCP) |
| Database | PostgreSQL |
| Persistent Memory | LangGraph Checkpointer |
| Frontend | Streamlit |

---

# 🚀 Installation & Setup Guide

Follow the steps below to configure the development environment and run the application locally.

## Prerequisites

Make sure the following tools are installed:

- Python 3.10 or later
- PostgreSQL
- Git
- Visual Studio Code (recommended)
- UV Package Manager

## Step 1: Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL

cd multi-agent-travel-planner
```

## Step 2: Create a Python Virtual Environment

```bash
python -m venv langgraph_env3
```

Activate the environment on Windows:

```powershell
langgraph_env3\Scripts\activate
```

## Step 3: Install Dependencies

Install the required Python packages:

```bash
pip install langgraph langchain langchain-openai langchain-groq langchain-community langchain-tavily psycopg[binary] psycopg_pool python-dotenv tavily-python requests streamlit
```

Install PostgreSQL checkpoint dependencies:

```bash
pip install -U "psycopg[binary,pool]" langgraph-checkpoint-postgres
```

## Step 4: Install and Configure PostgreSQL

Download PostgreSQL:

https://www.postgresql.org/download/

During installation, note your PostgreSQL username, password, and port number.

Create the application database:

```sql
CREATE DATABASE langgraph_memory_demo;
```

## Step 5: Configure Environment Variables

Create a `.env` file in the project root directory.

Add the following configuration:

```env
GROQ_API_KEY=your_groq_api_key

TAVILY_API_KEY=your_tavily_api_key

AVIATIONSTACK_API_KEY=your_aviationstack_api_key

DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost:5433/langgraph_memory_demo

OPENWEATHERMAP_API_KEY=your_openweathermap_api_key
```

**Important:**
- Replace placeholder values with your actual credentials.
- Update the PostgreSQL port according to your local configuration.
- Never commit your `.env` file or expose API keys in GitHub.

## Step 6: Generate Required API Keys

Configure the following external API services:

| Service | Purpose | API / Documentation |
|---|---|---|
| Groq | LLM inference | https://console.groq.com |
| Tavily | Web search | https://www.tavily.com/ |
| AviationStack | Flight information | https://aviationstack.com/ |
| OpenWeatherMap | Weather information | https://openweathermap.org/ |

---

# 🔌 MCP Server Configuration

The application uses MCP servers to provide external tool access to AI agents.

## Step 7: Configure AviationStack MCP Server

**MCP Repository:**

https://github.com/Pradumnasaraf/aviationstack-mcp

### 7.1 Clone the MCP Repository

Open PowerShell:

```powershell
E:

cd E:\Multi_agent_system_with_MCP

git clone https://github.com/Pradumnasaraf/aviationstack-mcp.git

cd aviationstack-mcp
```

### 7.2 Install UV Package Manager

Check whether UV is installed:

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

### 7.3 Configure AviationStack API Key

Create a `.env` file inside the AviationStack MCP project directory:

```env
AVIATION_STACK_API_KEY=your_aviationstack_api_key
```

### 7.4 Install MCP Dependencies

```bash
uv sync
```

This command creates the virtual environment and installs the project dependencies.

### 7.5 Activate the Virtual Environment

On Windows:

```powershell
.venv\Scripts\activate
```

### 7.6 Start the AviationStack MCP Server

```bash
uv run -m aviationstack_mcp mcp run
```

Alternatively:

```bash
python -m aviationstack_mcp mcp run
```

The MCP server will start and wait for incoming client requests.

**Note:** Keep the MCP server running while using the application.

To stop the server:

```bash
CTRL + C
```

---

## Step 8: Configure Weather MCP Server

Generate an API key from:

https://openweathermap.org/

Install the required dependencies:

```bash
pip install mcp requests
```

Configure the OpenWeatherMap API key in the application's `.env` file:

```env
OPENWEATHERMAP_API_KEY=your_openweathermap_api_key
```

Start the Weather MCP Server using the configured server entry point in the project.

---

# ▶️ Run the Application

## Step 9: Launch the Streamlit Web Application

From the project root directory, activate your Python environment and execute:

```bash
streamlit run frontend.py
```

Streamlit will start the web application and provide a local URL in the terminal.

Open the displayed URL in your browser to access the application.

---

## 💬 Example User Prompt

Try the following travel planning request:

```text
Plan a complete 7-day trip to Japan,
including flights, hotels, sightseeing,
and estimated expenses within a budget
of ₹2,00,000.
```

The Supervisor Agent will analyze the request and coordinate the relevant specialized agents to generate a travel plan.

---

## 🛡️ Guardrails & Human-in-the-Loop

### Input Guardrails

The system validates incoming user requests before starting the agent workflow.

It checks:

- Request relevance.
- Input validity.
- Safety and policy constraints.
- Travel planning requirements.

Invalid or unsupported requests are blocked before agent execution.

### Human-in-the-Loop

The generated travel itinerary is presented to the user for review.

Users can:

- Approve the generated itinerary.
- Request modifications.
- Trigger relevant agents again to update the travel plan.

This ensures better control, reliability, and user involvement in the final output.

---

## 🗄️ Memory & State Management

PostgreSQL is used for persistent memory and workflow checkpoint storage.

It enables the application to:

- Persist conversation history.
- Maintain workflow state.
- Store agent execution checkpoints.
- Support workflow continuation where configured.

---

## 📁 Project Features Summary

- Multi-Agent Architecture using LangGraph.
- Supervisor Agent for dynamic agent orchestration.
- Input Guardrails and request validation.
- Human-in-the-Loop approval workflow.
- PostgreSQL-based persistent memory.
- Tavily Search Integration.
- AviationStack MCP Integration.
- Weather MCP Integration.
- Shared State Management.
- Streamlit Web Application.
- External API Integration.
- Real-Time Travel Information (subject to API availability and provider limits).

---

## 🔮 Future Enhancements

- Docker-based application deployment.
- Kubernetes and Azure Kubernetes Service (AKS) integration.
- CI/CD automation using Azure DevOps.
- Infrastructure provisioning using Terraform.
- Application monitoring and observability.
- Advanced agent retry and failure-handling mechanisms.

---

## 👨‍💻 Author

**Vimlendu Shekhar Rai**

Generative AI Engineer | Azure | DevOps | Agentic AI | LangGraph | MCP | LLM | RAG | Kubernetes | Terraform

---

⭐ If you find this project useful, consider giving it a star!
