# 🦜🔗 LangGraph Workflow Patterns with Python

A collection of hands-on Jupyter Notebooks demonstrating core workflow patterns in [LangGraph](https://github.com/langchain-ai/langgraph) — from basic sequential pipelines to LLM-powered parallel evaluation systems.

---

## 📌 Overview

This repository is a practical guide for developers learning how to build stateful, graph-based AI workflows using LangGraph and LangChain. Each notebook is self-contained and walks through a specific workflow pattern with real working examples.

Whether you are just getting started with LangGraph or looking to understand how to chain LLM calls and run parallel evaluations, these notebooks have you covered.

---

## 📂 Repository Structure

```
├── langgraph_sequential_workflows.ipynb           # Basic sequential graph (BMI Calculator)
├── llm_based_langgraph_sequential_workflows.ipynb # LLM-powered sequential graph (Q&A)
├── prompt_chaining_langgraph_sequential_workflows.ipynb  # Prompt chaining (Blog Generator)
├── parallel_workflow_langgraph.ipynb              # Parallel graph (Cricket Stats Analyzer)
├── prallel_llm_based_workflow.ipynb               # Parallel LLM evaluation (UPSC Essay Scorer)
└── README.md
```

---

## 📓 Notebooks

### 1. `langgraph_sequential_workflows.ipynb` — Basic Sequential Graph
**Concept:** Introduction to LangGraph's `StateGraph` with simple node-to-node sequential flow.

**Example:** BMI Calculator — takes weight and height as input, calculates BMI, and then categorizes the result (Underweight / Normal / Overweight / Obese) in a multi-step pipeline.

**Key concepts covered:**
- Defining a typed state using `TypedDict`
- Adding nodes and edges to a `StateGraph`
- Compiling and invoking a workflow
- Visualizing the graph with Mermaid diagrams

---

### 2. `llm_based_langgraph_sequential_workflows.ipynb` — LLM-Powered Sequential Graph
**Concept:** Integrating an LLM (GPT-4o-mini via LangChain) into a LangGraph node for simple question-answering.

**Example:** A minimal Q&A workflow where a user question flows through a single LLM node that returns a structured answer.

**Key concepts covered:**
- Connecting `ChatOpenAI` inside a LangGraph node
- Passing prompts and extracting LLM responses within state
- Building the simplest possible LLM-backed graph

---

### 3. `prompt_chaining_langgraph_sequential_workflows.ipynb` — Prompt Chaining
**Concept:** Multi-step LLM pipelines where the output of one LLM call becomes the input for the next — a classic prompt chaining pattern.

**Example:** Blog Post Generator — first generates a detailed outline from a given topic, then writes a full blog post using that outline.

**Key concepts covered:**
- Chaining multiple LLM calls sequentially
- Carrying intermediate outputs (outline → content) through shared state
- Practical use of prompt engineering within a graph

---

### 4. `parallel_workflow_langgraph.ipynb` — Parallel Workflow (No LLM)
**Concept:** Running multiple independent nodes simultaneously from a single START node, then merging results into a final summary node.

**Example:** Cricket Batsman Stats Analyzer — given runs, balls, fours, and sixes, the graph concurrently computes Strike Rate, Balls Per Boundary, and Boundary Percentage, then summarizes all three.

**Key concepts covered:**
- Fan-out from `START` to multiple parallel nodes
- Fan-in from multiple nodes into a single aggregation node
- Understanding how LangGraph handles concurrent state updates

---

### 5. `prallel_llm_based_workflow.ipynb` — Parallel LLM Evaluation System
**Concept:** Running multiple LLM evaluators in parallel and aggregating their scores — a pattern commonly used in automated grading, essay scoring, and AI-based review pipelines.

**Example:** UPSC Essay Evaluator — an essay is evaluated simultaneously across three dimensions (Language Quality, Depth of Analysis, Clarity of Thought) by three independent LLM nodes. A final node computes the average score and consolidates all feedback.

**Key concepts covered:**
- Structured LLM output with Pydantic (`BaseModel` + `Field`)
- Using `Annotated` with `operator.add` to safely accumulate scores from parallel nodes without overwriting state
- Building a real-world multi-dimensional AI evaluation pipeline

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| [LangGraph](https://github.com/langchain-ai/langgraph) | Stateful graph-based workflow orchestration |
| [LangChain](https://github.com/langchain-ai/langchain) | LLM abstraction and prompt utilities |
| [LangChain OpenAI](https://pypi.org/project/langchain-openai/) | GPT-4o-mini integration |
| [Pydantic](https://docs.pydantic.dev/) | Structured LLM output schemas |
| Python `typing` | Type hints for state definitions |

---

## ⚙️ Setup & Installation

### Prerequisites
- Python 3.9 or higher
- An OpenAI API key

### Install Dependencies

```bash
pip install langgraph langchain langchain_openai pydantic
```

Or install notebook by notebook using the commented install cells at the top of each notebook:

```python
!pip install langgraph
!pip install langchain
!pip install langchain_openai
```

### Set Your API Key

Each LLM-based notebook prompts you securely at runtime:

```python
from getpass import getpass
OPENAI_API_KEY = getpass("Enter OPENAI API key")
import os
os.environ["OPENAI_API_KEY"] = OPENAI_API_KEY
```

Alternatively, you can set it as an environment variable before launching Jupyter:

```bash
export OPENAI_API_KEY="your-api-key-here"
```

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/langgraph-workflow-patterns.git
   cd langgraph-workflow-patterns
   ```

2. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

3. **Start with the basics** — open `langgraph_sequential_workflows.ipynb` first, then progress through the list above.

---

## 🧠 Learning Path

```
Beginner
    └── langgraph_sequential_workflows.ipynb          (No LLM — pure logic)
    └── llm_based_langgraph_sequential_workflows.ipynb (Single LLM node)
    └── prompt_chaining_langgraph_sequential_workflows.ipynb (Chained LLM calls)

Intermediate
    └── parallel_workflow_langgraph.ipynb             (Parallel nodes — no LLM)
    └── prallel_llm_based_workflow.ipynb              (Parallel LLM evaluation)
```

---

## 🤝 Contributing

Contributions are welcome! If you'd like to add a new workflow pattern, improve an existing notebook, or fix a bug:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/new-pattern`)
3. Commit your changes (`git commit -m 'Add new workflow pattern'`)
4. Push to the branch (`git push origin feature/new-pattern`)
5. Open a Pull Request

---

## 📄 License

This project is for educational and demonstration purposes. Feel free to fork and extend.
This project is for educational purposes. Feel free to use and adapt it for your own learning.

---

## ⭐ If you found this helpful

Give this repository a star ⭐ — it helps others discover it and motivates continued development!
