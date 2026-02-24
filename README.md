# LangChain for App Development (Groq Llama 3.1) — Notebooks (L1–L6)

Hands-on Jupyter notebooks covering core LangChain concepts for building LLM-powered applications, using **Groq** hosted models (primarily **`llama-3.1-8b-instant`**) and common LangChain building blocks: prompts, output parsers, memory, chains, retrieval/Q&A over documents, evaluation, and (token-conscious) agents.

This repository is structured as a **learning series**:
- Each lesson is provided as a **`.ipynb` notebook**
- Each notebook also has a corresponding **exported `.html`** version for easy viewing

---

## Contents / Lessons

| Lesson | Notebook | What it covers |
|---|---|---|
| L1 | `L1-Model_prompt_parser.ipynb` | Models, prompts, and output parsers; using Groq directly vs via LangChain |
| L2 | `L2-Memory.ipynb` | Conversation memory patterns (buffer, window, token buffer, summary) |
| L3 | `L3-Chains.ipynb` | LLMChain, sequential chains, router chains; composing workflows |
| L4 | `L4-QnA.ipynb` | Q&A over documents: loaders → embeddings → vector store → retrieval QA |
| L5 | `L5-Evaluation.ipynb` | Generating examples + manual/LLM-assisted evaluation; tracking results |
| L6 | `L6-Agents.ipynb` | **Token-efficient** approach to tools/agents; when to avoid heavy agents |

Exported HTML versions:
- `L1-Model_prompt_parser.html`
- `L2-Memory.html`
- `L3-Chains.html`
- `L4-QnA.html`
- `L5-Evaluation.html`
- `L6-Agents.html`

---

## Repository Structure (high level)

- `L1-Model_prompt_parser.ipynb` / `.html`
- `L2-Memory.ipynb` / `.html`
- `L3-Chains.ipynb` / `.html`
- `L4-QnA.ipynb` / `.html`
- `L5-Evaluation.ipynb` / `.html`
- `L6-Agents.ipynb` / `.html`
- `OutdoorClothingCatalog_1000.csv` — sample corpus used for retrieval/Q&A and evaluation
- `Data.csv` — additional sample data
- `evaluation_report.json` — example output artifact from evaluation work
- `LICENSE`

---

## Getting Started

### 1) Prerequisites
- Python 3.10+ recommended
- Jupyter Notebook or JupyterLab
- A **Groq API key** (set as `GROQ_API_KEY`)

### 2) Clone
```bash
git clone https://github.com/kateikyoushi/1_LangChain_for_AppDev.git
cd 1_LangChain_for_AppDev
```

### 3) Create a virtual environment (recommended)
```bash
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

### 4) Install dependencies
These notebooks often install dependencies inside cells (via `!pip install ...`), but for a smoother experience you can install them up-front:

```bash
pip install -U pip
pip install langchain langchain-groq python-dotenv pandas docarray sentence-transformers jupyter
```

> Some lessons use community modules like `langchain_community` and embeddings/vector store integrations.

### 5) Configure environment variables
Create a `.env` file in the repository root:

```bash
GROQ_API_KEY=your_groq_api_key_here
```

The notebooks use `python-dotenv` (`load_dotenv(find_dotenv())`) to load this.

### 6) Launch Jupyter
```bash
jupyter lab
# or
jupyter notebook
```

Open any of the `L*.ipynb` notebooks and run cells in order.

---

## Notes on LangChain Versions / Imports

At least one notebook prints a LangChain version like `1.2.8` and includes import checks. LangChain changes APIs over time, so if you hit an error such as:

- `No module named 'langchain.chains'`

it usually indicates an **API move / version mismatch**. Fix options:
- Upgrade LangChain and related packages:
  ```bash
  pip install -U langchain langchain-community langchain-groq
  ```
- Or adjust imports in the notebook to match the installed version.

If you want, open an issue with the exact traceback + your `pip freeze` and we can pin a known-good dependency set.

---

## Data Files

### `OutdoorClothingCatalog_1000.csv`
Used as a sample “document” dataset for:
- loading documents (CSV loader)
- embeddings (HuggingFace / sentence-transformers)
- vector search (in-memory / DocArray)
- retrieval-augmented generation (RAG) Q&A

### `evaluation_report.json`
An example artifact representing evaluation results generated during evaluation workflows.

---

## How to View Without Running Notebooks

If you only want to read the lessons:
- Open the corresponding **`.html`** files directly in GitHub, or
- Download and open them locally in a browser.

---

## Security / API Keys

Do **not** commit real API keys. Use:
- `.env` (local only)
- GitHub Secrets (for CI, if you add workflows later)

---

## License

See [`LICENSE`](LICENSE).

---

## Acknowledgements

This repo is organized as a lesson series inspired by common LangChain learning paths, adapted to run with **Groq Llama 3.1**.

---

## Next Improvements (optional)

If you'd like, I can help add:
- `requirements.txt` or `pyproject.toml` with pinned versions known to work
- a `.gitignore` for `.env`, `.venv`, notebook checkpoints
- a small `Makefile` or `justfile` for setup commands
- badges + a table-of-contents + screenshots
