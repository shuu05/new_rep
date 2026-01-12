Llama 4, Meta's multimodal AI suite including Scout, Maverick, and Behemoth models, launched in April 2025 with Mixture-of-Experts architecture and 10M token context. It faced safety critiques for jailbreak vulnerabilities and prompt injection risks, alongside some framework-related CVEs. Literature covers architecture analyses and security evaluations.[1][2]

## Key Incidents
- Protect AI vulnerability assessment (July 15, 2025) found Llama 4 Scout with 67.3% jailbreak attack success rate and 64.1% prompt injection rate; Maverick showed medium risk overall at 52-58%.[3]
- Reddit red-teaming discussions (April 7, 2025) highlighted multi-turn jailbreaks as a major weakness, where extended deceptive prompts bypassed guardrails.[4]
- CVE-2025-53002, a remote code execution flaw in LLaMA-Factory (used for Llama training) up to v0.9.3, disclosed June 25, 2025.[5]
- Detoxio evaluation (July 27, 2025) reported Llama Guard 4 blocking only 58.2% of adversarial jailbreak prompts (41.8% success rate).[6]

## Safety Reports
Meta's AI safety claims analysis (April 2025) evaluated Llama 4 for cyber risks, concluding no capabilities enabling catastrophic cyberattacks.[7]
Prisma AI security post (July 15, 2025) noted Llama Guard 4 blocks 66.2% of attacks but 33.8% harmful prompts bypass, emphasizing jailbreak and evasion hotspots.[8]

## Literature Overview
"Llama 4: The Challenges of Creating a Frontier-Level LLM" (April 27, 2025) details MoE architecture shift, early fusion multimodality, and scale increases over Llama 3.[9]
"Meta Llama 4: The Future of Multimodal AI" paper (April 6, 2025) explores capabilities in text, video, images, and audio processing.[10]

[1](https://currentaffairs.adda247.com/meta-launches-llama-4-ai-suite-scout-maverick-behemoth-to-rival-chatgpt-gemini/)
[2](https://www.reuters.com/technology/meta-releases-new-ai-model-llama-4-2025-04-05/)
[3](https://protectai.com/blog/vulnerability-assessment-llama-4)
[4](https://www.reddit.com/r/LocalLLaMA/comments/1jtelqu/red_teaming_llama4s_safety_guardrails/)
[5](https://nvd.nist.gov/vuln/detail/CVE-2025-53002)
[6](https://www.detoxio.ai/platform/evaluation-report-robustness-of-meta-llama-guard-4)
[7](https://aisafetyclaims.org/companies/meta)
[8](https://www.linkedin.com/posts/prisma-airs-by-palo-alto-networks_aisecurity-llm-llama4-activity-7351323475891929088-kvS1)
[9](https://cameronrwolfe.substack.com/p/llama-4)
[10](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5208228)
[11](https://techcrunch.com/2025/04/05/meta-releases-llama-4-a-new-crop-of-flagship-ai-models/)
[12](https://talent500.com/blog/meta-llama-framework-rce-vulnerability/)
[13](https://www.packetlabs.net/posts/llama-cve-exposes-ai-apps-to-remote-code-execution/)
[14](https://arxiv.org/html/2308.03825v2)
[15](https://blogs.cisco.com/security/bypassing-metas-llama-classifier-a-simple-jailbreak)
[16](https://huggingface.co/meta-llama)
[17](https://blog.virtueai.com/2024/07/28/safety-review-of-llama3-1-405b-model/)
[18](https://www.cve.org/CVERecord/SearchResults?query=CVE-2025-53002)
