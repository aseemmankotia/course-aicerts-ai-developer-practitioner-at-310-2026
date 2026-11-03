## Chapter 9: Domain 9: Generative and Multimodal AI Application Development — Practice Questions

**Q1.** A company is building a customer support bot that must give consistent, repeatable answers to FAQ-type questions, with minimal creative variation. Which parameter configuration BEST meets this requirement?

A) temperature=0.1, top_p=1.0
B) temperature=1.2, top_p=1.0
C) temperature=1.0, top_p=0.1
D) temperature=2.0, top_p=0.5

<details>
<summary>Answer</summary>

**Correct: A**

Low temperature (near 0) makes the model favor the highest-probability token, producing deterministic, repeatable output while leaving top_p at its default so it doesn't interfere.

**Why the others are wrong:**
- High temperature (1.2) increases randomness, the opposite of what's needed for consistency.
- Adjusting only top_p while leaving temperature at default still allows significant randomness and mixes two randomness controls, which official guidance advises against doing simultaneously.
- Temperature=2.0 is the maximum randomness setting, producing highly variable, inconsistent answers.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A developer needs an LLM to always return a JSON object with specific field names and types for a downstream parser that throws an error on any malformed or extra content. Which approach BEST ensures this?

A) Use the API's structured output feature with a defined JSON schema and strict mode enabled
B) Add the instruction 'Please respond in JSON format' to the end of the prompt
C) Set temperature to 0 and hope the formatting stays consistent
D) Parse the response with regex to extract JSON substrings after the fact

<details>
<summary>Answer</summary>

**Correct: A**

Structured output with a JSON schema and strict mode constrains decoding so the response conforms exactly to the defined fields and types, eliminating extra text or format drift.

**Why the others are wrong:**
- A plain text instruction is not enforced by the API and can still produce extra commentary or malformed JSON.
- Temperature=0 reduces randomness but does not guarantee schema conformance; the model can still omit or mislabel fields.
- Regex extraction is a brittle workaround that doesn't prevent malformed JSON in the first place.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A developer wants a model to classify customer emails into five non-standard, company-specific categories that the model has no prior knowledge of, using only a single prompt with no fine-tuning. Which technique is MOST appropriate?

A) Zero-shot prompting with just the category names listed
B) Increasing temperature to improve category diversity
C) Few-shot prompting with 2-3 labeled examples showing the exact categories and expected output format
D) Fine-tuning a dedicated model for each category

<details>
<summary>Answer</summary>

**Correct: C**

Few-shot prompting provides concrete labeled examples that teach the model the exact custom categories and output format it couldn't infer from pretraining alone.

**Why the others are wrong:**
- Zero-shot relies on the model's existing knowledge, which doesn't include these custom, non-standard categories.
- Temperature controls randomness, not classification accuracy or category understanding.
- Fine-tuning per category is unnecessary overhead when few-shot prompting solves the problem with a single API call.

</details>

---

**Q4.** Which type of model/API should be used to convert spoken customer feedback recordings into text before running sentiment analysis?

A) Speech-to-text (automatic speech recognition) model
B) Text-to-speech (TTS) model
C) Image generation model
D) Embedding model

<details>
<summary>Answer</summary>

**Correct: A**

Speech-to-text (ASR) models convert audio into text, which is the required input format for a subsequent text-based sentiment analysis step.

**Why the others are wrong:**
- Text-to-speech does the reverse operation — converting text into audio, not audio into text.
- Image generation models handle visual content and are unrelated to audio processing.
- Embedding models convert text into vector representations for similarity/search, not audio into text.

</details>

---

**Q5.** A design team needs to generate product mockup images from written text descriptions for a prototyping app. Which API category is appropriate?

A) Chat completions API
B) Text-to-image generation API
C) Speech synthesis (TTS) API
D) Embeddings API

<details>
<summary>Answer</summary>

**Correct: B**

Text-to-image generation APIs are specifically designed to produce visual images from natural language prompts.

**Why the others are wrong:**
- Chat completions APIs generate text responses, not images.
- Speech synthesis converts text into spoken audio, not visual content.
- Embeddings APIs produce numeric vector representations for search/similarity, not images.

</details>

---

**Q6.** In an OpenAI-style structured output request, what does setting 'strict': true in the json_schema response_format accomplish?

A) It makes the model respond faster by skipping validation
B) It guarantees the model's output strictly conforms to the provided schema's field names and types
C) It increases the maximum token limit for the response
D) It disables temperature-based sampling entirely

<details>
<summary>Answer</summary>

**Correct: B**

Strict mode constrains the model's decoding process to guarantee the output matches the exact schema structure and data types defined by the developer.

**Why the others are wrong:**
- Strict mode is about output conformance, not response latency.
- It has no effect on token limits, which are set separately.
- Temperature still applies to token selection; strict mode only constrains the output structure, not the sampling method.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A developer sets top_p=0.1 in an API call. What does this configure?

A) The model will generate at most 10 output tokens
B) The model will use only 10% of the available context window
C) The model will only consider tokens from the smallest set whose cumulative probability reaches 10% (nucleus sampling)
D) The response will have a 10% chance of being returned in JSON format

<details>
<summary>Answer</summary>

**Correct: C**

top_p implements nucleus sampling: the model restricts token selection to the smallest subset whose cumulative probability mass is at least the top_p value, narrowing options to the most likely tokens.

**Why the others are wrong:**
- top_p does not limit the number of output tokens; that is controlled by a max_tokens-style parameter.
- top_p has no relation to context window size.
- top_p controls sampling diversity, not output format.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the key difference between zero-shot and few-shot prompting?

A) Zero-shot provides no task examples in the prompt; few-shot includes a small number of labeled examples to guide output
B) Zero-shot requires fine-tuning; few-shot does not
C) Zero-shot uses temperature=0; few-shot uses temperature=1
D) Zero-shot only works with image models; few-shot only works with text models

<details>
<summary>Answer</summary>

**Correct: A**

Zero-shot prompting relies entirely on the model's pretrained knowledge with no examples given; few-shot prompting includes a handful of labeled examples in the prompt to demonstrate the desired task, format, or categories.

**Why the others are wrong:**
- Neither technique requires fine-tuning — both are prompt-time strategies.
- Temperature is an unrelated sampling parameter, not tied to the shot count.
- Both techniques apply to text, image, and other modalities, not restricted to one type.

</details>

---

