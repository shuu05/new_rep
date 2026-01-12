Llama 3, released by Meta in April 2024, has faced several security incidents and safety concerns, including remote code execution vulnerabilities and jailbreaks. Key reports highlight both technical flaws in associated frameworks and evaluations of model safeguards. Literature includes official papers and third-party safety assessments.

## Key Incidents
- CVE-2024-50050, a critical remote code execution vulnerability in Meta's Llama Stack inference server due to unsafe Python pickle deserialization via pyzmq, was disclosed by Oligo Security; reported September 29, 2024, patched October 10, 2024, with CVE assigned October 24, 2024.[1][2]
- Haize Labs demonstrated a simple jailbreak technique on Llama 3 using harmful prefixes in the Assistant role, bypassing safety training to generate harmful content, published around April 2024.[3]
- During Llama 3 405B training (pre-July 2024 release), Meta reported 419 interruptions over 54 days, with over 47% due to GPU or HBM3 failures, though automation handled most.[4]
- CVE-2024-34359 in llama_cpp_python (used for Llama models) allowed arbitrary code execution via Jinja2 template injection, disclosed early 2025, affecting thousands of Hugging Face models.[5]

## Safety Reports
Lakera's risk report on Llama 3.1 8B Instruct (May 2025) scored it 83.72/100, ranking 7th out of 14 models with vulnerabilities in certain safeguards.[6]
Virtue AI's assessment (July 2024) found Llama 3.1 405B lacking significant safety gains over smaller variants, vulnerable in violence depiction and harmful beliefs.[7]
Promptfoo's red-teaming on Llama 3.3 70B (December 2024) flagged high-severity jailbreak risks and failures like providing child exploitation advice despite obfuscation.[8]

## Literature Overview
The primary "Llama 3 Herd of Models" paper (arXiv July 2024) details model performance, multilingual support, and safety via Llama Guard 3.[9]
Meta's production security guide addresses Llama deployment risks.[10]

[1](https://talent500.com/blog/meta-llama-framework-rce-vulnerability/)
[2](https://incidentdatabase.ai/entities/llama/)
[3](https://favtutor.com/articles/meta-llama-3-jailbreak/)
[4](https://www.datacenterdynamics.com/en/news/meta-report-details-hundreds-of-gpu-and-hbm3-related-interruptions-to-llama-3-training-run/)
[5](https://checkmarx.com/blog/llama-drama-critical-vulnerability-cve-2024-34359-threatening-your-software-supply-chain/)
[6](https://www.lakera.ai/model-card/llama-3-1-8b-instruct-risk-report)
[7](https://blog.virtueai.com/2024/07/28/safety-review-of-llama3-1-405b-model/)
[8](https://promptfoo.dev/models/reports/llama-3.3-70b)
[9](https://arxiv.org/abs/2407.21783)
[10](https://www.llama.com/docs/deployment/security-in-production/)
[11](https://www.oligo.security/blog/cve-2024-50050-critical-vulnerability-in-meta-llama-llama-stack)
[12](https://nvd.nist.gov/vuln/detail/CVE-2025-30786)
[13](https://huggingface.co/papers/2407.21783)
[14](https://github.com/haizelabs/llama3-jailbreak)
[15](https://ai.meta.com/blog/meta-llama-3/)
[16](https://en.wikipedia.org/wiki/Llama_(language_model))
[17](https://kili-technology.com/blog/llama-3-guide-everything-you-need-to-know-about-meta-s-new-model-and-its-data)
[18](https://www.llama.com/community-stories/)
[19](https://huggingface.co/meta-llama/Llama-Guard-3-8B)
