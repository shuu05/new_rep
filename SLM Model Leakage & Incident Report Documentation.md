<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

## SLM Model Leakage \& Incident Report Documentation

This documentation compiles **data leakage incidents** (e.g., training data memorization/extraction, PII exposure) and **security incidents** (e.g., jailbreaks, CVEs, exploits) for each model from conversation history. **Key factors highlighted**: No model had catastrophic breaches; **framework vulns** > model weights; **code models** risk vuln insertion; **leakage low in SLMs** due to smaller size/data.

### Llama 3 (Meta, Apr 2024)

**Leakage**: None reported; general LLM repetition tests apply but Llama Guard 3 mitigated training data extraction.[^11]
**Incidents**:

- **Jailbreak**: Haize Labs prefix trick (Apr 2024) bypassed safety.[^12]
- **CVE-2024-50050**: RCE in llama-stack via pickle deserialization (Sep 29, 2024 disclosure; Oct 24 CVE).[^13][^14]
- **Training disruptions**: 419 GPU/HBM3 failures (pre-Jul 2024).[^15]
**Severity**: Medium; framework-focused.


### Llama 4 (Meta, Apr 2025)

**Leakage**: System prompt extraction high-risk (Lakera: 84.4/100 DIO/IIO); no PII dumps confirmed.[^3]
**Incidents**:

- **Jailbreak/Prompt Inj**: Scout 67.3% ASR, 64.1% injection; Maverick 52-58% risk (Jul 15, 2025).[^1]
- **Guardrail Bypass**: Llama Guard 4 blocked 66.2%, failed 33.8% incl. 63.4% injection (Jul 2025).[^16][^17]
- **CVE-2025-53002**: RCE in LLaMA-Factory (Jun 25, 2025).[^18]
- **Red-teaming**: 21.7% pass rate; critical in Pliny injections (Apr 2025).[^2]
**Severity**: **High**; multimodal amplified risks.


### Code Llama (Meta, Aug 2023)

**Leakage**: Code vuln datasets risked repo/PII memorization; PatchLM study showed extraction in fixes (2025).[^19]
**Incidents**:

- **Framework RCE**: Llama-stack CVE-2024-50050 (Jan 2025 coverage).[^5]
- **Ollama exposures**: Unauthorized access on exposed servers (1H 2025).[^20]
**Severity**: Low; no model-core exploits.


### Mistral (7B, Sep 2023)

**Leakage**: Multimodal Pixtral prone to CSAM recreation from descriptions (60x peers).[^21]
**Incidents**:

- **Safety Fail**: Pixtral CSAM/dangerous content (Jul 2025); policy update Dec 2024.[^22]
- **General**: Model inversion/evasion risks (Jan 2026).[^23]
**Severity**: Medium; content-focused.


### MPT-7B (Databricks, May 2023)

**Leakage**: None specific; CyberLLMInstruct showed fine-tune data poisoning extraction (Aug 2024).[^24]
**Incidents**: Zero model-specific; OWASP general risks.[^25]
**Severity**: **Very Low**; legacy stability.

### Gemma-7B (Google, Feb 2024)

**Leakage**: Indirect via Gemini Trifecta (prompts leaked user data, Oct 2025).[^26]
**Incidents**:

- **Gemini Suite Vulns**: Cloud Assist injection/API abuse (Oct 2025).
- **GenAI Patterns**: Prompt injection in timelines (2023-2025).[^27]
**Severity**: Low; lineage-related.


### Phi-3 Mini (Microsoft, Apr 2024)

**Leakage**: None; synthetic data + RLHF minimized memorization.[^28]
**Incidents**: Zero reported; safety evals passed internal red-teaming.[^29][^30]
**Severity**: **Negligible**; edge safeguards.

### StableLM (Stability AI, Apr 2023)

**Leakage**: Potential in early chat-tunes; GenAI timelines note patterns (2023-2025).[^27]
**Incidents**: None specific; Safety Index flagged reporting gaps (Winter 2025).[^31]
**Severity**: Low.

## Additional Models (From Catalog; Limited Incident Data)

