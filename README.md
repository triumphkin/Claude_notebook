📄 RAG Chatbot: Chat with your PDFs using Gemini & LangChain

An end-to-end Retrieval-Augmented Generation (RAG) application that allows users to upload PDF documents and ask questions about their content. Built with modern LangChain Expression Language (LCEL), powered by Google's Gemini API, and featuring a clean web UI using Gradio.
✨ Features

    Document Ingestion: Upload any standard PDF document directly through the web interface.

    Smart Context Chunking: Uses RecursiveCharacterTextSplitter to break down large PDFs into highly relevant, digestible segments for the AI.

    Vector Database: Utilizes ChromaDB to store and quickly retrieve document embeddings.

    Modern LangChain Architecture: Built using LCEL (LangChain Expression Language) for a fast, readable, and highly customizable data pipeline.

    Rich Markdown Output: The LLM responses are formatted in beautiful, readable Markdown (lists, headers, bold text) right in the UI.

🛠️ Technology Stack

    LLM: Google Gemini 2.5 Flash (gemini-2.5-flash)

    Embeddings: Google Gemini Embeddings (gemini-embedding-2-preview)

    Framework: LangChain

    Vector Store: Chroma

    Frontend UI: Gradio

🚀 Getting Started
1. Prerequisites

Ensure you have Python 3.9+ installed on your machine. You will also need a free Google Gemini API key.

    Get your API key here: Google AI Studio

2. Installation

Clone the repository and install the required dependencies:
Bash

git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

# Install the required Python packages
pip install langchain langchain-google-genai langchain-community langchain-text-splitters chromadb pypdf gradio python-dotenv google-genai

3. Environment Variables

Create a .env file in the root directory of the project and add your Google API key:
Code snippet

GOOGLE_API_KEY="your_api_key_here"

💻 Usage

If you are running this inside a Jupyter Notebook (.ipynb):

    Run all the cells in order.

    The final cell will launch a local Gradio server.

    Click the local URL provided (usually http://127.0.0.1:7861) to open the web app.

    Upload a PDF, type your question, and hit submit!

The RAG Pipeline Explained

    document_loader(file): Reads the uploaded PDF and extracts the raw text.

    text_splitter(data): Chunks the text into segments of 420 characters with a 50-character overlap to preserve context between chunks.

    vc_db(chunks): Converts the text chunks into mathematical vectors using Gemini Embeddings and stores them in a local Chroma vector database.

    retriever_qa(file, query): Takes the user's question, searches ChromaDB for the most relevant chunks, and pipes both the context and the question into the Gemini 2.5 Flash model to generate a highly accurate answer.

⚠️ Troubleshooting

Error: When localhost is not accessible, a shareable link must be created...
If you are repeatedly running the notebook cells and encounter a Gradio server error on port 7861, it means the previous web server instance is still running in the background.

Fix: Run the provided close command in a new cell before launching again:
Python

rag_application.close()

Alternatively, you can restart your Jupyter kernel, or update your launch command to bypass the localhost check by generating a public link:
Python

rag_application.launch(share=True)
