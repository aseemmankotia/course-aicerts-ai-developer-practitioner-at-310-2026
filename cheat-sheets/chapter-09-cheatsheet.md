# Domain 9 Cheat Sheet: Generative & Multimodal AI Dev (8%)

## Generation Parameters
| Parameter | Range/Default | Effect | Exam Rule |
|---|---|---|---|
| temperature | 0–2, default 1 | Lower = deterministic/focused; higher = creative/random | Use low temp for factual tasks, high for creative |
| top_p (nucleus) | 0–1, default 1 | Restricts sampling to smallest token set reaching cumulative prob ≥ p | Don't tune temperature AND top_p together |

**Gotcha:** Changing both temperature and top_p simultaneously is discouraged — exam favors answers that adjust only one.

## Prompting Techniques
| Technique | Definition | Use Case |
|---|---|---|
| Zero-shot | No examples in prompt, relies on pretrained knowledge | Common/general tasks the model already understands |
| Few-shot | 2–5 labeled examples included in prompt | Custom categories, specific formats, non-standard outputs |

**Gotcha:** Few-shot increases prompt length/cost — exam may test this tradeoff in scenario questions.

## Structured JSON Output
```json
{
  "response_format": {
    "type": "json_schema",
    "json_schema": {
      "name": "result",
      "strict": true,
      "schema": {
        "type": "object",
        "properties": {
          "category": {"type": "string"},
          "confidence": {"type": "number"}
        },
        "required": ["category", "confidence"],
        "additionalProperties": false
      }
    }
  }
}
```
- `json_object` type → only guarantees valid JSON syntax, no schema enforcement.
- `json_schema` + `strict:true` → guarantees exact field names/types via constrained decoding.

**Gotcha:** A plain-text instruction like "respond in JSON" is NOT enforced — model can still add commentary or break format.

## Modality API Selection
| Need | API Category |
|---|---|
| Text → structured/chat response | Chat/completions API |
| Text → image | Text-to-image generation API |
| Audio → text | Speech-to-text (ASR, e.g., Whisper-style) |
| Text → audio | Text-to-speech (TTS) |
| Text → vector for search/similarity | Embeddings API |

**Gotcha:** Exam often swaps TTS and ASR direction in distractors — read carefully which direction (text→audio or audio→text) is required.

## Simple GenAI App Architecture
```
Client Request
  → Prompt Template / Orchestration Layer
    → LLM API Call (with parameters: temperature, top_p, response_format)
      → Structured Output Parser (if JSON schema used)
        → Application Business Logic / Downstream System
```
**Design Principle:** Separate prompt construction from business logic for maintainability and easier testing of prompt variants.

## Quick Memory Tricks
- **Temperature = Thermostat** → turn it down (low) for cold, consistent, factual answers; turn it up (high) for hot, creative, varied answers.
- **Few-shot = "Follow my Format"** → give examples when you need a precise/custom structure.
- **Strict Schema = Straightjacket** → output cannot escape the defined shape.
