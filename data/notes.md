# RAG Pipeline Notes

Quick reference notes on building a retrieval-augmented generation pipeline.

## Stages

1. **Load** — read raw files (PDF, CSV, TXT, MD) into `Document` objects.
2. **Split** — chunk long documents so they fit an embedding model's context window.
3. **Embed** — turn each chunk into a vector.
4. **Retrieve** — find the chunks most similar to a query.
5. **Generate** — pass retrieved chunks to an LLM as context.

## Things to watch for

- Chunk size and overlap change retrieval quality a lot.
- Always keep `source` metadata so answers can be traced back to a file.
- CSV rows and PDF pages need different chunking strategies than free text.

> A document loader's only job is step 1 — everything downstream assumes it produced clean, well-tagged `Document` objects.
