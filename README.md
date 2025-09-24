# 📄 RAG-PDF – Chat with Your Documents 🚀

RAG-PDF is a **Retrieval-Augmented Generation (RAG)** application built with **LangChain, FastAPI, and Streamlit** that lets you chat with the content of your PDF documents.  

It transforms dense, multi-page PDFs into an interactive conversational experience, providing:  
- 🧠 Accurate, context-aware answers  
- 🔗 Direct citations to the source page  
- 🗄️ Persistent chat history for multi-turn dialogue  
- ⚡ Ultra-fast responses powered by the **Groq API**  

Built for the **AlgorithmX AI Engineer Intern assessment**, this project demonstrates a clean, scalable architecture for building modern AI applications.

---

## 💡 Features

### 📄 PDF Ingestion Engine
- Uploads PDFs, parses their content, and indexes text chunks into a **Qdrant** vector store.

### 💬 Conversational AI Core
- Generates human-like answers **grounded only in the provided document context**.

### 🔗 Citation Generator
- Automatically includes **source and page number citations** with every response.

### 📜 Chat History Persistence
- Saves every conversation to a **PostgreSQL database**, enabling multi-turn, context-aware dialogue.

### ⚡ FastAPI Backend
- Manages the entire **RAG pipeline**, from PDF indexing to database interactions.

### 🖥️ Streamlit Dashboard
- Provides a clean, interactive **UI for uploading files, adjusting settings, and chatting**.

### 🧹 Stateless Sessions
- Automatically clears the vector store for each new session, ensuring a **fresh start** every time.

---

## 🧱 Tech Stack

| Technology            | Purpose                                                     |
|-----------------------|-------------------------------------------------------------|
| **Python**            | Core programming language                                   |
| **FastAPI**           | Backend to manage the RAG pipeline & database connections   |
| **Streamlit**         | Frontend dashboard for user interaction                     |
| **LangChain**         | Core framework for orchestrating the RAG chain              |
| **Groq API** (gemma2-9b-it) | High-speed Large Language Model for generation       |
| **Sentence-Transformers** | State-of-the-art text embedding models                 |
| **Qdrant**            | Persistent, high-performance vector database                |
| **PostgreSQL**        | Relational database for persistent chat history             |

---

## ⚙️ How It Works

1. **Upload & Index**: A user uploads a PDF through the Streamlit UI. The FastAPI backend processes it and stores embeddings in Qdrant.  
2. **User Query**: The user asks a question in the chat interface.  
3. **Retrieve**: The backend queries Qdrant to find the most relevant text chunks from the PDF.  
4. **Augment & Generate**: The question, chat history, and retrieved chunks are combined into a prompt and sent to the Groq LLM.  
5. **Respond & Cite**: The LLM generates an answer grounded in context, streamed back to the user with citations. Chat history is saved to PostgreSQL.  

### ➡️ Pipeline Flow
  User Upload → PDF Parser → Embedding Model → Qdrant → User Query → Retriever → LLM → Streamlit UI
