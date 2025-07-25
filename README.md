# 📄 Chat with Multiple PDFs using Ollama

This is a **Streamlit app** that lets you **chat with multiple PDF files** using **LLMs (Large Language Models)** like LLaMA via **Ollama**, backed by **FAISS vector search** and embeddings from `nomic-embed-text`.

> Upload any number of PDF files, ask questions, and get answers based on the actual content of those documents. No hallucination. No guesswork.

---
![Chat with PDFs Demo](images/pic.jpg)
##  Features

- 📄 Upload and process multiple PDFs at once.
- 🔍 Smart chunking of document text for better context.
- 📦 Automatic vector indexing using FAISS.
- 🧠 Conversational answering using Ollama LLMs.
- 🔄 Reusable sessions with unique vector store handling.
- ⚠️ Warns if no documents are processed before asking a question.

---

## 🧑‍💻 How It Works

### Step-by-Step:

1. **Upload PDFs:**
   - Use the sidebar to upload one or more PDF files.

2. **Process Files:**
   - Click the **"Submit & Process"** button.
   - The app reads, extracts text, splits it into meaningful chunks, and embeds it.

3. **Ask a Question:**
   - Enter a natural question (e.g., *"What is the main topic of these documents?"*).
   - The app will search relevant text chunks and respond with the most accurate answer using LLaMA via Ollama.

---

## ⚙️ Tech Stack

| Component      | Library/Tool             |
|----------------|--------------------------|
| UI             | [Streamlit](https://streamlit.io) |
| PDF Parsing    | `PyPDF2`                 |
| Text Splitting | `langchain.text_splitter` |
| Vector Store   | [FAISS](https://github.com/facebookresearch/faiss) |
| LLM            | [Ollama](https://ollama.com) (`llama3:8b`) |
| Embeddings     | `nomic-embed-text` via `OllamaEmbeddings` |
| Prompting      | LangChain `PromptTemplate` |
| Env Mgmt       | `python-dotenv`          |

---

## 📁 Folder Structure

When you upload and process PDFs, the app:
- Extracts and chunks text
- Stores a **unique FAISS index** based on a hash of filenames (e.g., `faiss_index_a4b3c1d3...`)
- Loads this vector store each time the question is asked

This ensures:
- 🧠 Document-specific memory
- ❌ No accidental overwrite
- 🔁 Efficient reloading between sessions

---

## ✅ Requirements

### 🐍 Python Packages

Install them via:

```bash
pip install -r requirements.txt

```

You’ll also need to have:

- [Ollama](https://ollama.com) installed and running locally

- The desired model (like `llama3:8b`) pulled via:
```bash
ollama pull llama3:8b
```
### ▶️ Run the App
```bash
streamlit run app.py
```
Replace `app.py` with your filename if different.

### 💡 Tips & Recommendations
- 📌 Default chunk size is 500 characters with 50 character overlap — works well for most text-heavy PDFs.

- ✅ Always process PDFs before asking questions.

- 💬 Use full-sentence questions for better accuracy (e.g., "What are the key findings in this document?").
### 📣 Credits
- Built with using LangChain, Ollama, and Streamlit

- Embeddings powered by nomic-embed-text

- Vector search via FAISS from Meta AI


