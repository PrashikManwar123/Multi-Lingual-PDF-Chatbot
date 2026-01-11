# Multi-Lingual-PDF-Chatbot

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![LangChain](https://img.shields.io/badge/LangChain-0.1-green)
![Ollama](https://img.shields.io/badge/Ollama-Local%20LLM-orange)

A Retrieval-Augmented Generation (RAG) pipeline designed to chat with PDF documents entirely locally. This project utilizes **Ollama** for the LLM and Embeddings, **ChromaDB** for vector storage, and a robust **Hybrid Text Extraction** system that handles both standard and scanned (image-based) PDFs.

## 🚀 Key Features

- **100% Local Privacy:** Uses local LLMs (Llama 3.2) and Embeddings (Nomic) via Ollama. No data leaves your machine.
- **Hybrid PDF Parsing:**
  - Attempts fast direct text extraction first (using `PyMuPDF`).
  - Automatically falls back to **OCR (Tesseract)** if the document is scanned or has low text density (< 100 words).
- **Multi-Language OCR Support:** Pre-configured to support English, Hindi, Urdu, Bengali, Marathi, and Chinese (Sim).
- **Advanced Retrieval:** Implements LangChain's `MultiQueryRetriever`, which generates multiple perspectives of a user's question to find better context matches.
- **Interactive Notebook:** Built as a Jupyter Notebook for easy experimentation and visualization.

## 🛠️ Prerequisites

Before running the notebook, you need the following installed on your system.

### 1. System Dependencies (Linux / Colab)

The notebook relies on `tesseract-ocr` for image processing and `poppler` for PDF conversion.

```bash
sudo apt-get update
sudo apt-get install -y tesseract-ocr poppler-utils libpci3
```bash

```bash
# Install specific language packs for OCR
sudo apt-get install -y \
  tesseract-ocr-hin \
  tesseract-ocr-urd \
  tesseract-ocr-ben \
  tesseract-ocr-eng \
  tesseract-ocr-mar \
  tesseract-ocr-chi-sim
```bash

## 2. Ollama

You must have Ollama installed and running.

Install Ollama, then pull the required models used in this notebook:

```bash
ollama pull llama3.2
ollama pull nomic-embed-text
