## Chapter 8: Domain 8: NLP, Transformers, and LLM Fundamentals — Practice Questions

**Q1.** A company is building an internal search engine where a query like 'bank' must be interpreted differently depending on whether the surrounding text discusses rivers or finance. Which embedding approach BEST satisfies this requirement?

A) Contextual embeddings from a transformer model such as BERT
B) Static word embeddings such as Word2Vec or GloVe
C) One-hot encoded vectors for each vocabulary word
D) Bag-of-words frequency vectors

<details>
<summary>Answer</summary>

**Correct: A**

Contextual embeddings (e.g., from BERT) generate a different vector for the same word depending on surrounding tokens, resolving polysemy like 'bank'.

**Why the others are wrong:**
- Word2Vec/GloVe assign exactly one fixed vector per word regardless of context, so 'bank' always has the same vector.
- One-hot vectors carry no semantic meaning and treat every word as equally dissimilar to every other word.
- Bag-of-words ignores word order and context entirely, so it cannot disambiguate meaning.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An LLM has a context window of 8,192 tokens. A user needs to send a prompt containing 9,000 words of source text plus leave room for the model's response. Using the standard estimate of ~1.33 tokens per word, what is the BEST approach?

A) Split the input into chunks that fit the context window (or use map-reduce summarization), or switch to a model with a larger context window
B) Send the full 9,000-word prompt and let the API silently truncate the end
C) Apply stemming to the text first to reduce the character count before tokenizing
D) Ignore the limit — context windows automatically expand based on request size

<details>
<summary>Answer</summary>

**Correct: A**

9,000 words ≈ 12,000 tokens, exceeding the 8,192-token limit. Chunking/summarizing content or using a model with a larger context window are the only approaches that preserve full content without errors.

**Why the others are wrong:**
- Silent truncation loses content and does not reliably work across all APIs; many will instead throw an error.
- Stemming reduces word forms slightly but does not meaningfully reduce token count enough to matter, and it can also damage meaning.
- Context windows are a fixed architectural limit of the model and do not auto-expand.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A data scientist wants to quickly test a pretrained sentiment analysis model from Hugging Face with minimal code, without manually instantiating a tokenizer and model class separately. Which feature should they use?

A) The `pipeline()` function
B) The `Trainer` class
C) The `Dataset` class
D) The `AutoConfig` class

<details>
<summary>Answer</summary>

**Correct: A**

`pipeline('sentiment-analysis')` wraps tokenizer, model, and post-processing into a single high-level call, ideal for quick inference.

**Why the others are wrong:**
- `Trainer` is used for fine-tuning/training models, not quick one-off inference.
- `Dataset` is used for loading and managing training/evaluation data, not for running inference.
- `AutoConfig` only loads model configuration metadata, not a usable inference pipeline.

</details>

---

**Q4.** When generating text with a Hugging Face transformers pipeline, which parameter scales the probability distribution over the next predicted token to control output randomness?

A) temperature
B) max_length
C) num_beams
D) padding

<details>
<summary>Answer</summary>

**Correct: A**

Temperature scales the logits before the softmax; low values (e.g., 0.1) make output more deterministic, high values (e.g., 1.0+) make it more random/creative.

**Why the others are wrong:**
- max_length controls the maximum number of tokens generated, not randomness.
- num_beams controls beam search width for deterministic multi-path decoding, not probability scaling.
- padding controls how sequences are padded to equal length for batching, unrelated to randomness.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Using a Hugging Face AutoTokenizer for BERT, the word 'playing' is tokenized into ['play', '##ing']. What does the '##' prefix indicate?

A) The token is a stop word and will be removed during preprocessing
B) The token is out-of-vocabulary and will be ignored by the model
C) The token marks the end of a sentence
D) The token is a continuation of the previous token, not the start of a new word

<details>
<summary>Answer</summary>

**Correct: D**

In BERT's WordPiece tokenization, '##' marks a subword that continues the previous token rather than starting a new word, enabling handling of unseen/rare words.

**Why the others are wrong:**
- Stop words are not marked with '##'; they are simply regular tokens unless explicitly filtered by a separate step.
- WordPiece subwords are still part of the model's vocabulary and are processed normally, not ignored.
- Sentence boundaries are marked with special tokens like [SEP], not '##'.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** What is the primary difference between stemming and lemmatization in text preprocessing?

A) Stemming uses a dictionary to find the base form; lemmatization crudely chops word endings
B) Stemming and lemmatization are two names for the exact same algorithm
C) Stemming only processes verbs while lemmatization only processes nouns
D) Stemming crudely removes suffixes using rules and can produce non-words; lemmatization uses vocabulary and morphological analysis to return a valid dictionary base form

<details>
<summary>Answer</summary>

**Correct: D**

Stemming (e.g., Porter stemmer) applies simple suffix-stripping rules and can yield non-dictionary fragments (e.g., 'studies'→'studi'), while lemmatization uses linguistic knowledge to return a real dictionary form (e.g., 'studies'→'study').

**Why the others are wrong:**
- This reverses the definitions — stemming is the crude rule-based method, not lemmatization.
- They produce different outputs and use fundamentally different techniques (rule-based vs. dictionary/morphology-based).
- Both techniques operate on any part of speech, not restricted to specific word classes.

</details>

---

**Q7.** A chatbot needs 'bank' in 'I deposited money at the bank' and 'I sat by the river bank' to have different vector representations reflecting their distinct meanings. Which technique should be used to generate these word vectors?

A) GloVe static embeddings
B) A simple bag-of-words count vector
C) One-hot encoding of the vocabulary
D) Contextual embeddings from a transformer encoder

<details>
<summary>Answer</summary>

**Correct: D**

Transformer-based contextual embeddings compute a token's vector using the full surrounding sentence via self-attention, so the same word gets different vectors depending on context.

**Why the others are wrong:**
- GloVe is a static embedding method — 'bank' gets exactly one vector regardless of sentence.
- Bag-of-words discards word order and surrounding context entirely.
- One-hot encoding has no notion of meaning or context at all.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** In the transformer self-attention mechanism, what role do the Query, Key, and Value vectors play?

A) They compress the vocabulary into a smaller embedding dimension
B) They convert raw text into stemmed root words before embedding begins
C) They allow the model to weigh the importance of every other token in the sequence when computing a representation for the current token
D) They dynamically shrink the model's context window to save memory

<details>
<summary>Answer</summary>

**Correct: C**

Self-attention computes a similarity score between a token's Query and every other token's Key, then uses those scores to weight the Values — letting the model capture relationships between tokens regardless of their distance apart.

**Why the others are wrong:**
- Q/K/V vectors are not involved in vocabulary/embedding-dimension compression; that is handled by the embedding layer.
- Stemming is a preprocessing step unrelated to the Q/K/V mechanism inside the transformer.
- Context window size is a fixed architectural/config limit, not something adjusted by Q/K/V computation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

