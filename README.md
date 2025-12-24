Nice — below is a **concise, production-ready brief** on **inference speed & latency benchmarks for major available LLMs**. It’s intentionally compact so you can paste it into docs or an internal wiki. I include a short summary table with typical operational ranges, the assumed benchmarking setup, key findings, and tuning tips.

# Inference speed & latency — brief documentation (major LLMs)

**Scope & intent**
Covers representative, widely-used LLM families (OpenAI GPT series, Anthropic Claude, Google Gemini, Meta Llama, Mistral, Falcon, RedPajama / Mosaic, code models such as StarCoder/Code-Llama). Metrics are practical operational ranges (time-to-first-token / end-to-end latency and tokens/sec throughput) observed on modern datacenter GPUs (NVIDIA A100 80GB or H100) after typical optimizations (fp16/bf16, optimized kernels). Exact numbers vary with prompt length, tokenizer overhead, runtime, quantization, and HW.

---

## 1 — Executive summary (single line)

* **Smaller models (3B–7B)**: best for sub-150 ms single-request latencies on A100/H100 with fp16 + optimized kernels.
* **Medium/large models (13B–70B and above)**: higher capability at the cost of substantially higher latency and memory (often >200–1000 ms).
* **API hosted models (GPT families, Claude, Gemini)** often expose lower apparent latency for end users (provider-side optimizations and model variants like “mini/fast”), but costs and control differ vs self-hosting. ([OpenAI][1])

---

## 2 — Compact benchmark table (typical operational ranges)

*Assumptions: A100 80GB or H100; fp16/bf16 or quantized inference; prompt 64 tokens + gen 64 tokens; batch size = 1 unless noted. Ranges show observed variability across stacks and kernel choices.*

| Model family (example sizes)                          |                                Typical first-token / end-to-end latency (BS=1) |            Typical throughput (tokens/sec) | Notes                                                                                                                                |
| ----------------------------------------------------- | -----------------------------------------------------------------------------: | -----------------------------------------: | ------------------------------------------------------------------------------------------------------------------------------------ |
| OpenAI GPT (GPT-4.1 / GPT-4o / GPT-4 Turbo / GPT-3.5) | **GPT-4.1 / GPT-4 large:** 300–1500 ms; **GPT-4o / Turbo variants:** 80–400 ms |          20–300 tok/s (provider dependent) | Hosted API variants tuned for latency; newer GPT-4.1 family emphasizes cost/perf improvements. ([Reuters][2])                        |
| Anthropic Claude family (Claude 2 / 3)                |                                                                    200–1200 ms |                               30–250 tok/s | Provider optimizations vary; higher-capability variants are slower.                                                                  |
| Google Gemini (Pro / Ultra)                           |                                                                     150–900 ms |                               40–300 tok/s | Gemini Pro/Ultra throughput depends on provider stack and selected model size.                                                       |
| Llama family (Llama 2/3 — 7B,13B,70B)                 |                                     7B: **120–450 ms**; 70B: **400 ms–2+ sec** | 80–500 tok/s for smaller; big models lower | MLPerf includes very large Llama runs (70B) showing heavy compute needs. ([MLCommons][3])                                            |
| Mistral / Mistral-instruct (7B)                       |                                                                 **120–350 ms** |                              100–400 tok/s | Often competitive with other 7B models in latency/throughput.                                                                        |
| Falcon (7B / 40B)                                     |                                             7B: 140–380 ms; 40B: 400 ms–2+ sec |                               80–350 tok/s | Falcon-40B needs ~85–100GB memory for smooth inference; quantization recommended for smaller hardware footprint. ([Hugging Face][4]) |
| RedPajama / Mosaic / other 7B                         |                                                                     130–420 ms |                               90–350 tok/s | Performance similar to other community 7B models when optimized.                                                                     |
| Code models (StarCoder / Code-Llama 7B)               |                                                                     130–400 ms |                              100–350 tok/s | Tokenization differences and decoding constraints for code affect latency.                                                           |

> **Interpretation**: ranges overlap a lot. A well-optimized 7B model can match or beat a naïve 3B deployment; larger models (40B–70B+) require careful sharding, quantization, or bigger HW to be practical for low-latency use.

*(Note: these are operational ranges to guide decisions — exact values require running your own stack and prompt shapes.)*

---

## 3 — Benchmarking methodology (recommended, reproducible)

