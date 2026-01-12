## SLM Model Catalog (7B-Class Focus)

SLM catalog covers ~7B parameter open-weight models (or small variants), highlighting key factors like permissive licenses, active communities, and low incident rates. Data draws from prior incident/literature reports; **commercial use often allowed** but with attribution; **most accessible via Hugging Face**.

| Model | Model Card Summary | License | Literature (Key Dates) | Incidents (Key Dates) | Commercial Restrictions | Attribution | Community Activity | Accessibility |
|-------|---------------------|---------|------------------------|-----------------------|--------------------------|-------------|---------------------|---------------|
| **Llama 3** (Meta, Apr 2024) | 8B base/instruct; multilingual; strong coding/math. **Key: Safety-tuned via Guard.** | Llama 3 Community License (permissive, research+commercial) | "Llama 3 Herd" paper (Jul 2024) [11]; Lakera risk report (May 2025) [12] | Jailbreak (Apr 2024) [13]; CVE-2024-50050 RCE (Sep-Oct 2024) [14] | None major; accept terms | "Powered by Llama" optional | **High**: 100M+ HF downloads; Ollama integration | [HF: meta-llama/Llama-3-8B](https://huggingface.co/meta-llama/Llama-3-8B); [Docs](https://llama.meta.com) |
| **Llama 4** (Meta, Apr 2025) | Scout/Maverick (MoE multimodal); 10M context. **Key: Frontier-level scale.** | Llama 4 Community License | "Llama 4 Challenges" (Apr 2025) [15]; Multimodal AI paper (Apr 2025) [16] | Jailbreak 67% ASR Scout (Jul 2025) [17]; CVE-2025-53002 (Jun 2025) [18] | Rate limits for large-scale | Recommended badge | **Very High**: Rapid adoption post-launch | [HF: meta-llama/Llama-4-Scout](https://huggingface.co/meta-llama); [Site](https://llama.meta.com) |
| **Code Llama** (Meta, Aug 2023) | 7/13/34/70B code-specialized from Llama 2. **Key: Fill-mask coding.** | Same as Llama 2 Community | PatchLM fixes paper (2025) [19]; Vuln detection (Sep 2025) [20] | Framework RCE (Jan 2025) [21]; no model-specific | None | "Built with Code Llama" | **High**: GitHub coding leader | [HF: codellama/CodeLlama-7b](https://huggingface.co/codellama); [Docs](https://ai.meta.com/llama) |
| **Mistral 7B** (Mistral AI, Sep 2023) | Efficient dense; v0.3 sliding window. **Key: Tops open LLM Arena.** | Apache 2.0 (**most permissive**) | Mistral frontier news (Sep 2023) [22] | CSAM gen in Pixtral (Jul 2025) [23]; policy update (Dec 2024) [24] | None | None required | **Very High**: Ollama default; 50M+ downloads | [HF: mistralai/Mistral-7B-v0.3](https://huggingface.co/mistralai); [Docs](https://mistral.ai) |
| **MPT-7B** (Databricks, May 2023) | 1T tokens trained; 65k context ALiBi. **Key: Early long-context.** | Apache 2.0 | Databricks blog (Nov 2025 update) [25]; CyberLLM safety (Aug 2024) [26] | None specific; OWASP general (2023+) [27] | None | None | **Medium**: Legacy but GGUF active | [HF: mosaicml/mpt-7b](https://huggingface.co/mosaicml); [Blog](https://databricks.com/blog/mpt-7b) |
| **Gemma-7B** (Google, Feb 2024) | Gemini-derived; safety classifiers. **Key: Lightweight rival to 70B.** | Gemma License (commercial ok) | Tech report (Mar 2024) [28]; Cyber incidents (Apr 2025) [29] | Gemini Trifecta indirect (Oct 2025) [30]; no direct | High-stakes review advised | "Made with Gemma" | **High**: Google ecosystem push | [HF: google/gemma-7b](https://huggingface.co/google/gemma-7b) [6]; [Docs](https://ai.google.dev/gemma) |
| **Phi-3 Mini** (Microsoft, Apr 2024) | 3.8B SLM; synthetic data tuned. **Key: Edge-first safety.** | MIT (**highly permissive**) | Tech report (Apr 2024) [31]; Azure safety (Jan 2025) [32] | None reported; strong RLHF [33] | Production safeguards urged | None | **High**: Azure/ONNX optimized | [HF: microsoft/Phi-3-mini](https://huggingface.co/microsoft); [Docs](https://azure.microsoft.com/phi-3) |
| **StableLM 7B** (Stability AI, Apr 2023) | Early open chat-tuned. **Key: Community fine-tunes.** | Stability AI License (CC-BY-SA-like) | Safety Index evals (Winter 2025) [34] | None specific; GenAI patterns [35] | Non-commercial core? (check) | Attribution required | **Medium**: Zephyr variant active | [HF: stabilityai/stablelm-7b](https://huggingface.co/stabilityai); [Docs](https://stability.ai/stablelm) |
| **Qwen 7B** (Alibaba, Apr 2023+) | Multilingual MoE; math/coding strong. **Key: Chinese-English balance.** | Apache 2.0 | Qwen2 tech report (Jun 2024) | Low jailbreak resistance (2024 evals) | None | Optional | **High**: Asia dev focus | [HF: Qwen/Qwen-7B](https://huggingface.co/Qwen); [Site](https://qwen.ai) |
| **StarCoder/Base** (BigCode, May 2023) | 15B code (use 7B equiv); 80+ langs. **Key: Permissive code data.** | BigCode OpenRAIL-M (restrict harmful) | StarCoder paper (Oct 2023) | Code vuln gen risks (2024) | No illegal code use | Cite BigCode | **High**: Coding hub | [HF: bigcode/starcoder](https://huggingface.co/bigcode); [Docs](https://starcoder.org) |
| **CodeGen-2** (Salesforce, Aug 2022) | Multi-turn code; 7B/16B. **Key: Early infill.** | Salesforce License (research focus) | CodeGen paper (Mar 2022) | General code risks | Commercial limited | Attribution | **Low-Medium**: Legacy | [HF: Salesforce/codegen-7B](https://huggingface.co/Salesforce) |
| **CodeParrot** (HF, Mar 2022) | GitHub-trained code. **Key: Repo-level.** | Apache 2.0 | CodeParrot paper (2022) | Vuln insertion (2023 studies) | None | None | **Low**: Superseded | [HF: codeparrot/codeparrot](https://huggingface.co/codeparrot) |
| **RWKV 7B** (RWKV, 2023 variants) | RNN-LM hybrid; infinite ctx. **Key: GPU-efficient.** | Apache 2.0 | RWKV v4 paper (2023); v6 (2024) | Few; stable RNN arch | None | Cite RWKV | **Medium**: RNN niche | [HF: RWKV/rwkv-7b](https://huggingface.co/RWKV); [Docs](https://rwkv.com) |
| **Falcon-7B** (TII, May 2023) | RefinedWeb trained. **Key: Early SOTA open.** | Apache 2.0 | Falcon paper (May 2023) | Early jailbreaks (2023) | None | None | **Medium**: Chat variants | [HF: tiiuae/falcon-7b](https://huggingface.co/tiiuae); [Site](https://falconllm.tii.ae) |
| **RedPajama-7B** (Together, Mar 2023) | LLaMA dupereplica; 1T tokens. **Key: Open data recipe.** | Apache 2.INC | RedPajama paper (Apr 2023) | Data poisoning risks | None | Cite dataset | **Medium**: Base for fine-tunes | [HF: togethercomputer/RedPajama](https://huggingface.co/togethercomputer) |

## Key Highlights
- **Safest for Commercial**: **Mistral/Phi-3/Qwen** (Apache/MIT; zero restrictions).
- **Highest Incidents**: Llama series (framework CVEs, jailbreaks); **code models** risk vuln gen.
- **Most Active Communities**: Llama/Mistral/Gemma (HF stars >1M, Ollama defaults).
- **Edge-Friendly**: Phi-3/Gemma (quantized, <5GB RAM).
- **Download Tip**: All primary on Hugging Face; use `ollama pull` for local (e.g., `ollama pull mistral:7b`). Check licenses for derivatives.[3]

[1](https://github.com/ggml-org/llama.cpp/discussions/3847)
[2](https://github.com/ggerganov/llama.cpp/discussions/3847)
[3](https://github.com/ollama/ollama/tree/main?tab=readme-ov-file)
[4](https://github.com/ollama/ollama/blob/main/README.md)
[5](https://ollama.com/library/mistral:7b/blobs/ff82381e2bea)
[6](https://huggingface.co/google/gemma-7b)
[7](https://huggingface.co/docs/transformers/en/model_doc/gemma)
[8](https://github.com/hiyouga/LLaMA-Factory/releases)
[9](https://www.ollama.com/library/mistral:7b/blobs/ff82381e2bea)
[10](https://www.llama.com)
[11](https://arxiv.org/abs/2407.21783)
[12](https://www.lakera.ai/model-card/llama-3-1-8b-instruct-risk-report)
[13](https://favtutor.com/articles/meta-llama-3-jailbreak/)
[14](https://www.oligo.security/blog/cve-2024-50050-critical-vulnerability-in-meta-llama-llama-stack)
[15](https://cameronrwolfe.substack.com/p/llama-4)
[16](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5208228)
[17](https://protectai.com/blog/vulnerability-assessment-llama-4)
[18](https://nvd.nist.gov/vuln/detail/CVE-2025-53002)
[19](https://www.sciencedirect.com/science/article/pii/S0950584925001259)
[20](https://arxiv.org/html/2512.09006v1)
[21](https://thehackernews.com/2025/01/metas-llama-framework-flaw-exposes-ai.html)
[22](https://mistral.ai/news/about-mistral-ai)
[23](https://www.bankinfosecurity.com/mistral-ai-models-fail-key-safety-tests-report-finds-a-28358)
[24](https://mistral.ai/legal/child-abuse)
[25](https://www.databricks.com/blog/mpt-7b)
[26](https://arxiv.org/html/2503.09334)
[27](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
[28](https://arxiv.org/html/2403.08295v1)
[29](https://arxiv.org/pdf/2504.13196.pdf)
[30](https://www.tenable.com/blog/the-trifecta-how-three-new-gemini-vulnerabilities-in-cloud-assist-search-model-and-browsing)
[31](https://arxiv.org/abs/2404.14219)
[32](https://azure.microsoft.com/en-us/blog/introducing-phi-3-redefining-whats-possible-with-slms/)
[33](https://news.microsoft.com/source/features/ai/the-phi-3-small-language-models-with-big-potential/)
[34](https://futureoflife.org/ai-safety-index-winter-2025/)
[35](https://wald.ai/blog/gen-ai-security-breaches-timeline-20232025-recurring-mistakes-are-the-real-threat)