| Model | Leakage | Key Incidents | Severity |
| :-- | :-- | :-- | :-- |
| **Qwen 7B** | Low multilingual PII risk | Jailbreak evals (2024); no CVEs | Low |
| **StarCoder/Base** | Code repo leaks (2023 studies) | Vuln gen risks; no exploits | Medium |
| **CodeGen-2** | Early infill memorization | General code risks (2022-24) | Low |
| **CodeParrot** | GitHub data extraction | Vuln insertion studies (2023) | Medium |
| **RWKV 7B** | Minimal (RNN arch) | Few; stable (2023-24) | Very Low |
| **Falcon-7B** | Early data poisoning | Jailbreaks (2023) | Low |
| **RedPajama-7B** | Dataset duplication risks | Poisoning concerns (2023) | Low |

**Key Trends**: **Llama series** dominates incidents (framework RCE, high jailbreak ASRs); **SLMs like Phi-3/MPT** near-zero; **code models** leak via generation not weights. Mitigation: Use guards (LlamaFirewall); monitor OWASP LLM Top 10. No confirmed PII mass-leaks across all.[^7][^25]
<span style="display:none">[^10][^4][^6][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://protectai.com/blog/vulnerability-assessment-llama-4

[^2]: https://www.promptfoo.dev/models/reports/llama-4-scout

[^3]: https://www.lakera.ai/model-card/meta-llama-4-maverick-risk-report

[^4]: https://www.techradar.com/pro/security/meta-llama-llm-security-flaw-could-let-hackers-easily-breach-systems-and-spread-malware

[^5]: https://thehackernews.com/2025/01/metas-llama-framework-flaw-exposes-ai.html

[^6]: https://cybersecuritynews.com/metas-llama-framework-vulnerability/

[^7]: https://www.llama.com/llama-protections/

[^8]: https://www.scram-pra.org/cyberseceval3.html

[^9]: https://www.vcindi.com/2025/01/security-vulnerabilities-in-metas-llama.html

[^10]: https://ai.meta.com/blog/ai-defenders-program-llama-protection-tools/

[^11]: https://arxiv.org/abs/2407.21783

[^12]: https://favtutor.com/articles/meta-llama-3-jailbreak/

[^13]: https://www.oligo.security/blog/cve-2024-50050-critical-vulnerability-in-meta-llama-llama-stack

[^14]: https://talent500.com/blog/meta-llama-framework-rce-vulnerability/

[^15]: https://www.datacenterdynamics.com/en/news/meta-report-details-hundreds-of-gpu-and-hbm3-related-interruptions-to-llama-3-training-run/

[^16]: https://www.detoxio.ai/platform/evaluation-report-robustness-of-meta-llama-guard-4

[^17]: https://www.linkedin.com/posts/prisma-airs-by-palo-alto-networks_aisecurity-llm-llama4-activity-7351323475891929088-kvS1

[^18]: https://nvd.nist.gov/vuln/detail/CVE-2025-53002

[^19]: https://www.sciencedirect.com/science/article/pii/S0950584925001259

[^20]: https://www.trendmicro.com/vinfo/us/security/news/threat-landscape/trend-micro-state-of-ai-security-report-1h-2025

[^21]: https://www.bankinfosecurity.com/mistral-ai-models-fail-key-safety-tests-report-finds-a-28358

[^22]: https://mistral.ai/legal/child-abuse

[^23]: https://www.practical-devsecops.com/ai-security-system-attacks/

[^24]: https://arxiv.org/html/2503.09334

[^25]: https://owasp.org/www-project-top-10-for-large-language-model-applications/

[^26]: https://www.tenable.com/blog/the-trifecta-how-three-new-gemini-vulnerabilities-in-cloud-assist-search-model-and-browsing

[^27]: https://wald.ai/blog/gen-ai-security-breaches-timeline-20232025-recurring-mistakes-are-the-real-threat

[^28]: https://arxiv.org/abs/2404.14219

[^29]: https://news.microsoft.com/source/features/ai/the-phi-3-small-language-models-with-big-potential/

[^30]: https://azure.microsoft.com/en-us/blog/introducing-phi-3-redefining-whats-possible-with-slms/

[^31]: https://futureoflife.org/ai-safety-index-winter-2025/

