## Chapter 8: Domain 8: NLP, Transformers, and LLM Fundamentals — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | GPT-4 Turbo / GPT-4o context window size? | 128,000 tokens. Exam tip: larger context windows allow more conversation history or document content but increase cost and latency. |
| 2 | Claude 3 family context window size? | 200,000 tokens. Exam tip: one of the largest standard context windows, well-suited for long-document analysis tasks. |
| 3 | Rough token-to-word ratio for English text? | ~1 token ≈ 0.75 words (equivalently, 1 word ≈ 1.33 tokens). Exam tip: used to estimate whether a prompt will fit within a model's context window. |
| 4 | Word2Vec/GloVe vs. BERT embeddings — key difference? | Word2Vec/GloVe: static, one fixed vector per word regardless of context. BERT: contextual, vector changes based on surrounding words. Exam tip: contextual embeddings resolve polysemy (e.g., 'bank'). |
| 5 | Stemming vs. Lemmatization? | Stemming: rule-based suffix stripping, can produce non-words (e.g., 'studies'→'studi'). Lemmatization: dictionary/morphology-based, returns a valid base form (e.g., 'studies'→'study'). Exam tip: lemmatization is more accurate but computationally heavier. |
| 6 | Tokens vs. words — why do they differ? | Tokenizers (e.g., BPE, WordPiece) split text into subword units, not whole words — common words may be one token, rare/long words split into several. Exam tip: token count ≠ word count; always estimate with the token-to-word ratio. |
| 7 | Hugging Face `pipeline()` function purpose? | High-level API for quick inference with pretrained models (e.g., `pipeline('sentiment-analysis')`) without manually loading tokenizer/model classes. Exam tip: ideal for fast prototyping, not for training. |
| 8 | Hugging Face: AutoTokenizer vs. AutoModel? | AutoTokenizer converts text into token IDs; AutoModel loads the pretrained architecture and weights. Exam tip: both load via `.from_pretrained('model-name')`. |
| 9 | What does the '##' prefix mean in BERT WordPiece tokens? | Indicates the token continues the previous token rather than starting a new word (e.g., 'playing' → ['play', '##ing']). Exam tip: subword tokenization handles out-of-vocabulary words gracefully. |
| 10 | What does the `temperature` parameter control in LLM generation? | Scales the probability distribution over next-token predictions. Low temperature (e.g., 0.1) = deterministic/focused; high temperature (e.g., 1.0+) = more random/creative. Exam tip: temperature near 0 is nearly deterministic. |
| 11 | What do Query, Key, Value (Q/K/V) vectors do in self-attention? | Each token's Query is compared against every other token's Key to compute attention scores, which weight the Values. Exam tip: this lets transformers relate tokens regardless of their distance in the sequence. |
| 12 | Why do transformers use multi-head attention? | Running several attention computations in parallel ('heads') lets the model capture different types of relationships (e.g., syntax vs. semantics) simultaneously, then concatenates the results. Exam tip: 'multi-head' = multiple parallel attention operations. |
