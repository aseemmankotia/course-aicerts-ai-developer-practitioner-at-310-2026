## Chapter 12 Cheat Sheet: Responsible AI, Security, Monitoring, Capstone

### Microsoft Responsible AI Principles
| Principle | Focus | Artifact/Check |
|---|---|---|
| Fairness | Equitable outcomes across groups | Bias metrics across subgroups |
| Reliability & Safety | Consistent, safe behavior | Testing, fallback handling |
| Privacy & Security | Data protection, access control | Key Vault, encryption, RBAC |
| Inclusiveness | Serves diverse users/abilities | Accessibility review |
| Transparency | Explainability, disclosure | Model cards, documentation |
| Accountability | Human oversight, governance | Audit logs, review process |

### Prompt Injection
| Type | Source | Example | Mitigation |
|---|---|---|---|
| Direct | User types it | "Ignore previous instructions..." | Instruction hierarchy in system message + Prompt Shields |
| Indirect | Retrieved/external content | Hidden text in a PDF/webpage | Spotlighting (delimiters), isolate untrusted content as data, Prompt Shields |

**Key Azure feature:** Azure AI Content Safety → **Prompt Shields** — detects direct + indirect injection.

### Secrets Management
| Do | Don't |
|---|---|
| Store secrets in Azure Key Vault | Hardcode keys in source code |
| Use Managed Identity to access Key Vault | Store client secrets in appsettings.json |
| Reference Key Vault secrets via App Settings | Commit keys to source control |
| Rotate keys periodically | Embed keys in client-side code |

**Managed Identity > Service Principal w/ secret** — no credential to manage, rotate, or leak.

### Monitoring Deployed Models
| Concern | Tooling | Action |
|---|---|---|
| Requests, latency, errors | Azure Monitor + Application Insights | Dashboards, alerts |
| Model/data drift | Scheduled evaluation vs. baseline dataset | Alert on metric degradation |
| Content safety failures | Azure AI Content Safety logs | Review flagged content |
| Cost/usage spikes | Azure Monitor metrics | Budget alerts |

### Exam Gotchas
- Indirect injection (via RAG/retrieved docs) is tested MORE than direct injection — don't assume "prompt injection" always means user-typed text.
- Prompt Shields ≠ Azure Monitor — Shields are content-classification security; Monitor is telemetry/observability.
- Managed Identity is almost always the "best practice" answer over keys/secrets/service principals when the scenario involves Azure-to-Azure auth.
- Drift = distribution/performance shift over time; NOT the same as a one-time content safety failure.
- Transparency = documentation/explainability; Fairness = equitable outcomes — exam frequently swaps these in distractors.

### Capstone & Exam Strategy
- Capstone integrates: prompt engineering, RAG grounding, security (Key Vault/Managed Identity), content safety, and monitoring — expect scenario questions spanning multiple domains.
- Time management: flag and skip long scenario questions, return after finishing shorter ones; budget ~1–1.5 min/question and reserve 10 min for review.
