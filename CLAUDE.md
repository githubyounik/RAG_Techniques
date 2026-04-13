# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is an educational repository showcasing advanced Retrieval-Augmented Generation (RAG) techniques. Each technique is implemented as a Jupyter notebook in `all_rag_techniques/` and often has a corresponding standalone Python script in `all_rag_techniques_runnable_scripts/`.

## Setup and Dependencies

There is no `requirements.txt` checked in currently (CI installs one if present). To set up locally, install packages used across notebooks:

```bash
pip install langchain langchain-openai langchain-community langchain-core langchain-text-splitters \
    faiss-cpu openai python-dotenv nbformat rank-bm25 pymupdf deepeval
```

Set `OPENAI_API_KEY` in your environment or a `.env` file — the notebooks load it via `python-dotenv`.

## Running Tests

```bash
# Run all tests
pytest

# Run tests excluding specific notebooks or scripts
pytest --exclude=all_rag_techniques/some_notebook.ipynb,all_rag_techniques_runnable_scripts/some_script.py

# Run a specific test
pytest tests/test_imports.py::test_notebook_imports
pytest tests/test_imports.py::test_script_imports
```

Tests do **not** execute notebooks end-to-end. They only extract and validate that every `import` statement in each notebook (`all_rag_techniques/`) and runnable script (`all_rag_techniques_runnable_scripts/`) can be executed successfully. CI runs with a dummy `OPENAI_API_KEY="123"`, so tests must not make real API calls.

## Repository Structure

```
all_rag_techniques/          # Jupyter notebooks — one per technique
all_rag_techniques_runnable_scripts/  # Standalone .py equivalents of the notebooks
evaluation/                  # evalute_rag.py: deepeval-based RAG evaluation harness
helper_functions.py          # Shared utilities used across notebooks and scripts
data/                        # Sample input documents (e.g., Nike annual report)
images/                      # SVG diagrams embedded in notebooks
tests/
  conftest.py                # pytest fixtures (llm, embeddings, vector_store, etc.)
  test_imports.py            # Import-validation tests for notebooks and scripts
```

## Shared Utilities (`helper_functions.py`)

All techniques import from this module. Key functions:

- `encode_pdf(path)` / `encode_from_string(content)` — chunk and embed content into a FAISS vector store
- `retrieve_context_per_question(question, retriever)` — fetch relevant chunks
- `create_question_answer_from_context_chain(llm)` / `answer_question_from_context(...)` — LangChain chain for Q&A
- `bm25_retrieval(bm25, cleaned_texts, query)` — keyword-based retrieval
- `get_langchain_embedding_provider(provider, model_id)` — multi-provider embedding factory (OpenAI, Cohere, Bedrock)
- `retry_with_exponential_backoff(coroutine)` — async retry on `RateLimitError`

## Adding a New RAG Technique

1. Create a notebook in `all_rag_techniques/` following this structure: title/overview → explanation → Mermaid diagram (saved as SVG in `images/`) → implementation → usage example → comparison with basic RAG.
2. Optionally add a runnable script in `all_rag_techniques_runnable_scripts/`.
3. Update **both** the numbered list and the techniques table in `README.md`. Numbers must match in both places; renumber all subsequent techniques if inserting mid-list.
4. Each code cell in a notebook must be preceded by a markdown cell describing it; clear outputs before committing.

## CI

GitHub Actions (`.github/workflows/github-test.yml`) triggers on PRs to `main` that touch `requirements.txt`, installs dependencies, and runs `pytest` with Python 3.12.6.
