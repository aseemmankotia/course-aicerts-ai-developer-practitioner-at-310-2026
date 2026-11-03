# Domain 10 Cheat Sheet: RAG and Knowledge Assistants

## RAG Pipeline (Retrieve → Augment → Generate)
| Step | What Happens | Key Tool |
|---|---|---|
| Retrieve | Embed query, search vector store for top-k similar chunks | FAISS, Chroma |
| Augment | Insert retrieved chunks + query into the prompt | Prompt template |
| Generate | LLM produces answer grounded in the augmented prompt | LLM |

**Exam note:** Questions often ask which stage a described action belongs to — know the boundaries between retrieve/augment/generate.

## Embeddings & Similarity Search
- Embeddings convert text into dense numeric vectors capturing semantic meaning.
- **Cosine similarity** range: **-1 to 1** (1 = identical, 0 = unrelated, -1 = opposite).
- Formula: `cos_sim(A,B) = (A·B) / (||A|| * ||B||)`
- Vector stores (FAISS, Chroma) index embeddings for fast nearest-neighbor lookup.

## Embedding Search vs Keyword Search
| Aspect | Embedding Search | Keyword/BM25 Search |
|---|---|---|
| Matches | Semantic meaning (synonyms, paraphrase) | Exact/overlapping terms |
| Fails when | — | Query wording differs from document wording |
| Strength | Finds conceptually related content | Finds exact identifiers, codes, rare terms |

**Common mistake:** Choosing keyword search for a scenario describing synonym/paraphrase matching — exam wants embedding-based similarity search.

## Chunking Strategy
- **Chunk size:** too large → diluted embeddings, low precision. Too small → lost context.
- **Typical range:** ~300-1000 tokens per chunk (varies by document type).
- **Overlap:** 10-20% between adjacent chunks prevents content split at boundaries (e.g., multi-step procedures) from being lost.
- Chunk by logical boundaries (paragraphs, sections) when possible rather than arbitrary token cuts.

**Common mistake:** Zero overlap causing answers to miss content that spans two chunks — fix is to add overlap, not just resize chunks.

## Grounding & Hallucination Reduction
- Instruct the model to answer **only** from retrieved context.
- Require citations to source chunks.
- Provide a fallback: "If the answer isn't in the context, say you don't know."
- Lower temperature reduces randomness/hallucination; higher temperature increases it.

**Common mistake:** Believing bigger chunks or removing retrieval reduces hallucination — both make it worse.

## Evaluating RAG Quality
| Metric | Measures |
|---|---|
| Faithfulness / Groundedness | Is the answer supported by retrieved context? |
| Relevance | Does the answer address the user's question? |
| Context precision/recall | Did retrieval return the right chunks (and enough of them)? |
| BLEU | N-gram overlap with reference text (NOT grounding) |
| Perplexity | Model's fluency/confidence (NOT grounding) |

**Exam note:** Faithfulness ≠ relevance — an answer can be relevant but hallucinated, or faithful but off-topic.
