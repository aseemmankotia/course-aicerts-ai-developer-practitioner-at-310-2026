## Chapter 9: Domain 9: Generative and Multimodal AI Application Development — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | What does temperature=0 do in LLM sampling? | Produces near-deterministic output by always favoring the highest-probability token. Exam tip: use low temperature for factual/consistent tasks, higher values (1.5-2) for creative tasks. |
| 2 | Valid range and default for the temperature parameter? | 0 to 2, default 1. Exam tip: avoid adjusting both temperature and top_p in the same call — guidance recommends changing only one. |
| 3 | What is top-p (nucleus) sampling? | Model samples only from the smallest set of tokens whose cumulative probability is ≥ p. top_p=0.1 restricts to the top 10% probability mass. Range 0-1, default 1. |
| 4 | Zero-shot prompting vs Few-shot prompting | Zero-shot: no examples provided, relies on pretrained knowledge. Few-shot: 2-5 labeled examples included to demonstrate format/task. Exam tip: use few-shot for custom or non-standard output requirements. |
| 5 | How do you force an LLM API to return JSON matching an exact schema? | Use structured output: response_format={'type':'json_schema','json_schema': {...}, 'strict': true}. Exam tip: strict:true guarantees schema conformance via constrained decoding. |
| 6 | Which model type converts text into spoken audio? | Text-to-speech (TTS) API. Exam tip: don't confuse with speech-to-text (ASR), which does the reverse. |
| 7 | Which model type converts spoken audio into text? | Speech-to-text / Automatic Speech Recognition (ASR). Used before running text-based sentiment or chat pipelines on voice input. |
| 8 | Which API type generates images from text prompts? | Text-to-image generation API. Exam tip: distinct from chat completion and embeddings APIs — don't mix them up in service-selection questions. |
| 9 | response_format type 'json_object' vs 'json_schema' | 'json_object' only guarantees syntactically valid JSON with no structure enforcement. 'json_schema' with strict:true enforces exact field names and types. Exam tip: use json_schema when a downstream parser requires a fixed structure. |
| 10 | Basic GenAI application architecture pattern | Client → Prompt template/orchestration layer → LLM API call → optional structured-output parser → Application logic. Exam tip: keep prompt construction separate from business logic for maintainability. |
| 11 | When should you prefer few-shot over zero-shot prompting? | When the task needs a specific output format, uncommon categories, or consistent style the model can't infer alone. Exam tip: few-shot increases token usage and cost — a tradeoff often tested in scenarios. |
| 12 | Effect of high temperature (1.5-2.0) on output? | Increases randomness and creativity, producing more diverse but less predictable/accurate responses. Exam tip: avoid high temperature for factual Q&A or structured data extraction tasks. |
