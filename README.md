Below is a **brief, production-ready documentation** you can directly use in design docs or architecture reviews for **evaluating Small Language Models (SLMs)**.

---

# Evaluation Criteria for SLMs

*(Accuracy, Speed, Cost, Deployment & Operational Readiness)*

## 1. Purpose

This document defines **standard evaluation criteria** for selecting and benchmarking **Small Language Models (SLMs)** (≈3B–7B parameters) for enterprise use cases such as **code generation, review, documentation, RAG-based assistants, and SDLC automation**.

---

## 2. Core Evaluation Dimensions

### 2.1 Accuracy & Quality

Measures how correctly and reliably the SLM performs the intended task.

**Key Metrics**

* Task accuracy (exact match, pass@k for code)
* Semantic similarity (BLEU, ROUGE, BERTScore for docs)
* Human evaluation score (use-case specific)
* Hallucination rate
* Instruction-following consistency

**Evaluation Methods**

* Benchmark datasets (code, QA, summarization)
* Golden test cases (internal repos, PRs, docs)
* Manual review for high-risk outputs (security, infra code)

**Typical Acceptance Benchmarks**

* ≥85–90% correctness on domain-specific tasks
* Low hallucination rate (<5–8% in critical workflows)

---

### 2.2 Inference Speed & Latency

Measures responsiveness and throughput in real usage.

**Key Metrics**

* Time to First Token (TTFT)
* End-to-end response latency (p50 / p95 / p99)
* Tokens per second (throughput)
* Cold start latency

**Why It Matters**

* IDE assistants require <300 ms TTFT
* Chat/RAG systems tolerate higher latency but need stability
* High latency degrades developer experience

**Target Ranges (Typical)**

* TTFT: <200–300 ms (interactive use)
* Throughput: 100–400 tokens/sec (GPU dependent)

---

### 2.3 Cost Efficiency

Measures total cost of ownership (TCO), not just model size.

**Cost Components**

* Training / fine-tuning cost (LoRA vs full FT)
* Inference cost (GPU hours, memory)
* Storage & monitoring
* Engineering & MLOps overhead

**Key Metrics**

* Cost per 1M tokens (inference)
* GPU cost per concurrent user
* Cost vs accuracy gain ratio

**Evaluation Guideline**

* Prefer **LoRA + RAG** if accuracy gain <10% from full fine-tuning
* Quantized models (int8/int4) often reduce inference cost by 30–60%

---

### 2.4 Deployment & Infrastructure Readiness

Measures how easily the model can be deployed and scaled.

**Key Criteria**

* GPU/CPU memory footprint
* Single-GPU vs multi-GPU requirement
* Compatibility with Kubernetes, Docker
* Support for quantization & sharding
* Startup and autoscaling behavior

**Operational Benchmarks**

* Fits in ≤24–40 GB VRAM for single-node serving
* Horizontal scaling supported
* Supports rolling updates & zero-downtime deploys

---

### 2.5 Scalability & Reliability

Measures production robustness under load.

**Key Metrics**

* Throughput degradation under concurrency
* Error rate at peak load
* Stability during long-context inference
* Recovery time on failure

**Evaluation Tests**

* Load testing (concurrent requests)
* Long-running inference tests
* Chaos testing (node restarts, memory pressure)

---

### 2.6 Customization & Extensibility

Measures how easily the SLM adapts to domain needs.

**Key Factors**

* LoRA / adapter support
* Prompt controllability
* RAG compatibility
* Multi-task or multi-domain tuning
* Tool/function calling support

**Preferred Capabilities**

* Adapter-based fine-tuning
* External tool orchestration
* Prompt + retrieval based specialization

---

### 2.7 Security & Compliance

Measures enterprise readiness.

**Key Criteria**

* On-prem / VPC deployment support
* Data isolation
* No external API dependency (optional)
* Logging & auditability
* Model output filtering & guardrails

**Enterprise Expectations**

* Full data ownership
* Secure access control (RBAC)
* Traceability of prompts and outputs

---

## 3. Evaluation Scorecard (Sample)

| Dimension                 | Weight (%) | Evaluation Notes       |
| ------------------------- | ---------- | ---------------------- |
| Accuracy & Quality        | 30         | Core task correctness  |
| Speed & Latency           | 20         | User experience impact |
| Cost Efficiency           | 15         | Inference + ops cost   |
| Deployment Ease           | 15         | Infra & DevOps fit     |
| Scalability & Reliability | 10         | Production stability   |
| Customization             | 5          | Fine-tuning & RAG      |
| Security & Compliance     | 5          | Enterprise readiness   |
| **Total**                 | **100**    |                        |

---

## 4. Recommended Evaluation Flow

1. **Offline evaluation**

   * Accuracy benchmarks
   * Latency profiling
2. **Pilot deployment**

   * Single-GPU inference
   * Limited user testing
3. **Load & stress testing**

   * Concurrency benchmarks
   * Cost modeling
4. **Production readiness review**

   * Security, monitoring, rollback
5. **Go / No-Go decision**

---

## 5. Key Decision Principles

* **Do not optimize accuracy alone** — latency and cost determine adoption
* **Quantization + RAG often beats larger models**
* **Measure p95/p99 latency, not averages**
* **Prefer models that scale operationally, not just benchmark well**

---

### Summary (One-liner)

> An SLM is production-ready only when it achieves **acceptable accuracy**, **predictable low latency**, **controlled cost**, and **simple, secure deployment** — all at the same time.

---

If you want next, I can:

* Convert this into a **formal evaluation checklist or Excel scorecard**
* Map these criteria to **SLM vs LLM selection**
* Create **acceptance thresholds** specifically for **SDLC / coding assistants**
* Add **sample KPIs for leadership reviews**

Just tell me what you want to build next.
