# AI Testing Tools (EvaliQA) — TechPulse Support Chat Evaluation

Practical QA portfolio case exploring **AI testing tools** with **EvaliQA**, covering API connector setup, JSON field mapping, mock API responses, and LLM-as-a-judge evaluation against **TechPulse** domain rules.

## Domain Rules Under Test (TechPulse)
- **Support hours:** Monday–Friday, `09:00–18:00 EET`.
- **Delivery:** Courier delivery in `1–3` business days (`$5` fee, free from `$70`; no Sunday delivery).
- **Returns:** Within `14` calendar days in unused original condition with full packaging.
- **Promo code:** `START10` gives `10%` off a first order of at least `$40`.

## Setup & Integration Flow
1. **Mock endpoint (`POST`):** Configured a mock endpoint returning JSON in `{"response": "..."}` format.
2. **EvaliQA output mapping:** Connected the endpoint, verified request/response flow, and mapped `Actual output path` to `response`.
3. **Evaluation run:** Executed test cases through EvaliQA metrics (`llm-gateway`) to evaluate response quality and domain alignment.

## QA Findings & Practical Observations
- **Over-sharing / Relevance drop (`Failed` cases):** Returning all support policies in a single static response includes accurate facts, yet lowers relevance for narrow queries (such as Friday support hours) because unrelated delivery, return, or promo details add extra noise.
- **LLM Gateway Limits & Model Availability (`400` / `429` / `503`):** Running parallel evaluations on free-tier provider quotas can trigger rate-limiting (`429`), temporary provider overload (`503`), or model availability/retirement errors (`400`). Reducing batch size/concurrency, spacing runs, or switching to a supported lightweight model helps avoid quota bottlenecks.

## Files in This Folder
- `mock_response.json` — sample JSON response payload mapped via `response`.
- `dataset_sample.json` — sample test cases for support hours, delivery, returns, and promo rules.
