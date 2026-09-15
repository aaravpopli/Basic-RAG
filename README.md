# Basic RAG Research Assistant

A simple Streamlit application that lets you ask questions about research papers using retrieval augmented generation (RAG).

The app loads PDF files from `research_papers/`, splits their text into chunks, creates local Hugging Face embeddings, stores them in a FAISS vector index, and uses Groq to generate an answer from the most relevant passages.

## Features

- Load multiple research papers in PDF format
- Search paper content with semantic similarity
- Generate answers using Groq
- Display the retrieved document passages for verification
- Run locally with Streamlit

## Project structure

```text
.
├── app.py
├── requirements.txt
├── research_papers/
│   ├── Attention.pdf
│   └── LLM.pdf
└── .env                 # local only; do not upload
```

## Setup

Create and activate a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Create a `.env` file in the project folder and add your Groq API key:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Never commit or share the `.env` file. It is excluded by `.gitignore`.

## Run the app

```bash
streamlit run app.py
```

Open the local URL shown in the terminal, click **Document embeddings**, and then enter a question about the papers.

## GitHub upload

```bash
git init -b main
git add app.py requirements.txt README.md .gitignore research_papers
git commit -m "Add basic RAG research assistant"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

Replace `YOUR_USERNAME` and `YOUR_REPOSITORY` with your GitHub details.

## Notes

- The first embedding run may download the Hugging Face model `sentence-transformers/all-MiniLM-L6-v2`.
- The Groq model configured in `app.py` is `openai/gpt-oss-120b`.
- Answers depend on the text extracted from the PDFs and should be checked against the displayed source passages.
