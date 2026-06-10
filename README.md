# AI Agents 💫

A curated collection of Jupyter notebooks exploring **design patterns for autonomous AI agents** using frameworks like Microsoft AutoGen, LangGraph, Taskweaver, CrewAI, and more.

---

## 📌 Overview

This repository demonstrates how to build, orchestrate, and compose intelligent agents capable of planning, reasoning, code execution, retrieval-augmented generation (RAG), and multi-agent collaboration. Each notebook is self-contained and focused on a specific pattern or use case.

---

## 🌟 Agent Architecture

![agent-overview](https://github.com/GURPREETKAURJETHRA/AI-Agents/blob/main/IMG/AgentOverview.png)

---

## 📁 Notebooks

### 1. 🔬 Multi-Agent Research Group Chat
**File:** `agentchat_groupchat_research.ipynb`

A multi-agent group chat where specialized agents — Admin, Engineer, Scientist, Planner, Executor, and Critic — collaborate to perform research tasks. Demonstrates the impact of a Critic agent on output quality by comparing results with and without it.

- **Task:** Find recent LLM papers on arXiv and organize them into a markdown table by domain
- **Framework:** AutoGen
- **Key agents:** `UserProxyAgent`, `AssistantAgent`, `GroupChatManager`

---

### 2. 📊 Data Analysis with Visualization Critic
**File:** `Autogen_Data_Analysis_Graphs.ipynb`

A group chat between a Coder agent and a Visualization Critic agent. The critic reviews generated plots and suggests improvements, which the coder implements — producing higher-quality visualizations iteratively.

- **Tasks:** Plot weight vs. horsepower from car data; visualize Seattle weather frequency
- **Framework:** AutoGen
- **Libraries:** `matplotlib`, `seaborn`, `pandas`
- **Key agents:** `UserProxyAgent`, Coder `AssistantAgent`, Critic `AssistantAgent`

---

### 3. 📚 Group Chat with Retrieval-Augmented Generation (RAG)
**File:** `Autogen_groupchat_RAG.ipynb`

Demonstrates how `RetrieveUserProxyAgent` overcomes the knowledge limitations of standard LLMs by grounding responses in provided documentation. Compares standard chat (incorrect output) vs. RAG-enabled chat (correct output) for tasks involving post-training API knowledge.

- **Framework:** AutoGen + ChromaDB
- **Use case:** Generate valid Spark API code using FLAML documentation
- **Key agents:** `RetrieveUserProxyAgent`, Boss, Boss_Assistant

---

### 4. 🗺️ Collaborative Planning with a Planner Agent
**File:** `Autogen_planning_with_Agents.ipynb`

Shows how an Assistant agent can consult a dedicated Planner agent before executing tasks. The Planner breaks down complex tasks into actionable steps without writing code itself, while the Assistant handles execution.

- **Task:** Suggest a fix for an open "good first issue" on the FLAML GitHub repo
- **Framework:** AutoGen
- **Pattern:** `ask_planner` function call between agents
- **Planner component:**

  ![plan-and-execute](https://github.com/GURPREETKAURJETHRA/AI-Agents/blob/main/IMG/PlanExecute.png)

---

### 5. 🦙 Local RAG Agent with LLaMA 3
**File:** `Local_RAG_Agent_LLAMA_3.ipynb`

An advanced, fully local RAG agent built with LangGraph that combines three research-backed RAG strategies:

| Strategy | Paper | Description |
|---|---|---|
| **Adaptive RAG** | [arXiv 2403.14403](https://arxiv.org/abs/2403.14403) | Routes questions to vectorstore or web search |
| **Corrective RAG** | [arXiv 2401.15884](https://arxiv.org/pdf/2401.15884.pdf) | Falls back to web search when docs are irrelevant |
| **Self-RAG** | [arXiv 2310.11511](https://arxiv.org/abs/2310.11511) | Self-corrects hallucinations and incomplete answers |

- **Framework:** LangGraph + LangChain
- **LLM:** LLaMA 3 (via Ollama — runs fully locally)
- **Embeddings:** GPT4All
- **Vector store:** Chroma
- **Web search:** Tavily
- **Pipeline stages:** Index → Retrieve → Grade → Generate → Hallucination check → Answer grading

---

## 🏗️ Agent Design Patterns Covered

| Pattern | Description |
|---|---|
| **Multi-Agent Group Chat** | Multiple specialized agents collaborate in a shared conversation |
| **Plan & Execute** | A Planner decomposes tasks; an Executor implements them |
| **RAG with Agents** | Agents retrieve and ground responses in external documents |
| **Critic/Reflection** | A Critic agent reviews outputs and triggers self-improvement |
| **Adaptive Routing** | An agent routes queries to the best retrieval strategy |
| **Self-Correction** | Agents detect and fix hallucinations in their own outputs |

---

## ⚙️ Setup & Installation

### Prerequisites
- Python 3.9+
- OpenAI API key (for AutoGen notebooks) **or** Ollama with LLaMA 3 (for local RAG notebook)

### AutoGen Notebooks
```bash
pip install pyautogen
pip install pyautogen[retrievechat]  # for RAG notebook
```

Configure your API key in `OAI_CONFIG_LIST`:
```json
[
  {
    "model": "gpt-4",
    "api_key": "<your OpenAI API key>"
  }
]
```

### Local RAG Notebook (LLaMA 3)
```bash
pip install langchain-nomic langchain_community tiktoken langchainhub \
            chromadb langchain langgraph tavily-python
```

Install and run Ollama with LLaMA 3:
```bash
ollama pull llama3
```

---

## 🖼️ Architecture Diagrams

**Taskweaver Design**

<img width="812" alt="taskweaver_arch" src="https://github.com/GURPREETKAURJETHRA/AI-Agents/blob/main/IMG/TaskweaverDesign.png">

> [Taskweaver GitHub →](https://github.com/microsoft/taskweaver/)

**AutoGen Agent Chat**

![autogen_agentchat](https://github.com/GURPREETKAURJETHRA/AI-Agents/blob/main/IMG/AutogenAgent.png)

**Multi-Agent Conversation**

<img width="1094" alt="chat_example" src="https://github.com/GURPREETKAURJETHRA/AI-Agents/blob/main/IMG/MultiAgentConversation.png">

**HuggingGPT Agent**

<img width="750" alt="hugging-gpt" src="https://github.com/GURPREETKAURJETHRA/AI-Agents/blob/main/IMG/HuugingGPTAgent.png">

---

## 📚 References & Further Reading

- [AutoGen Documentation](https://microsoft.github.io/autogen/)
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [Taskweaver by Microsoft](https://github.com/microsoft/taskweaver)
- [Adaptive RAG Paper](https://arxiv.org/abs/2403.14403)
- [Corrective RAG Paper](https://arxiv.org/pdf/2401.15884.pdf)
- [Self-RAG Paper](https://arxiv.org/abs/2310.11511)

---

---

> ⭐ If you find this repository helpful, please consider giving it a star!
