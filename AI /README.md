# LLM’s

## Langchain

Framework for LLM’s

Why use langchain?

- Great for scalability
    - As our data or model gets bigger, langchain has memory module to provide context, no need to read all previous chats or entire chunks of data by token
- Great for indexing
    - Large chunks of texts,  how would you reead them? By word or by chunks of sentences
    - Use recursive character texts to split
- Provide proper context?
    - when data increases, our prompt gets more complicated

Indexes

- Process of structuring data so LLM’s can read it
- Embeddings - converts texts into numbers and store them into vectors
- Vector Store - store embeddings into a database designed for vectors
