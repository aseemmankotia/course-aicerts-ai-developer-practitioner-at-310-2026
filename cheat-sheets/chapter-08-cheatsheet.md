## Domain 8 Cheat Sheet: NLP, Transformers & LLM Fundamentals

### Tokenization vs. Words
| Concept | Detail |
|---|---|
| Token | Subword unit from BPE/WordPiece tokenizer; not the same as a word |
| Word→Token ratio | ~1 word ≈ 1.33 tokens (1 token ≈ 0.75 words) |
| Exam trap | Assuming word count = token count when estimating context window fit |

### Stemming vs. Lemmatization
| Technique | Method | Example | Output quality |
|---|---|---|---|
| Stemming | Rule-based suffix stripping | studies → studi | May produce non-words |
| Lemmatization | Dictionary/morphology lookup | studies → study | Always a valid word, slower |

### Embeddings
| Type | Example Models | Context-aware? |
|---|---|---|
| Static | Word2Vec, GloVe | No — one vector per word |
| Contextual | BERT, GPT encoders | Yes — vector varies by sentence |

Exam trap: picking static embeddings when the scenario requires disambiguating word meaning (e.g., 'bank').

### Self-Attention (Transformer Core)
- Each token generates a **Query**, **Key**, **Value** vector.
- Attention score = similarity(Query_i, Key_j) for all tokens j.
- Scores weight the Values → new representation for token i.
- **Multi-head attention**: runs several Q/K/V attention computations in parallel to capture different relationship types, then concatenates.
- Benefit over RNNs: attends to all tokens at once, regardless of distance, enabling parallel training.

### Context Window Limits (known at publication)
| Model Family | Context Window |
|---|---|
| GPT-4 Turbo / GPT-4o | 128,000 tokens |
| Claude 3 family | 200,000 tokens |
| Llama 3.1 | 128,000 tokens |

Exam trap: exceeding the context window silently truncates or errors — solution is chunking/map-reduce summarization or switching to a larger-window model, not stemming or ignoring the limit.

### Hugging Face Quick Reference
```python
from transformers import pipeline
clf = pipeline('sentiment-analysis')
clf('This course is great!')

from transformers import AutoTokenizer, AutoModel
tok = AutoTokenizer.from_pretrained('bert-base-uncased')
model = AutoModel.from_pretrained('bert-base-uncased')
tokens = tok.tokenize('playing')  # ['play', '##ing']
```

### Prompting Parameters
| Parameter | Effect |
|---|---|
| temperature | Scales randomness of next-token probabilities (low=deterministic, high=creative) |
| top_p / top_k | Restricts sampling pool to most likely tokens |
| max_length / max_tokens | Caps number of generated tokens |

Exam trap: confusing `temperature` (randomness) with `max_length` (output length cap) or `num_beams` (deterministic beam search).
