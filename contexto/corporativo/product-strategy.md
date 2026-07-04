---
title: Product Strategy — Coverwise
author: Claude (Cowork)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Cowork)
version: 1.0
modification_count: 1
status: active
---

# Product Strategy — Coverwise

> Describes the strategic direction of the product: vision, objectives, OKRs, and market context.
> Read at the start of any specs, discovery, or strategic planning task.

---

## Product Vision

**Vision:** Any NexHealth policyholder can instantly know whether their procedure is covered — no calling, no waiting, no forms.

---

## Strategic Objectives

| # | Objective | Success Indicator | Horizon |
|---|-----------|-------------------|---------|
| O1 | Reduce call center load for coverage inquiries | Coverage-related calls −30% | Q3 2026 |
| O2 | Improve policyholder experience at critical health moments | Policyholder NPS +10 points | Q4 2026 |
| O3 | Increase retention in the young segment (25–40 years) | Digital segment churn rate −15% | Q4 2026 |

---

## Active OKRs

### Objective: Enable policyholders to resolve coverage questions without human intervention

| Key Result | Baseline | Target | Date | Status |
|-----------|----------|--------|------|--------|
| KR1: % of coverage inquiries resolved via digital self-service | 12% | 45% | Sep 2026 | `on_track` |
| KR2: Reduction in coverage-related calls to the call center | 8,200/month | 5,700/month | Sep 2026 | `on_track` |
| KR3: NPS post coverage inquiry | 28 | 42 | Dec 2026 | `at_risk` |

---

## Market and User Context

**User segment:** Young NexHealth policyholder (25–40 years old), digital plan, mobile-first. Used to handling everything from their phone. Low tolerance for friction: if they don't get an answer in seconds, they call — or simply don't seek care.

**Problem we solve:** The policyholder doesn't know whether their procedure is covered at the moment they need to know — right before going to the doctor, clinic, or ER. The standard answer today is calling the call center (average wait time: 7 minutes) or navigating an app with a chatbot that only understands keywords and responds with PDF forms.

**Competitive context:** Traditional insurers have no natural language solution — their bots are decision trees in disguise. The most advanced insurtechs (Bupa Digital, Vida Cámara) have modern apps but still require manual search by procedure code. Coverwise aims to be the first to answer "is this covered?" in natural language, with no code, no manual.

---

## Strategic Constraints

| Constraint | Detail |
|------------|--------|
| Legacy core system | Coverage data lives in a 15-year-old policy system. Available APIs are REST but with high latency (~2s) and a complex data schema. Coverwise must abstract this complexity. |
| Health regulation | In Chile and Colombia, coverage responses have legal implications. Coverwise must make clear that the answer is informational and does not replace the insurer's formal resolution. |
| Data privacy | Policy data is sensitive. Coverwise cannot store identified query history without the policyholder's explicit consent. |
| Time to market | The team has budget for a 3-month TW engagement. The solution must be deployable before the contract ends. |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (Cowork) | Initial population with NexHealth/Coverwise fictional case context |
