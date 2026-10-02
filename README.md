# Email Agent

An LLM-powered agent that manages emails via natural-language requests, using
[aisuite](https://github.com/andrewyng/aisuite) with Groq (`openai/gpt-oss-20b`)
for function-calling over a small FastAPI + SQLite email backend.

## Features

- Natural-language requests mapped to tool calls (list, list unread, search).
- FastAPI service backed by SQLite for email storage.
- Evaluation harness that tracks actual tool invocations per request and
  checks them against expected tools, catching tool-selection regressions.

## Setup

```bash
pip install -r requirements.txt
```

Create a `.env` file in the project root:

```
GROQ_API_KEY=your_key_here
```

## Usage

Run the agent directly:

```bash
python agent.py
```

Run the evaluation suite:

```bash
python -m evaluation.evaluator
```

Run the FastAPI backend:

```bash
uvicorn app.main:app --reload
```

## Project Structure

```
agent.py           # Agent entrypoint, tool tracking, Groq compatibility patch
app/                # FastAPI app, models, schemas, DB seeding
tools/              # Email tool functions exposed to the LLM
evaluation/         # Test cases and evaluation harness
```
