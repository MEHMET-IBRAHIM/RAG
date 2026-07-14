### PDF RAG Chatbot

A CLI-based chatbot that answers questions strictly from your PDF documents using Retrieval-Augmented Generation (RAG).

How It Works
PDF Documents → Chunking → Embeddings → ChromaDB
User Question → Embed Query → Retrieve Chunks → Groq LLM → Answer
PDFs are loaded, split into chunks, and embedded using all-MiniLM-L6-v2
Embeddings are stored in ChromaDB (local vector database)
User asks a question → most relevant chunks are retrieved
Groq LLM (llama-3.3-70b-versatile) answers strictly from retrieved context
If the answer is not in the PDFs, it returns "I don't know"


Tech Stack


LangChain — document loading, text splitting, prompt management
SentenceTransformers — text embeddings (all-MiniLM-L6-v2)
ChromaDB — local vector store
Groq — LLM inference (llama-3.3-70b-versatile)
PyMuPDF — PDF parsing


Setup
# Clone the repo
git clone https://github.com/A-bdullahamirr/pdf-rag-chatbot
cd pdf-rag-chatbot

# Install dependencies
uv sync

# Add your Groq API key
echo "GROQ_API_KEY=your_key_here" > .env
Usage


Add your PDF files to data/text_files/pdf/
Run the notebook notebook/document.ipynb cell by cell
Chat with your documents in the CLI
PDF Chatbot Ready. Type 'quit' to exit.

You: what is machine learning?
Bot: Machine Learning is a subset of AI where systems learn from data automatically...

You: quit
Project Structure:
pdf-rag-chatbot/
├── data/
│   ├── text_files/
│   │   └── pdf/        ← put your PDFs here
│   └── vector_store/   ← ChromaDB persisted here
├── notebook/
│   └── document.ipynb  ← main pipeline
├── .env                ← GROQ_API_KEY
├── .gitignore
└── README.md
Key Concepts Implemented


RAG Pipeline — retrieval-augmented generation from private documents
Semantic Search — vector similarity to find relevant chunks
Strict Grounding — LLM answers only from document context, no hallucination fallback

