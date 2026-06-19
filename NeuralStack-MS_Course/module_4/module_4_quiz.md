### Module 4 Quiz

1. What is the core mechanism behind RAG?
   a) Retraining the model on new data every time it's queried
   b) Retrieving semantically similar document chunks and inserting them into the context window at query time
   c) Storing the entire internet inside the model's weights
   d) Encrypting all user queries before processing

2. Why can RAG pipelines be exploited even if the underlying model is secure?
   a) The model cannot distinguish a retrieved document from a trusted instruction
   b) RAG pipelines never use embeddings
   c) Vector databases are immune to access control issues
   d) RAG systems don't process untrusted content

3. Which RAG stage is most directly responsible for cross-tenant data exposure in multi-tenant systems?
   a) Chunking
   b) Indexing / storage, when access controls are weak
   c) Embedding model training
   d) User authentication only

4. What is "provenance tagging" in the context of RAG security?
   a) Encrypting the vector database
   b) Passing metadata about a chunk's source and trust level alongside retrieved content
   c) Deleting all documents older than 30 days
   d) A method for compressing embeddings

5. Embedding model integrity checks are connected to which other OWASP risk category from Module 2?
   a) LLM09 — Misinformation
   b) LLM03 — Supply Chain
   c) LLM07 — System Prompt Leakage
   d) LLM10 — Unbounded Consumption

**Answer key:** 1-b, 2-a, 3-b, 4-b, 5-b
