## Chapter 12: Domain 12: Responsible AI, Security, Monitoring, and Capstone — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Direct vs. indirect prompt injection — what's the difference? | Direct: attacker types the malicious instruction straight into the chat input. Indirect: malicious instructions are hidden in external/retrieved content (documents, web pages, emails) processed via RAG or tools. Exam tip: indirect injection is the harder-to-detect, more heavily tested variant. |
| 2 | Which Azure feature automatically detects prompt injection attacks? | Azure AI Content Safety — Prompt Shields. Detects both direct (jailbreak) and indirect (document-based) injection attempts. |
| 3 | Best practice for storing Azure OpenAI API keys in production? | Store in Azure Key Vault and access via Managed Identity. Never hardcode keys in source code, config files, or client-side code. |
| 4 | What is 'spotlighting' as an injection mitigation technique? | Wrapping untrusted/retrieved content in clear delimiters (e.g., XML tags) and instructing the model to treat it as data, not instructions. Reduces indirect injection risk. |
| 5 | Microsoft's Responsible AI principles (list all six)? | Fairness, Reliability & Safety, Privacy & Security, Inclusiveness, Transparency, Accountability. Exam tip: group as People (fairness, inclusiveness), Trust (reliability, privacy, transparency), Governance (accountability). |
| 6 | What is 'model drift' in monitoring deployed AI models? | Performance degradation over time as real-world input distribution diverges from training/baseline data. Mitigate with scheduled evaluation against a baseline dataset plus alerting. |
| 7 | Managed Identity vs. Service Principal with client secret — which is preferred? | Managed Identity — no secret to store, rotate, or leak. Service Principal with a client secret requires manual secret management. Exam favors Managed Identity as best practice. |
| 8 | Where should connection strings/secrets live for an Azure App Service in production? | Azure Key Vault, referenced via Key Vault references in App Settings, accessed through Managed Identity — not in appsettings.json or committed config files. |
| 9 | Which services provide telemetry (requests, latency, errors) for monitoring a deployed AI app? | Azure Monitor + Application Insights. Used to build dashboards and alerts for usage, errors, and drift/failure detection. |
| 10 | Why is indirect prompt injection the most heavily tested AT-310 security topic? | RAG apps routinely ingest untrusted external content (docs, web, email) as part of normal operation, making attacks easy to hide without input isolation and content filtering. |
| 11 | What artifact demonstrates the 'Transparency' Responsible AI principle? | Model cards / documentation describing capabilities, limitations, and intended use. Exam tip: Transparency = disclosure/explainability, not accuracy. |
| 12 | How do you validate 'fairness' in a capstone AI solution before deployment? | Run bias evaluation across demographic/subgroup segments using fairness metrics (e.g., disparate impact), not just overall accuracy. |