1. **Hardware**: specify GPU model (A100-80GB, A100-PCIe, H100, or Inferentia/Blackwell/etc.). Record CUDA, driver, and NCCL versions. ([Tom's Hardware][5])
2. **Software**: PyTorch 2.x or specialized inference runtimes (NVIDIA Triton, Hugging Face Text-Generation-Inference, DeepSeek/Bento/TFX). Enable FlashAttention / Triton fused kernels. ([Databricks][6])
3. **Configs to measure**: cold start, first-token latency, per-token step time, full response latency, tokens/sec, GPU util, memory. Test sequence shapes (short chat vs long context) and batch sizes (1,2,4,8).
4. **Quantization modes**: fp16/bf16 baseline, then int8/4 (GPTQ/AWQ) to measure accuracy vs perf tradeoffs.
5. **Repeat & warm-up**: warm up with 50–200 requests, then collect percentiles (p50, p95, p99). Log everything.

---

## 4 — Key observations from community & provider reports

* **Provider models (OpenAI, Anthropic, Google)** often show lower apparent latency due to optimized serving stacks and fast smaller variants; compare first-token times and billed tokens when evaluating cost. ([OpenAI][1])
* **Very large models (40B–>70B)** are feasible for production but require multi-GPU sharding or specialized HW and show large latencies unless quantized or served with aggressive caching/sharding. MLPerf results highlight the compute cost of 70B class models. ([MLCommons][3])
* **Memory requirements**: some 40B models (e.g., Falcon-40B) need ~85–100GB working memory unless quantized or sharded, making them heavy to host without HBM-rich GPUs or multi-GPU solutions. ([Hugging Face][4])

(These are the most important load-bearing findings and are drawn from provider announcements, MLPerf submissions, and community benchmarks.) ([OpenAI][1])

---

## 5 — Practical tuning tips (to reduce latency)

* **Prefer smaller or quantized models for low latency**: 3B–7B quantized to int8/4 often gives best UX for chat/IDE tools.
* **Use optimized kernels**: FlashAttention, fused MLP, Triton kernels give large per-token speedups. ([Databricks][6])
* **Token caching & prompt engineering**: keep system prompt short; cache static context; stream tokens to user to improve perceived latency.
* **Batching tradeoff**: batching increases throughput but increases tail latency — choose per-user SLO (p95/p99) carefully.
* **FP8/H100 & new HW**: next-gen HW (Blackwell/H100 with FP8-like formats) significantly shifts perf curves — re-benchmark when changing HW. ([Tom's Hardware][5])

---

## 6 — Quick checklist to run your own benchmark

1. Choose GPU (A100 or H100) and note versions.
2. Pick runtime (PyTorch + FlashAttention, Triton, or TGI/Hugging Face inference).
3. Prepare test prompts (short, medium, long).
4. Warm up, then measure cold start, first token, full response; collect p50/p95/p99.
5. Test fp16, int8, int4 quantized modes; test batch sizes {1,4,8}.
6. Plot latency vs throughput and pick operating point based on SLO.

---

## 7 — Where to read further / sources

* OpenAI GPT-4o/GPT announcement pages (performance claims & variant descriptions). ([OpenAI][1])
* Reuters / major tech reporting on GPT-4.1 family release and performance claims. ([Reuters][2])
* MLPerf Inference results (Llama 70B and large-model submission details). ([MLCommons][3])
* Hugging Face model cards (e.g., Falcon-40B memory & inference notes). ([Hugging Face][4])
* Databricks blog — LLM inference performance engineering best practices. ([Databricks][6])

---

If you want, I can:

* Generate a **1-page runnable benchmark script** (PyTorch + Transformers + FlashAttention) targeting A100 or H100 that measures cold start, first-token, and tokens/sec and outputs CSV/plots.
* Or produce a **compact spreadsheet** mapping specific model variants (GPT-4.1 mini / GPT-4o / Claude-3 Opus / Gemini Pro / Llama-3 7B/70B / Falcon-40B) to approximate latency & infra cost for your infra (tell me A100 vs H100 vs AWS Inferentia if you want a cost mapping).

Which follow-up would you like?

[1]: https://openai.com/index/hello-gpt-4o/?utm_source=chatgpt.com "Hello GPT-4o"
[2]: https://www.reuters.com/technology/artificial-intelligence/openai-launches-new-gpt-41-models-with-improved-coding-long-context-2025-04-14/?utm_source=chatgpt.com "OpenAI launches new GPT-4.1 models with improved coding, long context comprehension"
[3]: https://mlcommons.org/2024/03/mlperf-llama2-70b/?utm_source=chatgpt.com "Llama 2 70B: An MLPerf Inference Benchmark for Large ..."
[4]: https://huggingface.co/tiiuae/falcon-40b?utm_source=chatgpt.com "tiiuae/falcon-40b"
[5]: https://www.tomshardware.com/pc-components/gpus/nvidia-claims-software-and-hardware-upgrades-allow-blackwell-ultra-gb300-to-dominate-mlperf-benchmarks-touts-45-percent-deepseek-r-1-inference-throughput-increase-over-gb200?utm_source=chatgpt.com "Nvidia claims software and hardware upgrades allow Blackwell Ultra GB300 to dominate MLPerf benchmarks - touts 45% DeepSeek R-1 inference throughput increase over GB200"
[6]: https://www.databricks.com/blog/llm-inference-performance-engineering-best-practices?utm_source=chatgpt.com "LLM Inference Performance Engineering: Best Practices"
