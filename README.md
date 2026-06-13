# Conversational PDF RAG Assistant

A Retrieval-Augmented Generation (RAG) application that allows users to upload PDF documents and chat with them using natural language. The system maintains conversation history, understands follow-up questions, and retrieves relevant information from uploaded documents before generating responses.

## Features

- Upload multiple PDF documents
- Automatic document chunking
- Vector embeddings using HuggingFace MiniLM
- Semantic search with ChromaDB
- Conversational memory
- History-aware question reformulation
- Context-aware answers
- Streamlit user interface
- Groq LLM integration

---

## Architecture

```text
PDF Upload
    ↓
PDF Loader
    ↓
Document Chunking
    ↓
Embeddings Generation
    ↓
Chroma Vector Database

User Question
    ↓
Chat History
    ↓
History-Aware Retriever
    ↓
Question Reformulation
    ↓
Semantic Search
    ↓
Relevant Chunks
    ↓
LLM
    ↓
Final Answer
```

## Tech Stack

### Frontend
- Streamlit

### LLM
- Groq
- Llama 3.1 8B Instant

### Embeddings
- HuggingFace Embeddings
- all-MiniLM-L6-v2

### Vector Database
- ChromaDB

### Frameworks
- LangChain
- LangChain Community
- LangChain Chroma
- LangChain Groq

---

## How It Works

### 1. Document Processing

Uploaded PDF files are loaded using PyPDFLoader and converted into LangChain Document objects.

### 2. Text Chunking

Documents are split into smaller chunks using RecursiveCharacterTextSplitter.

```python
chunk_size = 5000
chunk_overlap = 500
```

### 3. Embedding Generation

Each chunk is converted into a dense vector representation using:

```python
all-MiniLM-L6-v2
```

### 4. Vector Storage

Embeddings are stored inside ChromaDB for semantic retrieval.

### 5. History-Aware Retrieval

The system uses chat history to rewrite ambiguous questions.

Example:

User:
```text
What is ASP.NET Core?
```

Follow-up:

```text
When was it released?
```

Rewritten to:

```text
When was ASP.NET Core released?
```

### 6. Retrieval-Augmented Generation

The retriever fetches the most relevant chunks from the vector database and injects them into the LLM prompt.

The LLM then generates a grounded answer based on document content.

---

## Installation

### Clone Repository

```bash
git clone <repository-url>
cd conversational-pdf-rag
```

### Create Virtual Environment

```bash
python -m venv venv
```

### Activate Environment

Windows:

```bash
venv\Scripts\activate
```

Linux/Mac:

```bash
source venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Environment Variables

Create a `.env` file:

```env
GROQ_API_KEY=your_groq_api_key
HF_Token=your_huggingface_token
```

---

## Run Application

```bash
streamlit run app.py
```

---

## Learning Outcomes

This project demonstrates:

- Retrieval-Augmented Generation (RAG)
- Vector Databases
- Semantic Search
- Embeddings
- Conversational AI
- LangChain Pipelines
- Chat Memory Management
- LLM Prompt Engineering
- Streamlit Application Development

---



Built by [Your Name]

Focused on Generative AI, RAG Systems, .NET Development, and Full-Stack Engineering.
