# Answer Key — Practice Test 1

**Q1. Correct: A**

Pretrained LLMs accessed via API already encode broad language generation capability; prompt engineering lets a developer get usable output in hours without any training data or infrastructure, matching the two-day constraint.

---

**Q2. Correct: B**

Deep learning is a specialized branch of machine learning that relies on neural networks with many layers to automatically extract hierarchical features, removing the need for manual feature engineering common in classical ML.

---

**Q3. Correct: C**

Classifying the intent of a written message is a text-understanding task, which falls squarely under Natural Language Processing — the field focused on enabling machines to interpret and act on human language.

---

**Q4. Correct: A**

pandas.read_csv() efficiently parses large CSV files into a DataFrame, and converting a column to a numpy array (via .values or .to_numpy()) enables vectorized, C-level numerical operations that are far faster than Python-level loops.

---

**Q5. Correct: B**

A dict is a hash map that stores key-value pairs and provides average O(1) time complexity for lookups, insertions, and updates by key, which is exactly what a configuration lookup needs.

---

**Q6. Correct: D**

df['score'].fillna(df['score'].mean()) computes the mean of the non-missing values in that column and uses it to replace all NaN entries, which is the standard pandas pattern for mean imputation.

---

**Q7. Correct: C**

In Python, a list (defined with []) can be modified after creation (items added, removed, or changed), while a tuple (defined with ()) is immutable and cannot be changed once created.

---

**Q8. Correct: B**

Mean/median imputation preserves row count for a quick baseline and is appropriate when missingness is random (MCAR), minimizing bias introduced by the imputation.

---

**Q9. Correct: D**

A correlation heatmap displays the pairwise correlation coefficients for all feature combinations in a single color-coded grid, making it easy to spot strongly correlated pairs at a glance.

---

**Q10. Correct: B**

One-hot encoding avoids implying a false ordinal relationship between nominal categories, which is essential for linear models that would otherwise interpret integer-encoded labels as having magnitude or order.

---

**Q11. Correct: D**

KNN relies on distance metrics, such as Euclidean distance; without scaling, features with larger numeric ranges disproportionately dominate the distance calculation, skewing neighbor selection.

---

**Q12. Correct: B**

F1 score is the harmonic mean of precision and recall, so it penalizes models that ignore the minority class while still rewarding correct detections — making it robust to severe class imbalance.

---

**Q13. Correct: C**

Cosine similarity computes the cosine of the angle between two vectors, so it captures directional similarity while being unaffected by the vectors' magnitudes — the standard choice for comparing embeddings.

---

**Q14. Correct: C**

z = (90 − 70) / 5 = 4. Since |4| > 3, this point exceeds the standard outlier threshold and is correctly flagged as an outlier.

---

**Q15. Correct: C**

The median is the middle value when data is sorted, so it is resistant to the pull of extreme high values and better represents the typical salary in a right-skewed distribution.

---

**Q16. Correct: D**

A large gap between training accuracy (98%) and validation accuracy (65%) is the classic signature of overfitting — the model has memorized training data patterns, including noise, instead of learning generalizable rules. Regularization, simplifying the model, dropout, or adding more diverse training data are standard fixes.

---

**Q17. Correct: C**

Since there are no predefined labels and the goal is to discover natural groupings in the data, this is an unsupervised learning problem. Clustering algorithms like K-means group data points by similarity without needing labeled outcomes.

---

**Q18. Correct: B**

The target variable (sale price) is a known, continuous numeric value in the training data, making this a supervised learning problem. Since the output is continuous rather than a discrete category, regression is the correct algorithm type.

---

**Q19. Correct: C**

The validation set is used iteratively during model development to tune hyperparameters (e.g., learning rate, regularization strength) and compare candidate models, without touching the held-out test set, which prevents data leakage into the final performance estimate.

---

**Q20. Correct: C**

Recall (true positives / (true positives + false negatives)) directly measures the model's ability to catch actual fraud cases, which is what the team wants to maximize even at the cost of more false positives.

---

**Q21. Correct: D**

Stratified k-fold cross-validation preserves the original class proportions in every fold, ensuring the minority class is adequately represented in both training and validation splits, which is critical for reliable evaluation on imbalanced data.

---

**Q22. Correct: B**

k = 10 is a widely used default because it provides a good trade-off: enough folds to reduce variance in the estimate while keeping computational cost reasonable and each training fold large enough to avoid high bias.

---

**Q23. Correct: A**

A false negative occurs when the model incorrectly predicts the negative class (no disease) while the actual label is positive (disease present) — the model misses a real case.

---

**Q24. Correct: A**

Transfer learning reuses low-level and mid-level features already learned on a large dataset, requiring far less data and compute to adapt to a new task by retraining only the top layers.

---

**Q25. Correct: D**

A widening gap between falling training loss and rising validation loss is the classic signature of overfitting; dropout, data augmentation, and early stopping all directly counter this by limiting memorization of training data.

---

