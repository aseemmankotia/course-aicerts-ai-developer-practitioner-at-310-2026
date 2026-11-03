# Answer Key — Practice Test 2

**Q1. Correct: C**

Calling an existing model's API, prompting it, and integrating outputs into business logic is the application/orchestration layer — the layer AT-310 explicitly positions as where most developers 'plug in', as opposed to the research/training layers.

---

**Q2. Correct: D**

Fixed, known categories plus labeled historical examples is the defining signature of supervised machine learning — learning a mapping from input features to predefined labels.

---

**Q3. Correct: A**

The standard nested hierarchy is AI ⊃ ML ⊃ DL, and modern generative AI (LLMs, diffusion models) is predominantly built on deep neural network architectures — placing GenAI as a deep-learning-driven application area within this stack.

---

**Q4. Correct: B**

numpy broadcasting aligns shapes from the trailing dimension. data is (1000, 50) and means is (50,); the (50,) array is treated as (1, 50) and stretched across all 1000 rows, so each row gets the correct per-feature mean subtracted. No reshape is needed.

---

**Q5. Correct: A**

transform() applies the aggregation but broadcasts the result back to the original DataFrame's shape and index, so every row gets its region's average revenue correctly aligned by the original row index.

---

**Q6. Correct: A**

axis=1 collapses the test-score axis (axis 1) for each student, summing the 4 scores per row and returning a (3,) array of per-student totals.

---

**Q7. Correct: C**

Default argument values in Python are evaluated exactly once, when the function is defined, not each time it's called. Since dataset=[] creates one list object at definition time, every call that omits the dataset argument mutates and reuses that same list, so add_sample(1) followed by add_sample(2) returns [1, 2], not [2] — a well-known gotcha that causes subtle data leakage between unrelated calls in training pipelines.

---

**Q8. Correct: B**

A log transformation compresses large values more than small ones, pulling the long right tail inward, reducing skewness and moving the distribution closer to normal, which improves linear regression assumptions.

---

**Q9. Correct: B**

Missingness here depends on the unobserved value itself (extreme heat causes the sensor to fail), which is the definition of MNAR. Adding a missingness indicator preserves the signal that missingness correlates with extreme events, and domain-informed imputation avoids biasing values toward the lower observed range.

---

**Q10. Correct: A**

A diverging colormap like 'coolwarm' combined with center=0 and a range of [-1,1] correctly maps negative correlations to one color extreme, positive correlations to the other, and values near zero to the neutral midpoint color.

---

**Q11. Correct: C**

RobustScaler centers and scales data using the median and IQR instead of the mean, standard deviation, or min/max, so the extreme mansion outliers do not distort the scaling applied to the majority of typical houses.

---

**Q12. Correct: D**

With severe class imbalance, the large number of true negatives inflates ROC-AUC, making it look deceptively good. PR-AUC focuses on precision and recall for the positive (minority) class, which is what actually matters for catching fraud, so Model B's much higher PR-AUC makes it the better real-world choice.

---

**Q13. Correct: B**

Cosine similarity divides the dot product by the product of the vector magnitudes, so it measures only the angle between vectors. This makes it robust to magnitude variation caused by differing document lengths or embedding scales.

---

**Q14. Correct: B**

The empirical rule states ~95% of normally distributed data falls within mean ± 2 standard deviations, leaving ~2.5% in each tail. Mean + 2(SD) = 120 + 2(15) = 150 ms, so about 2.5% of latencies exceed this value.

---

**Q15. Correct: B**

For output = W · input to be valid matrix multiplication, with input as a 256x1 column vector and output as a 64x1 column vector, W must have dimensions 64x256, since (64x256)(256x1) = (64x1).

---

**Q16. Correct: D**

A large train/validation gap that barely shrinks with more data is a classic overfitting signature (high variance). The fix is reducing effective model capacity via simplification or regularization, not feeding it more data or capacity.

---

**Q17. Correct: B**

With no ground-truth labels and an unknown number of groups, this is an unsupervised clustering problem. K-means with the elbow method (or silhouette score) is the standard way to discover natural groupings and choose K objectively.

---

**Q18. Correct: C**

With a small dataset, k-fold cross-validation rotates every example through both training and evaluation roles across folds, maximizing data usage while producing a more reliable, lower-variance performance estimate than any single split.

---

**Q19. Correct: B**

Similarly poor performance on both training and validation sets is the hallmark of high bias / underfitting — the model is too simple to capture the underlying pattern. The fix is to increase capacity (more features, more complex algorithm, less regularization), not to simplify further.

---

**Q20. Correct: B**

PR-AUC summarizes precision and recall across all thresholds and is specifically recommended for highly imbalanced datasets because it focuses on performance for the rare positive class rather than being dominated by the abundant negative class.

---

**Q21. Correct: C**

Time series split trains on past data and validates on subsequent future data in sequential folds, mirroring how the model will actually be used and preventing the model from 'seeing the future' during training.

---

**Q22. Correct: D**

Bayesian optimization builds a surrogate probabilistic model (commonly a Gaussian process) of the objective function and uses it to select the next most promising hyperparameter combination, making it far more sample-efficient than methods that evaluate points independently — ideal for a limited 40-run budget across 8 parameters.

---

**Q23. Correct: A**

Precision = 80/(80+20) = 0.80. Recall = 80/(80+40) = 0.667. F1 = 2 × (0.80 × 0.667)/(0.80 + 0.667) = 2 × 0.5333/1.467 ≈ 0.727, which rounds to 0.73.

---

**Q24. Correct: C**

