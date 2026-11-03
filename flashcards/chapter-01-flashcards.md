## Chapter 1: Domain 1: Foundations of Modern AI for Developers — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | AT-310 exam format: question count, time limit, and passing score? | 50 questions, 90 minutes, 70% required to pass. Exam tip: that's ~1.8 min/question — don't get stuck on one item. |
| 2 | What background is assumed before starting AT-310? | Basic Python and basic AI/ML concepts. Exam tip: the exam won't teach you Python syntax or ML theory from zero — it assumes you already have it. |
| 3 | AI vs ML vs DL vs GenAI — how do they nest? | AI ⊃ ML ⊃ DL ⊃ GenAI. Each is a subset of the previous. Exam tip: GenAI is the narrowest category, not a separate parallel field. |
| 4 | Where does NLP fit in the AI/ML/DL/GenAI hierarchy? | NLP is a cross-cutting application domain (working with human language) implemented using ML/DL/GenAI techniques — it's not a layer in the AI>ML>DL>GenAI nesting itself. |
| 5 | What are the three developer entry points into AI covered in AT-310? | 1) Consuming a model via API, 2) Fine-tuning an existing model, 3) Building a pipeline (e.g., retrieval + orchestration) around a model. Exam tip: most real-world dev scenarios map to #1 or #3. |
| 6 | When should a developer choose API consumption over fine-tuning? | Choose API consumption when no customization to proprietary data/behavior is needed and speed/budget matter most. Exam tip: fine-tuning implies updating model weights on new data — a bigger commitment than a prompt or API call. |
| 7 | Define 'model' in the AI vocabulary set. | A trained artifact (architecture + learned weights) that maps inputs to outputs. Exam tip: the model is the end product of training, not the training process itself. |
| 8 | Define 'weights' in the AI vocabulary set. | The numeric parameters learned during training that the model uses to compute outputs. Exam tip: weights are updated in training/fine-tuning, frozen during inference. |
| 9 | Inference vs Training — what's the key difference? | Training = weights are updated from a dataset. Inference = frozen weights are used to produce output from new input. Exam tip: every API call to a model is inference, never training. |
| 10 | Define 'dataset' in the AI vocabulary set. | A structured collection of examples used to train, fine-tune, or evaluate a model. Exam tip: dataset quality/relevance directly affects which entry point (fine-tune vs API) makes sense. |
| 11 | How does AT-310 relate to AT-330? | AT-310 (Foundations, developer-focused, API/consumption level) is the feeder course into AT-330 (Engineer track, deeper pipeline/fine-tuning/architecture work). Exam tip: AT-310 won't test deep engineering — that's AT-330 territory. |
| 12 | Is Generative AI a type of Deep Learning or a separate field? | GenAI is a subset of Deep Learning — it uses deep neural network architectures (e.g., transformers) specifically to generate new content. Exam tip: don't treat GenAI as parallel to DL; it's nested inside it. |