**Q26. Correct: C**

ReLU outputs the input directly when positive and zero otherwise, which prevents gradient saturation for positive activations and is very fast to compute, making it the standard default for CNN hidden layers.

---

**Q27. Correct: D**

Pooling layers reduce the spatial dimensions (width and height) of feature maps, which lowers computation and parameter count in later layers while keeping the strongest activations, such as with max pooling.

---

**Q28. Correct: D**

Dense embeddings capture semantic meaning in vector space, so paraphrased queries and synonyms land near each other even with zero lexical overlap, which is exactly the AT-310 'embeddings for semantic retrieval' objective.

---

**Q29. Correct: A**

Decoder-only transformers use masked self-attention so each position can only attend to earlier tokens, which is precisely the mechanism needed for left-to-right autoregressive generation — the architecture behind GPT-style LLMs covered in AT-310.

---

**Q30. Correct: A**

A model's context window is a fixed architectural limit on total input plus output tokens; exceeding it causes the API to truncate the input or return an error, which is a core 'how LLMs are used from code' exam point.

---

**Q31. Correct: D**

Self-attention computes a weighted combination of all tokens' representations for each position, letting the model dynamically determine which other tokens are most relevant to interpreting the current one — the foundational transformer concept tested on AT-310.

---

**Q32. Correct: B**

Structured output (JSON mode / schema-constrained generation) forces the model to return machine-parseable, schema-conformant data, eliminating the need for fragile string parsing and making downstream integration reliable.

---

**Q33. Correct: C**

A multimodal model can natively accept image input alongside text in the same context, enabling both initial description generation and coherent follow-up Q&A grounded in the image.

---

**Q34. Correct: A**

Low temperature combined with low top_p narrows the model's token sampling toward the highest-probability choices, producing more deterministic and repeatable outputs — ideal for code generation.

---

**Q35. Correct: A**

Function calling allows the model to output a structured payload (function name plus arguments) that application code can directly invoke, instead of relying on parsing free-form natural-language prose.

---

**Q36. Correct: D**

Splitting along natural document structure (headers, paragraphs, table boundaries) keeps semantically related content together, and a small overlap prevents loss of context for information that spans a chunk boundary — producing chunks that are both coherent and retrievable with precision.

---

**Q37. Correct: A**

Overlap ensures that sentences or ideas spanning the boundary between two chunks appear fully in at least one chunk, preventing loss of meaning and improving the chance that relevant context is retrieved intact.

---

**Q38. Correct: A**

Large chunks covering multiple topics produce embeddings that are an average of several unrelated semantic concepts, so they can match many unrelated queries at a moderate similarity score. Shrinking chunk size to one topic per chunk sharpens the embedding's semantic focus and improves retrieval precision.

---

**Q39. Correct: A**

RAG keeps the base model frozen and supplies relevant retrieved context as part of the prompt at query time, making knowledge updates as simple as updating the vector store. Fine-tuning instead updates the model's internal weights through a training process, which is slower and costlier to refresh.

---

**Q40. Correct: A**

FastAPI exposes the agent over HTTP, and Docker containerization packages the app with its exact dependencies and runtime, guaranteeing identical behavior across staging and production regardless of host OS differences.

---

**Q41. Correct: B**

FastAPI is built on Starlette and Pydantic, providing native async/await support, automatic request validation from type hints, and auto-generated OpenAPI/Swagger documentation out of the box — exactly matching all three requirements.

---

**Q42. Correct: C**

Defining a Pydantic BaseModel for the request body and using @app.post correctly tells FastAPI to parse and validate the incoming JSON body against the 'prompt' field, matching the stated requirement.

---

**Q43. Correct: D**

An agent loop is defined by its iterative observe-decide-act cycle, where the agent can invoke tools, evaluate results, and repeat steps until it determines the task is complete — this is what enables multi-step reasoning and tool calling.

---

**Q44. Correct: C**

Prompt-injection defense requires guardrails: detecting override attempts (input filtering), restricting what the model can output (output filtering), and ensuring secrets/system instructions are never placed where the model or a crafted prompt could leak them. This is the standard layered mitigation taught in AT-310 for securing LLM apps.

---

**Q45. Correct: B**

Once a secret is exposed in a public repo, it must be treated as compromised. The only safe remediation is to revoke/rotate the credential immediately, remove it from source code in favor of a secrets manager or environment variable, and check logs for misuse — deleting history alone does not undo prior exposure.

---

**Q46. Correct: B**

Data drift (and the resulting model/concept drift) occurs when production input distributions diverge from training data, degrading accuracy over time. AT-310 covers monitoring deployed models specifically for drift by comparing feature distributions, prediction distributions, or performance metrics against baseline training data.

---

**Q47. Correct: B**

Explainability (also called interpretability) is the responsible-AI pillar focused on making model decisions understandable to humans — whether through feature importance, decision rules, or model-agnostic explanation techniques — so stakeholders can trust and audit outcomes.

---

