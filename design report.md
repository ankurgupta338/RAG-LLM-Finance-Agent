## Design Report
Document Load --> Chunking into smaller chunks --> Storing in FAISS Vector Store --> Retrieval of top k documents --> reranking and selecting top n documents --> passing top n docs along with user query to LLM --> return response to user


### Why Vector Search First?
Vector search is:
- Sublinear time (ANN)
- Scales to millions of chunks
- Good recall mechanism
- It ensures we don’t scan the whole corpus.


### Why Retrieve top k (ex. 20) But Return top n (ex. 5)?

Dense retrieval prioritizes recall over precision.
- We retrieve 20 candidates (high recall)
- We rerank them for precision
- We return top-5
- We this improves answer faithfulnesst