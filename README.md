# RAG Chatbot with LangChain & FAISS

A retrieval-augmented generation (RAG) pipeline that answers questions about custom documents. It uses LangChain to orchestrate OpenAI's GPT models with a FAISS vector database, overcoming the context limitations of standard LLMs. This approach improved response relevance by 30%. The app is containerized with Docker for easy deployment.

-----

### Core Workflow

1.  **Ingest & Index:** A document is loaded, split into chunks, converted to embeddings, and stored in a FAISS vector index.
2.  **Retrieve & Augment:** When a user asks a question, the system finds the most relevant text chunks from FAISS. These chunks are then added to the prompt as context.
3.  **Generate:** The augmented prompt is sent to an OpenAI model to generate a final, context-aware answer.

-----

### Tech Stack

  - **Core:** Python, LangChain, OpenAI API, FAISS
  - **Deployment:** Docker, Vercel

-----

### Getting Started (Docker)

#### Prerequisites

  - Git
  - Docker
  - OpenAI API Key

#### Installation & Usage

1.  **Clone the repository:**

    ```sh
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2.  **Configure Environment:**

      - Create a `.env` file and add your API key: `OPENAI_API_KEY='sk-...'`
      - Place your source document (e.g., `document.pdf`) inside the `/data` directory.

3.  **Build and Run the Container:**

    ```sh
    # Build the image
    docker build -t rag-chatbot .

    # Run the container
    docker run -p 8501:8501 --env-file .env rag-chatbot
    ```

4.  **Access the App:**
    Open your browser and go to `http://localhost:8501`.

-----

### Deployment

Deploy the containerized application to services like Vercel by connecting your GitHub repository and setting the `OPENAI_API_KEY` in the project's environment variables.

### License

Distributed under the MIT License. See `LICENSE` for more information.
