# 🔍 LLM-Powered RAG Pipeline 

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline using **LlamaIndex**, **OpenAI's GPT-3.5**, and **FAISS**, designed to allow real-time, grounded Q&A from uploaded documents (PDFs, TXT, DOCX). It runs entirely in **Google Colab**, with a future-ready path to a UI (Gradio, Streamlit, etc.).

---

## 🧠 What It Does

- Ingests your documents (e.g. resumes, legal docs, manuals)
- Parses and chunks them using `SimpleDirectoryReader`
- Converts text chunks to vector embeddings using `OpenAIEmbedding`
- Stores the embeddings in FAISS for high-speed retrieval
- Retrieves top-k relevant chunks per user query
- Feeds them into `gpt-3.5-turbo` to generate **grounded** answers
- Displays the response **along with source text snippets**

---

## 🧱 Architecture Overview

| Layer               | Component                        | Description                                                                 |
|--------------------|----------------------------------|-----------------------------------------------------------------------------|
| Document Parsing   | `SimpleDirectoryReader`          | Automatically extracts and chunks text from `.pdf`, `.txt`, `.docx` files  |
| Embedding          | `OpenAIEmbedding`                | Converts each chunk into a high-dimensional vector                         |
| Vector Store       | `FAISS`                          | Stores all embeddings in-memory and enables top-k similarity retrieval     |
| Index Construction | `VectorStoreIndex` (LlamaIndex)  | Maps document chunks → FAISS and connects them to the LLM orchestration    |
| Query Execution    | `GPT-3.5 Turbo`                  | Retrieves top-k chunks, constructs a prompt, and generates a grounded response |

---

Colab link: https://colab.research.google.com/drive/1HVmdv9OueWyUQdvS1D5H-Fqh3Yc6Zpcy?usp=sharing
