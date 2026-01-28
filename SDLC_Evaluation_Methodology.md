
# SDLC AI Assistant Evaluation – Detailed Methodology

## 1. Data Source
All metrics are derived from actual Kaggle notebook executions per model.
No synthetic or benchmark datasets were used.

## 2. Task Identification
Markdown cells containing task headers were treated as individual SDLC tasks.

## 3. Functional Accuracy
Scored using:
- Successful execution → 1.0
- Partial / non-executing but relevant output → 0.5
- No output → 0.0

## 4. Execution Accuracy
Calculated as the ratio of error-free code executions to total code attempts.

## 5. Coverage
Each task assumed 3 expected SDLC aspects.
Coverage measured how many were addressed in generated outputs.

## 6. Hallucination Detection
Counted fabricated APIs, invalid logic, or unsupported claims.
Heuristically detected via execution failures and content mismatch.

## 7. Consistency
Qualitatively assessed based on response structure and logical flow consistency.

## 8. Final Scoring
Weighted aggregation aligned to enterprise SDLC priorities.


## 9. Task-wise Evaluation Strategy
Each SDLC capability (code generation, code review, bug detection, documentation)
is evaluated independently to avoid masking model weaknesses.

## 10. Equal Weighting Rationale
All SDLC tasks were assigned equal importance to ensure balanced system design
and prevent bias toward generation-heavy workflows.

## 11. Capability-based Model Routing
Final recommendations enable routing tasks to the most suitable model,
improving reliability and reducing hallucination risk in production.

## 12. Governance Considerations
Task-wise scoring supports auditability, safer autonomy levels,
and clearer risk assessment for enterprise deployment.
