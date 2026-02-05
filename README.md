# rag-candidate-analyzer
This project demonstrates a Retrieval-Augmented Generation (RAG) system designed to analyze unstructured candidate profiles and support decision-making in data science and AI recruitment.
## System Architecture

```mermaid
flowchart LR
  U[User / Analyst] -->|Question| Q[Query Handler]

  subgraph Ingestion["Ingestion Pipeline"]
    D[Raw Docs] --> S[Text Splitter]
    S --> E[Embedding Model]
    E --> V[(Chroma Vector DB)]
  end

  subgraph Retrieval["Retrieval + Generation"]
    Q --> EQ[Embed Query]
    EQ --> R[Retriever]
    R --> C[Context Builder]
    C --> P[Controlled Prompt]
    P --> L[LLM]
    L --> A[Answer]
  end

  V --> R
  A --> U
