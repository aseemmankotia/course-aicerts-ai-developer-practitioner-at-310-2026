## Domain 1 Cheat Sheet: Foundations of Modern AI for Developers (5%)

### The Nesting Hierarchy
| Layer | Scope | Example |
|---|---|---|
| AI | Broadest umbrella — any system mimicking intelligent behavior | Rule-based systems, ML, robotics |
| ML | Subset of AI — learns patterns from data instead of hard-coded rules | Linear regression, decision trees |
| DL | Subset of ML — uses multi-layer neural networks | CNNs, RNNs, Transformers |
| GenAI | Subset of DL — generates new content (text/image/code) | LLMs, diffusion image models |

**NLP** is a cross-cutting *application domain* (language tasks), implemented using ML/DL/GenAI — it is not a layer in the nesting above.

**Memory trick:** AI → ML → DL → GenAI, each one is a smaller circle inside the last. If an answer treats GenAI as separate/parallel to DL, it's wrong.

### Core Vocabulary (know cold)
| Term | Definition | Exam Trap |
|---|---|---|
| Model | Trained artifact (architecture + weights) mapping input→output | Don't confuse with "dataset" |
| Weights | Learned numeric parameters | Updated in training/fine-tuning; frozen at inference |
| Training | Process of learning weights from a dataset | Requires compute + ML expertise |
| Fine-tuning | Further training an existing model on a smaller, specific dataset | Still updates weights — not the same as prompting |
| Inference | Using a trained model (frozen weights) to produce output from new input | Every API call = inference, never training |
| Dataset | Collection of examples used for training/eval | Quality drives fine-tune vs API decision |

### Developer Entry Points
| Entry Point | When to Use | Skill/Budget Needed |
|---|---|---|
| API Consumption | No customization to proprietary data needed, fast time-to-ship | Low — just Python + API key |
| Fine-tuning | Need model to adapt tone/domain using your labeled data | Medium — ML basics, curated dataset |
| Pipeline Building | Need to ground model in proprietary docs (e.g., retrieval) without retraining | Low-Medium — no ML engineer required |
| Training from Scratch | Almost never justified for app developers | High — large dataset, GPUs, ML team |

**Rule of thumb:** If the question says "no ML engineers," "limited budget," or "ship fast" → API consumption or pipeline building is correct, NOT fine-tuning or training from scratch.

### AT-310 Exam Logistics
| Item | Value |
|---|---|
| Questions | 50 |
| Time limit | 90 minutes |
| Passing score | 70% |
| Assumed background | Basic Python, basic AI/ML concepts |
| Next course | AT-330 (Engineer track — deeper pipelines/fine-tuning) |

### Common Mistakes
- Treating GenAI as parallel to DL instead of nested inside it.
- Assuming every scenario requires fine-tuning — most don't.
- Confusing "inference" (using a model) with "training" (building a model).
- Forgetting AT-310 assumes you already know basic Python/ML — it won't teach fundamentals from zero.
