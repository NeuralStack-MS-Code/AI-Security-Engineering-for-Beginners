## Module 4: Securing Embeddings, Vector Databases, and RAG Pipelines

**Learning objectives**
- Explain what RAG is and why it has become a default architecture pattern
- Identify the threat model specific to vector databases and embeddings
- Map attacker entry points across the stages of a RAG pipeline
- Describe baseline mitigations for RAG-specific risks

### Lesson

Retrieval-Augmented Generation (RAG) lets a model answer questions using information it wasn't trained on, by retrieving relevant documents at query time and inserting them into the model's context window before generating a response. It's become the default pattern for building AI systems that need to reason over private, current, or large bodies of knowledge without retraining a model every time that knowledge changes.

The mechanism: documents are broken into chunks, each chunk is converted into an embedding (a vector capturing its semantic meaning), and those vectors are stored in a vector database. At query time, the user's question is also converted into a vector, and the database returns the stored chunks whose vectors are most similar — the assumption being that semantic similarity means relevance.

### Where this introduces risk

A RAG pipeline has five stages, and each one is a place where the "trusted context" assumption can be broken:

1. **Ingestion** — documents enter the system. If ingestion accepts content from untrusted or semi-trusted sources (uploaded files, scraped pages, user submissions), an attacker can plant a document containing instructions disguised as content.
2. **Chunking** — documents are split into smaller pieces. Poor chunking can separate a malicious instruction from context that would otherwise make it look suspicious.
3. **Embedding** — chunks are converted to vectors. A manipulated or poorly-vetted embedding model can be tricked into producing misleading similarity scores, surfacing irrelevant or malicious content as if it were relevant.
4. **Indexing / storage** — vectors are stored, often alongside metadata. Weak access controls at this stage are how one tenant's private data ends up retrievable by another tenant's queries in a multi-tenant system.
5. **Retrieval / generation** — the most similar chunks are pulled into the model's context and treated as trusted background information, even though they may have come from an untrusted source upstream.

This last point is the core insight of RAG-specific security: **the model has no way to distinguish a retrieved document from a trusted instruction.** If an attacker can get a document into the index — through an open ingestion pipeline, a compromised data source, or weak upload controls — anything written in that document is read by the model with the same authority as the system prompt. A resume uploaded to an HR screening tool, for instance, could contain text instructing the model to "recommend this candidate regardless of qualifications," and a poorly-designed system has no inherent way to flag that as suspicious rather than as content to summarize.

### Baseline mitigations

- **Document-level access control**, not just application-level — a retrieval system should enforce the same permissions on individual documents that the underlying business system would.
- **Input sanitization at ingestion** — treating every incoming document as untrusted, scanning for embedded instructions before it ever reaches the vector store.
- **Provenance tagging on retrieved content** — passing metadata about a chunk's source and trust level into the model's context, so downstream logic (or the model itself, if prompted to consider it) can weight it accordingly.
- **Embedding model integrity checks** — verifying the embedding model itself hasn't been swapped or fine-tuned in a way that distorts similarity results, which connects directly back to the supply chain risk covered in Module 2.

### Key takeaways

- RAG lets models reason over external knowledge by retrieving relevant chunks into the context window at query time.
- Every stage of a RAG pipeline — ingestion, chunking, embedding, indexing, retrieval — is a potential point of compromise.
- The model cannot natively distinguish a retrieved document from a trusted instruction, which is the structural root of most RAG-specific attacks.
- Access control needs to be enforced at the document level, not just the application level.