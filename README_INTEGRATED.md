## Integrated RAG Pipeline (Basic + Sentence-Window + Auto-Merging)

This repo originally has 3 notebooks. This script runs the same three strategies back-to-back and prints the answers and top sources.

### Setup
1. Install Python deps:
   - `pip install -r requirements.txt`
2. Set your OpenAI key (pick ONE):
   - Option A (recommended): create a `.env` file
     - Copy `.env.example` to `.env`
     - Put your key in `.env` as `OPENAI_API_KEY=...`
   - Option B: set `OPENAI_API_KEY` environment variable
   - Option C: pass `--openai-api-key` to the script

### Run
- Basic default (uses `data/Henry.txt` shipped as a sample):
  - `python integrated_rag_pipeline.py --query "Who is the beautiful person in Hong Kong?"`

- Use your own knowledge file:
  - `python integrated_rag_pipeline.py --input-file "path/to/your.txt" --query "your question"`

- Enable persistence (faster on reruns; uses `--cache-dir`):
  - `python integrated_rag_pipeline.py --persist --cache-dir ".rag_cache"`

### Notes
- The sentence-window and auto-merging retrieval steps use local embedding and reranking models:
  - embeddings: `local:BAAI/bge-small-en-v1.5`
  - reranker: `BAAI/bge-reranker-base`
  These may require downloading models on first run.

