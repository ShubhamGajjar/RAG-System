# RAG-System: FastAPI, React, and Vercel

This project is a Retrieval-Augmented Generation (RAG) system that allows users to upload documents and ask questions about their content. It's built with a FastAPI backend, a React frontend, and is designed for deployment on Vercel's serverless platform.

## ✨ Features

- **Document Upload:** Supports PDF, DOCX, and TXT file uploads.
- **Semantic Search:** Uses a vector database for efficient, meaning-based search.
- **LLM Integration:** Powered by Gemini (or other user-selected models) for generating answers.
- **Model Customization:** Allows users to select the LLM and adjust settings like temperature.
- **Serverless-Optimized:** Built with Vercel's free-tier limitations in mind.

## 🛠️ Tech Stack

- **Backend:** FastAPI, LangChain, Python
- **Frontend:** React, Vite, TypeScript
- **Vector Database:** FAISS (for local development), with plans for a managed service like Pinecone or Weaviate for production.
- **Orchestration & Monitoring:** LangFlow, LangFuse
- **Deployment:** Vercel

## 🚀 Getting Started

### Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Node.js](https://nodejs.org/) (v18 or later)
- [Python](https://www.python.org/downloads/) (v3.10 or later)

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/<your-username>/RAG-System.git
    cd RAG-System
    ```

2.  **Run with Docker:**
    ```bash
    docker-compose up --build
    ```
    - The frontend will be available at `http://localhost:3000`.
    - The backend will be available at `http://localhost:8000`.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
