# Agentic RAG With LangGraph

**Agentic RAG With LangGraph** is a Python project that demonstrates how to build an **agentic system** using **Retrieval-Augmented Generation (RAG)** with **LangGraph** and **LangChain**. This system can autonomously decide when to retrieve relevant documents and generate informed answers using LLMs.

## Features

*   Stateful multi-actor workflows with **LangGraph**.
*   Retrieval-Augmented Generation (RAG) using **vector databases**.
*   Uses **OpenAI GPT-4** for generating high-quality answers.
*   Simple heuristic-based retrieval decision logic.
*   Supports testing with sample questions.

## Installation

1.  **Clone the repository**
    ```bash
    git clone https://github.com/AyorindeTayo/Agenticrag-Question-and-answer-.git
    cd Agenticrag-Question-and-answer-
    ```

2.  **Create a virtual environment**
    ```bash
    python -m venv autogen_env
    # Activate the environment
    # For Linux/macOS:
    source autogen_env/bin/activate
    # For Windows:
    # autogen_env\Scripts\activate
    ```

3.  **Install required packages**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up environment variables**
    Create a `.env` file in the root directory and add your OpenAI API key:
    ```env
    OPENAI_API_KEY=your_openai_api_key_here
    ```

## Usage

1.  **Run the main script**
    ```bash
    python src/main.py
    ```

2.  **Ask questions using the agent** (programmatically)
    ```python
    from src.main import ask_question

    question = "What is LangGraph?"
    result = ask_question(question)
    print(result['answer'])
    ```

## How It Works

### 1. State Definition
The system uses a state graph where each state is defined as:
```python
class AgentState(TypedDict):
    question: str
    documents: List[Document]
    answer: str
    needs_retrieval: bool
