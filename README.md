# 🔍 `rag_local_pdfs` 
### — Retrieval-Augmented Generation with Local PDFs

This project implements a **Retrieval-Augmented Generation (RAG)** system using **local PDF documents** as the knowledge base. Built with **LangChain**, **ChromaDB**, and a **local LLM via Ollama**, this setup enables question-answering over your own documents using efficient vector search and contextual responses from LLMs.

---
![Sample illustration, showing how data flow from source to Vector db to Response to the User](https://github.com/shekar369/rag_local_pdfs/blob/main/SImple_RAG.png)

![Sample illustration, showing how data flow from source to Vector db to Response to the User](https://github.com/shekar369/rag_local_pdfs/blob/main/Rag_original-chunks-embedding.png)

## Features

-  **PDF Loader**: Extracts text from PDF files in your local `data/` directory.
-  **Text Chunking**: Splits text into overlapping chunks using `RecursiveCharacterTextSplitter` to preserve context.
-  **Vector Store (ChromaDB)**: Stores and indexes embeddings for fast similarity search.
-  **Local LLM via Ollama**: Generates contextual answers using lightweight models like Mistral, all on your local machine.
-  **Testing Suite**: Validate system accuracy using test queries.

---

##  Project Structure

```
rag_local_pdfs/
│
├── data/                      # Local PDFs for ingestion
├── chroma/            # Local chroma directory will be added when we run populate_database.py
├── get_embedding_function.py  # Defines embedding logic
├── populate_database.py       # Loads, chunks, embeds, and stores PDFs
├── query_data.py              # Queries ChromaDB and returns LLM response
├── test_rag.py                # Test queries to validate responses
├── requirements.txt           # Python dependencies
└── README.md
```

## ⚙️ Setup Instructions
### 1. Clone the repository
```git clone https://github.com/your-username/rag_local_pdfs.git
cd rag_local_pdfs
```

### 2. Create virtual environment & install dependencies
```
python -m venv venv
source venv/bin/activate   # on Windows use venv\Scripts\activate
pip install -r requirements.txt
```
### 3. Add PDFs to data/ folder
Put your PDF files in the data/ directory for ingestion.

### 4. Install and run Ollama server. For running LLM Locally.
**Install Ollama from https://ollama.com, then run:**
Below step will download model
```
ollama run llama 3.2
```
Make sure Ollama is running in the background.

### 5. Populate the vector database
```
python populate_database.py
```
### 6. 🔍 Query your documents
```python query_data.py "What is the summary of the document?"```

### 7.  Run tests
```python test_rag.py```<br/><br/>

** Local LLM Support**
  
Uses Ollama for running models like:<br/>
-llama3.2<br/>
-gemma<br/>

Change model name in query_data.py if you prefer a different LLM.
  
## 📌 Future Enhancements<br/>
-GUI or Streamlit interface<br/>
-Multi-file PDF summarization<br/>
-Real-time chat over documents<br/>
-RAG + Agent framework (e.g., LangGraph or CrewAI)<br/>