The gap between 99% training accuracy and 68% validation accuracy is classic overfitting caused by too few images relative to the number of trainable parameters. Freezing most of the pretrained convolutional base preserves generalizable low- and mid-level features learned from ImageNet, while only training the small classifier head drastically reduces trainable parameters, which is the standard transfer-learning fix for small-dataset overfitting.

---

**Q25. Correct: A**

Correct transfer-learning setup replaces the task-specific output layer to match the new number of classes, keeps the pretrained convolutional layers frozen initially to reuse learned feature representations, and trains only the new head, typically with a moderate-to-low learning rate to avoid destroying useful pretrained weights.

---

**Q26. Correct: C**

With only ~900 total labeled images and a limited compute budget, transfer learning from a model pretrained on a large dataset lets the developer reuse already-learned visual features (edges, textures, shapes) and only fine-tune a small number of layers, which converges quickly and achieves good accuracy with little data and compute.

---

**Q27. Correct: A**

Pooling layers (such as max pooling) reduce the spatial dimensions (width and height) of feature maps, which decreases computation and memory requirements in later layers while preserving the strongest/most salient activations, and also provides a degree of translation invariance.

---

**Q28. Correct: B**

Context windows are a hard token limit on input+output combined. Summarizing or truncating older, less relevant turns reduces token count while retaining the information needed to continue the conversation coherently — a standard pattern for long-running chat sessions.

---

**Q29. Correct: A**

Cosine similarity equals the dot product divided by the product of vector magnitudes. When vectors are already L2-normalized (magnitude = 1), the dot product alone produces the same ranking as cosine similarity, which is why many vector databases use dot product for speed when embeddings are pre-normalized.

---

**Q30. Correct: C**

BPE and similar subword methods (e.g., WordPiece, SentencePiece) break unfamiliar words into smaller known subword units learned from training data, so rare or novel words are represented as a sequence of known pieces rather than a single <UNK> token. This is the tokenization approach used by GPT, BERT, and most modern LLMs.

---

**Q31. Correct: D**

As the dimension d_k increases, the variance of the raw dot products QK^T grows, pushing softmax inputs to extreme values and causing vanishing gradients during training. Dividing by sqrt(d_k) keeps the dot products in a stable range, improving gradient flow — this is explicitly why the scaling factor was introduced in the original Transformer paper.

---

**Q32. Correct: D**

Native structured output / JSON-schema enforcement constrains the response at the API level so it conforms to the schema regardless of prompt phrasing, eliminating this class of parsing failure.

---

**Q33. Correct: D**

Low temperature produces consistent, deterministic output appropriate for code generation, while higher temperature increases lexical diversity and creativity, appropriate for slogans — this is standard sampling-parameter practice tested on the exam.

---

**Q34. Correct: D**

Multimodal model APIs impose maximum image size, resolution, or payload limits; large unoptimized photos commonly trigger request failures, and resizing/compressing before sending is the standard fix.

---

**Q35. Correct: B**

Chunking audio to respect the hard duration limit, preserving timestamps for correct ordering, and adding a dedicated diarization step to label speakers is the standard pattern for building compliant long-audio transcription features that also need speaker separation.

---

**Q36. Correct: A**

Smaller, semantically coherent chunks with overlap preserve local context across boundaries and prevent irrelevant text from diluting the retrieved context, directly fixing both the boundary-split and dilution problems.

---

**Q37. Correct: C**

Weaviate is an open-source vector database purpose-built for ANN search with metadata filtering and native horizontal sharding/replication, meeting all three stated requirements at billion-scale.

---

**Q38. Correct: D**

Lowering top_k and adding a similarity-score cutoff ensures only the most relevant chunks are passed to the LLM, reducing noise and keeping the prompt within the context window.

---

**Q39. Correct: A**

For L2-normalized vectors, the dot product equals the cosine of the angle between them, so ranking by dot product produces identical ordering to ranking by cosine similarity.

---

**Q40. Correct: D**

A bounded iteration count with a graceful fallback is the standard safeguard against runaway agent loops caused by parsing errors or ambiguous stopping conditions — it caps cost/latency while still allowing a few retries.

---

**Q41. Correct: D**

FastAPI's Pydantic models give automatic schema validation, and StreamingResponse natively supports sending tokens as they're produced — satisfying both requirements without extra frameworks.

---

**Q42. Correct: C**

Pinning both the base image and exact package versions makes the build reproducible — the same image behaves identically in every environment, eliminating 'works on my machine' drift.

---

**Q43. Correct: C**

Native function/tool calling constrains the model's output to a defined JSON schema, so the agent code can reliably extract arguments without fragile regex or string parsing of free-form text.

---

**Q44. Correct: A**

Indirect prompt injection hides malicious instructions inside retrieved content. The core defense is treating all retrieved/untrusted text as data, not commands, and gating any sensitive tool invocation (like sending email) behind validation and human-in-the-loop approval, regardless of what instructions appear in the content.

---

**Q45. Correct: B**

Silent accuracy degradation with no errors logged is the signature of data or concept drift — the statistical properties of incoming data have shifted away from what the model was trained on. Monitoring must actively compare live distributions to the training baseline to catch this, since the model will not throw an error; it will just perform worse.

---

**Q46. Correct: C**

Secrets should be injected at runtime from a dedicated secrets manager via environment variables, kept out of source control, logs, and especially out of LLM prompts, since prompt content can be exposed through model outputs, logs, or injection attacks.

---

**Q47. Correct: A**

A model card is a standardized documentation artifact that communicates a model's intended use, out-of-scope uses, limitations, training data provenance, and evaluation metrics (including across demographic or use-case subgroups), enabling responsible deployment and informed decision-making by downstream users.

---

