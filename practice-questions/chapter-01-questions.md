## Chapter 1: Domain 1: Foundations of Modern AI for Developers — Practice Questions

**Q1.** A solo developer with no ML engineering background needs to add a text-summarization feature to a web app within one week. No internal company data needs to be incorporated into the model's behavior. Which developer entry point BEST fits this situation?

A) Train a transformer model from scratch on a labeled summarization dataset
B) Fine-tune an open-weight LLM on company support tickets
C) Call a pre-trained GenAI model through its API
D) Build a custom neural network architecture and train it on GPUs

<details>
<summary>Answer</summary>

**Correct: C**

API consumption is the entry point for developers who need GenAI capability fast with zero training infrastructure, and no customization to proprietary data is required here.

**Why the others are wrong:**
- Training from scratch requires massive datasets, compute, and ML expertise — far beyond a one-week solo timeline.
- Fine-tuning is unnecessary because the task doesn't require adapting the model to proprietary/internal data or tone.
- Building a custom architecture duplicates work already solved by existing pre-trained models and ignores the time constraint.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company wants an LLM-powered assistant to answer employee questions using the company's internal HR policy documents. The team has no ML engineers and a limited budget. Which approach BEST matches their constraints?

A) Use an existing GenAI model via API combined with a retrieval pipeline over the HR documents
B) Fine-tune a foundation model on the HR documents
C) Train a new language model from scratch using the HR documents
D) Wait until an ML engineer is hired before building anything

<details>
<summary>Answer</summary>

**Correct: A**

API consumption plus a retrieval/pipeline layer lets developers ground model answers in proprietary documents without any training expertise or GPU budget.

**Why the others are wrong:**
- Fine-tuning requires ML skills, curated training data, and compute budget the team doesn't have.
- Training from scratch is the most resource-intensive option and is never justified for this scenario.
- This isn't a valid engineering decision — the pipeline-building entry point exists specifically so non-ML teams can ship this today.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A developer reads that a vendor's chatbot 'generates new marketing copy that did not exist in its training data.' Which category of AI does this behavior place the chatbot in, within the AI > ML > DL hierarchy?

A) Classical machine learning
B) Rule-based expert system
C) Supervised classification
D) Generative AI, a subset of deep learning

<details>
<summary>Answer</summary>

**Correct: D**

Generating novel content (text, images, code) rather than predicting a label is the defining trait of Generative AI, which sits inside Deep Learning, which sits inside Machine Learning, which sits inside AI.

**Why the others are wrong:**
- Classical ML (e.g., linear regression, decision trees) typically predicts/classifies rather than generates novel content.
- Rule-based systems follow hand-coded logic, not learned weights, so they can't generate novel content this way.
- Supervised classification assigns inputs to predefined labels; it does not generate new content.

</details>

---

**Q4.** Which term refers to the numeric parameters a model learns during training and uses to compute predictions during inference?

A) Dataset
B) Weights
C) Epoch
D) Prompt

<details>
<summary>Answer</summary>

**Correct: B**

Weights are the adjustable numeric parameters inside a model that are updated during training and then held fixed (frozen) during inference.

**Why the others are wrong:**
- A dataset is the collection of examples used to train or evaluate a model, not the learned parameters themselves.
- An epoch is one full pass of the training data through the model, a unit of training time, not a parameter.
- A prompt is the input text given to a model at inference time, not a learned parameter.

</details>

---

**Q5.** Which field is the broadest umbrella term that encompasses Machine Learning, Deep Learning, and Generative AI as nested subsets?

A) Natural Language Processing (NLP)
B) Deep Learning
C) Generative AI
D) Artificial Intelligence (AI)

<details>
<summary>Answer</summary>

**Correct: D**

AI is the top-level umbrella; ML is a subset of AI, DL is a subset of ML, and GenAI is a subset of DL. NLP is a cross-cutting application area, not the top of the hierarchy.

**Why the others are wrong:**
- NLP is an application domain (working with human language) that uses ML/DL techniques — it isn't the umbrella term over the other categories.
- Deep Learning is a subset of Machine Learning (networks with many layers), not the broadest term.
- Generative AI is the narrowest of the four, sitting inside Deep Learning.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A candidate is scheduling their AT-310 exam attempt. According to the official exam format, what score is required to pass?

A) 50%
B) 70%
C) 60%
D) 80%

<details>
<summary>Answer</summary>

**Correct: B**

AT-310 requires a 70% passing score across 50 questions in a 90-minute window.

**Why the others are wrong:**
- 50% is below the stated passing threshold for AT-310.
- 60% is below the stated passing threshold for AT-310.
- 80% exceeds the actual documented passing threshold for AT-310.

</details>

---

**Q7.** During which phase of a model's lifecycle does a developer send a new, unseen input to a model and receive an output, without updating any of the model's weights?

A) Training
B) Fine-tuning
C) Inference
D) Dataset labeling

<details>
<summary>Answer</summary>

**Correct: C**

Inference is the phase where a trained model with frozen weights processes new input and produces output — this is what happens every time a developer calls a model API.

**Why the others are wrong:**
- Training is the phase where weights are learned/updated from a dataset, which does not happen on each API call.
- Fine-tuning further updates an already-trained model's weights on a new dataset — it also changes weights, unlike inference.
- Dataset labeling is a data preparation step that occurs before training, not an interaction with a trained model.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly describes the relationship between AI, ML, and Deep Learning?

A) Deep Learning is a subset of ML, which is a subset of AI
B) ML is a subset of Deep Learning, which is a subset of AI
C) AI, ML, and Deep Learning are three unrelated, parallel fields
D) AI is a subset of ML, and Deep Learning is a subset of AI

<details>
<summary>Answer</summary>

**Correct: A**

The correct nesting is AI ⊃ ML ⊃ DL ⊃ GenAI — each term is a more specialized subset of the one before it.

**Why the others are wrong:**
- This reverses the actual nesting order; ML is broader than Deep Learning, not narrower.
- These fields are not parallel/unrelated — they are nested subsets of one another.
- This reverses the hierarchy entirely; AI is the broadest term, not a subset of ML.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

