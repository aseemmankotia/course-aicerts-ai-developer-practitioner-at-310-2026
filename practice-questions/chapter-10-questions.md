## Chapter 10: Domain 10: Retrieval-Augmented Generation and Knowledge Assistants — Practice Questions

**Q1.** A company builds a knowledge assistant over 50,000 internal PDFs averaging 20 pages each. Users ask highly specific technical questions and expect precise, complete answers. Which chunking strategy BEST balances retrieval precision and context completeness?

A) Fixed-size chunks of roughly 500 tokens with 10-20% overlap between adjacent chunks
B) Treat each entire document as a single chunk with no splitting
C) Split by single sentence with zero overlap
D) Use random chunk sizes ranging from 50 to 5000 tokens

<details>
<summary>Answer</summary>

**Correct: A**

Mid-sized chunks with overlap preserve enough local context for embeddings to be meaningful while keeping retrieved passages focused enough for precise matching; overlap prevents losing information that spans a chunk boundary.

**Why the others are wrong:**
- Whole-document chunks dilute the embedding vector with too many topics, hurting retrieval precision and often exceeding usable context length.
- Single-sentence chunks with no overlap lose surrounding context, so retrieved text is often too fragmented to answer the question.
- Random, inconsistent chunk sizes produce unpredictable retrieval quality and make tuning the pipeline impossible.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A RAG-based assistant sometimes produces answers that sound plausible but reference facts absent from the source documents. Which technique BEST reduces this hallucination?

A) Increase the LLM's temperature setting to make responses more creative
B) Instruct the model via the prompt to answer only from the retrieved context, cite the source chunk, and respond 'I don't know' when the context lacks the answer
C) Remove the retrieval step and let the model answer purely from pretrained knowledge
D) Increase chunk size to 10,000 tokens so documents are never split

<details>
<summary>Answer</summary>

**Correct: B**

Explicit grounding instructions constrain the model to the supplied context and give it a safe fallback, which is the standard technique for reducing hallucination in RAG systems.

**Why the others are wrong:**
- Higher temperature increases output randomness, which increases the chance of hallucination, not decreases it.
- Removing retrieval eliminates the grounding source entirely, making hallucination more likely, not less.
- Very large chunks dilute relevance scoring and can exceed context window limits; it does not guarantee the model stays grounded.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A search feature must find documents that are semantically related to a query even when exact keywords differ, such as matching 'automobile' when the user searches 'car'. Which approach should be used?

A) Keyword/BM25 search
B) Regular expression pattern matching
C) Exact string match with wildcard characters
D) Embedding-based similarity search using cosine similarity between query and document vectors

<details>
<summary>Answer</summary>

**Correct: D**

Embeddings map semantically similar text to nearby vectors regardless of exact wording, and cosine similarity measures that closeness directly.

**Why the others are wrong:**
- BM25/keyword search relies on term overlap and would miss synonyms like 'car' vs 'automobile'.
- Regex matching only finds literal patterns, not semantic equivalence.
- Exact string matching with wildcards still requires shared substrings and cannot capture synonym relationships.

</details>

---

**Q4.** Which component in a RAG pipeline is responsible for storing embedding vectors and performing fast nearest-neighbor similarity lookups?

A) The large language model
B) A vector store such as FAISS or Chroma
C) The prompt template engine
D) The tokenizer

<details>
<summary>Answer</summary>

**Correct: B**

Vector stores like FAISS and Chroma index document embeddings and support efficient approximate or exact nearest-neighbor search, which is the retrieval mechanism in RAG.

**Why the others are wrong:**
- The LLM generates text; it does not store or index vectors.
- The prompt template engine assembles text for the LLM call; it has no indexing or search function.
- The tokenizer converts text to tokens for the model; it plays no role in vector storage or similarity search.

</details>

---

**Q5.** In the retrieve-augment-generate RAG pipeline, which step involves inserting the retrieved chunks into the prompt that is sent to the LLM?

A) Retrieve
B) Augment
C) Generate
D) Embed

<details>
<summary>Answer</summary>

**Correct: B**

The 'augment' step takes the chunks found during retrieval and combines them with the user's question into the context sent to the LLM.

**Why the others are wrong:**
- Retrieve is the step that searches the vector store for relevant chunks, before they are added to the prompt.
- Generate is the step where the LLM produces the final answer, after augmentation has already occurred.
- Embedding is a preprocessing step that converts text into vectors; it is not part of the retrieve-augment-generate runtime sequence.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** An engineer sets chunk size to 2000 tokens with zero overlap for RAG over technical documentation containing numbered procedural steps. Users report answers frequently miss steps that span chunk boundaries. What is the most likely fix?

A) Increase chunk size further to 10,000 tokens
B) Switch to a larger embedding model
C) Switch the similarity metric from cosine similarity to Euclidean distance
D) Add 10-20% overlap between adjacent chunks so content near boundaries appears in more than one chunk

<details>
<summary>Answer</summary>

**Correct: D**

Zero overlap means content exactly at a chunk boundary is split and may not be fully retrieved together; adding overlap ensures boundary content appears intact in at least one chunk.

**Why the others are wrong:**
- Increasing chunk size further dilutes topical focus and can still split content at new boundaries; it does not directly solve the overlap problem.
- A larger embedding model improves semantic representation quality but does not address lost content at chunk boundaries.
- Changing the distance metric affects ranking of similarity scores but does not fix content being physically split across chunks.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Two document vectors A and B have a cosine similarity of 0.92. What does this value indicate?

A) The vectors are nearly orthogonal and unrelated in meaning
B) The vectors represent exact opposite meanings
C) The vectors point in nearly the same direction, indicating high semantic similarity, since cosine similarity ranges from -1 to 1
D) The score is invalid because cosine similarity cannot exceed 1

<details>
<summary>Answer</summary>

**Correct: C**

Cosine similarity ranges from -1 (opposite) to 1 (identical direction); a value of 0.92 is close to 1, indicating the vectors are highly aligned and thus semantically similar.

**Why the others are wrong:**
- Orthogonal vectors would produce a cosine similarity near 0, not 0.92.
- Exact opposite direction corresponds to a cosine similarity of -1, not a high positive value.
- 0.92 is well within the valid -1 to 1 range, so the score is not invalid.

</details>

---

**Q8.** Which metric is specifically used to evaluate whether a RAG system's generated answer is faithful to (grounded in) the retrieved context, as opposed to measuring general answer relevance?

A) BLEU score
B) Faithfulness (groundedness) score
C) Perplexity
D) Token latency

<details>
<summary>Answer</summary>

**Correct: B**

Faithfulness/groundedness metrics check whether claims in the generated answer are actually supported by the retrieved source text, directly measuring hallucination risk.

**Why the others are wrong:**
- BLEU measures n-gram overlap with a reference answer and does not check whether the answer is supported by retrieved context.
- Perplexity measures how confidently a language model predicts text; it does not evaluate factual grounding.
- Token latency measures response speed, an operational metric unrelated to answer quality or grounding.

</details>

---

