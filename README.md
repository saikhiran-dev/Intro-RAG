### Intro RAG

A small Python project for experimenting with Retrieval-Augmented Generation (RAG) using local document data.

## Prerequisites

- Python 3.11. (supports all libraries. latest version doesn't have full support yet)
- uv (instead of pip)
- Windows OS (this workspace has been tested on Windows).

## Setup Instructions

1. Open a terminal in the project root.
2. Create and activate a virtual environment if not already active:

   I have used uv - you can use  [ pip install uv ] to install directly in vs code.

   ```
   1. uv init
   2. uv venv
   3: .venv\Scripts\Activate
   ```

3. Install the required Python dependencies:
  
   uv add -r requirements.txt
   ```

4. If your code or notebooks require PyTorch, install the pinned PyTorch packages separately:

   ```
   uv pip install torch==2.8.0 torchvision==0.23.0 torchaudio==2.8.0
   ```

## Development Notes

- The project dependencies are managed in `pyproject.toml` and declared in `requirements.txt`.
- The notebooks under `notebook/` are for exploring PDF loading and text embedding workflows.

## Data Files

- Pace source PDFs into `data/pdf/`.
- Place plain text files into `data/text_files/`.
- When building a RAG pipeline, use these files as the corpus for document loading, embedding creation, and retrieval.

## Common Errors and Fixes

### 1. Virtual environment not activated

Error:

```text
ModuleNotFoundError: No module named 'langchain'
```

Fix:

- Activate the `.venv` environment before installing or running code.
- Use `uv add -r requirements.txt` inside the active environment.

### 2. PyTorch installation issues

Error:

```text
No module named 'torch'
``` 
or package version conflicts during install.

Fix:

- Install the specific versions used in this workspace:

  ```powershell
  pip install torch==2.8.0 torchvision==0.23.0 torchaudio==2.8.0
  ```

### 3. FAISS import or installation problems

Error:

```text
ImportError: No module named 'faiss'
``` 
or `faiss-cpu` fails to install.

Fix:

- Make sure `faiss-cpu` is installed in the active environment.
- On Windows, use the wheel available for your Python version or install via:

  ```powershell
  uv pip install faiss-cpu
  ```

### 4. LangChain version mismatches

Error:

```text
ImportError: cannot import name 'SomeClass' from 'langchain'
``` 
or unexpected API changes.

Fix:

- Use the versions specified in `pyproject.toml`.
- If upgrading or changing dependencies, ensure `langchain`, `langchain-core`, and `langchain-community` are compatible.

### 5. PDF loading errors

Error:

```text
ValueError: cannot read PDF file```

Fix:

- Install `pymupdf` and `pypdf` into the active environment.
- Confirm the PDF file is valid and not password protected.


