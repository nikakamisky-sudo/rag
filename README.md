# RAG Prototype: Question Answering over Lecture Notes

A small Retrieval-Augmented Generation (RAG) prototype in Python. It answers questions about "Was ist Analysis?" by Mathe-für-nicht-Freaks by retrieving the most relevant passages and letting an LLM answer only from them.

## How it works
1. **Chunking**: text is split into overlapping chunks (configurable size and overlap).
2. **Embeddings**: multilingual Sentence-Transformers model (`paraphrase-multilingual-MiniLM-L12-v2`), run locally.
3. **Retrieval**: cosine similarity (NumPy) selects the top-k chunks. No vector database.
4. **Generation**: Gemini API answers only from the retrieved context, or says the answer is not in the notes.

## Setup
```
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
```
Create a `.env` file with `GEMINI_API_KEY=your_key_here` (see `.env.example`), then run `rag math.ipynb` top to bottom.

## What I tested
Tested two questions: 
1. **What can you do in Algebra?**(Answer was in the text) Model gave a correct answer.
2. **What is an eigenvalue in Linear Algebra?**(Answer wasn't in the text)
Model said that this wasn't written in text
