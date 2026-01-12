Code Llama, a code generation model family derived from Llama 2 and released by Meta on August 24, 2023 (in 7B, 13B, 34B, and 70B parameter sizes), lacks major public security incidents specific to its core model. Vulnerabilities have primarily affected deployment frameworks like llama-stack rather than the model weights themselves. Literature focuses on its use for vulnerability detection and patching rather than flaws in Code Llama.

## Key Incidents
No CVEs or exploits directly target Code Llama's architecture; related issues include CVE-2024-50050 (disclosed September 2024) in Meta's Llama Stack inference server, enabling remote code execution via unsafe Python deserialization, applicable to Code Llama deployments.[1]
Trend Micro's 1H 2025 AI security report noted exposed Ollama servers (used for local Code Llama inference) vulnerable to unauthorized access, but no Code Llama-specific breaches.[2]

## Safety Reports
Sophos benchmarking (March 2024) ranked Code Llama-34B-Instruct at 85% accuracy in security incident analysis tasks, competitive with GPT-4 for threat investigation.[3]
Adversa AI's 2025 incidents report highlighted GenAI (including code models) in 70% of AI failures, but agentic systems caused more severe issues like supply chain attacks, without naming Code Llama.[6]

## Literature Overview
ArXiv paper "Llama-based source code vulnerability detection" (September 2025) fine-tuned Code Llama variants, achieving 0.997 AUC on BigVul dataset for vulnerability identification, outperforming CodeBERT.[4]
ScienceDirect study (2025) introduced PatchLM, a Code Llama fine-tune for generating security fixes in commit hunks.[7]

[1](https://thehackernews.com/2025/01/metas-llama-framework-flaw-exposes-ai.html)
[2](https://www.trendmicro.com/vinfo/us/security/news/threat-landscape/trend-micro-state-of-ai-security-report-1h-2025)
[3](https://www.sophos.com/es-es/blog/benchmarking-the-security-capabilities-of-large-language-models)
[4](https://arxiv.org/html/2512.09006v1)
[5](https://www.linkedin.com/pulse/ai-generated-code-risks-2024-2025-incidents-frameworks-faisal-yahya-qybxc)
[6](https://adversa.ai/blog/adversa-ai-unveils-explosive-2025-ai-security-incidents-report-revealing-how-generative-and-agentic-ai-are-already-under-attack/)
[7](https://www.sciencedirect.com/science/article/pii/S0950584925001259)
[8](https://www-cdn.anthropic.com/b2a76c6f6992465c09a6f2fce282f6c0cea8c200.pdf)
[9](https://www.oligo.security/blog/more-models-more-probllms)
[10](https://research.aimultiple.com/llms-in-cybersecurity/)
