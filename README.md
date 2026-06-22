# llm-zoomcamp-hw2

LLM Zoomcamp 2026 Module 2 Homework - Vector Search and Hybrid Search

## Overview

This repository contains homework for Module 2 of the LLM Zoomcamp 2026 course. The focus is on implementing vector search using embeddings and combining it with text-based search for better results.

## Key Concepts

### Embeddings
- Converting text into vector representations using `SentenceTransformer` model (`all-MiniLM-L6-v2`)
- Embeddings capture semantic meaning - similar texts produce similar vectors
- Computing similarity between vectors using dot product

### Vector Search
- Building an in-memory vector search index using `minsearch.VectorSearch`
- Encoding query into a vector before searching
- Finding the most similar documents based on cosine similarity
- Exact nearest neighbor search - compares query against all documents

### Text Search
- Keyword-based search using `minsearch.Index`
- Searching for text matches in document content
- Good for finding exact keyword mentions

### Hybrid Search
- Combining results from both vector search and text search
- Using **Reciprocal Rank Fusion (RRF)** to merge and rank combined results
- RRF formula: `score = sum(1 / (k + rank))` where k is a constant (typically 60)
- Provides better overall search quality than either method alone

### Document Chunking
- Breaking longer documents into smaller overlapping chunks
- Using `gitsource.chunk_documents()` with configurable size and step
- Helps find more relevant passages within larger documents

## Repository Structure

- `homework-module2.ipynb` - Main homework notebook with practical examples
- `embedder.py` - Wrapper around SentenceTransformer for encoding text
- `download.py` - Data download and preparation utilities
- `main.py` - Main entry point
- `pyproject.toml` - Project dependencies
- `.python-version` - Python version specification (3.12.1)

## Technology Stack

- **Embedding Model**: Sentence Transformers (`all-MiniLM-L6-v2`)
- **Search Library**: minsearch (both vector and text search)
- **Data Processing**: gitsource (for loading GitHub repository documents)
- **Numeric Computing**: NumPy
- **Environment**: Python 3.12.1

## Getting Started

Install dependencies using uv:
```bash
uv sync
```

Run the homework notebook:
```bash
jupyter notebook homework-module2.ipynb
```

## Workflow

The homework demonstrates:

1. Loading markdown documents from a GitHub repository
2. Encoding documents and queries into vectors
3. Computing vector similarity scores
4. Building and querying a vector search index
5. Building and querying a text search index
6. Merging vector and text search results using RRF
7. Comparing results from different search methods

## Learning Outcomes

By completing this module, you will understand:
- How embeddings capture semantic meaning
- How to build and use vector search indexes
- How exact nearest neighbor search works
- How to combine multiple search methods for better results
- Trade-offs between vector search and keyword search
