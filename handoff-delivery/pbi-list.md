---
title: PBI List — Coverwise Conversational Response — Ciclo 01/2026
author: Claude (Handoff facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Handoff facilitador)
version: 1.0
modification_count: 1
status: draft
cycle: ciclo-01-2026
---

# PBI List — Coverwise Conversational Response

> **Solución:** Coverwise Conversational Response
> **Oportunidad:** C1.1 — Respuesta ambigua/técnica que no genera confianza para actuar sin llamar
> **Spec de referencia:** `handoff-delivery/specs/activas/prd-coverwise-conversational-response.md`

---

## PBIs del ciclo

| ID | Título | Descripción breve | Sprint | Prioridad | Trazabilidad OST | Status |
|----|--------|-------------------|--------|-----------|-----------------|--------|
| PBI-01 | Conversational Response Engine | Integración LLM que transforma el texto de póliza en respuesta conversacional personalizada al plan del asegurado | Sprint 01–02 | Must | C1.1 | `draft` |
| PBI-02 | Plan & Confidence Indicator | Indicador visual que muestra a qué plan aplica la respuesta y el nivel de certeza del sistema | Sprint 02 | Must | C1.1, C1.2 | `draft` |
| PBI-03 | Suggested Next Step CTA | Acción contextual post-respuesta (agendar, encontrar prestador, guardar confirmación) según el resultado de la consulta | Sprint 03 | Should | C1.1, D1.1 | `draft` |
| PBI-04 | Smart Escalation Fallback | Flujo de escalación inteligente cuando certeza < umbral: ofrece conectar con asesor con el contexto de la consulta preservado | Sprint 04 | Should | C1.1, C1.3 | `draft` |
| PBI-05 | A/B Test Infrastructure | Feature flag + tracking de variante para experimento A/B (respuesta actual vs. conversacional). Integración con PostHog | Sprint 03 | Must | Experimento | `draft` |

---

## Criterios de ready (Definition of Ready)

Un PBI puede entrar al sprint cuando:
- [ ] Spec en `handoff-delivery/specs/activas/` con `status: approved`
- [ ] Acceptance criteria escritos en Gherkin y revisados por la tríada
- [ ] Dependencias técnicas identificadas y desbloqueadas (o con plan de desbloqueo)
- [ ] Diseño aprobado (wireframe o referencia del design system suficiente para el PBI)
- [ ] Supuestos de solución relevantes validados (ver `ideate-validate/solution-assumptions.md`)

---

## Dependencias entre PBIs

```
PBI-01 (Response Engine)
    └──► PBI-02 (Plan & Confidence Indicator)  — PBI-01 debe proveer el campo de plan y confidence score
    └──► PBI-03 (Suggested Next Step)          — PBI-01 determina el resultado (cubierto / no cubierto) que dispara el CTA
    └──► PBI-04 (Smart Escalation)             — PBI-01 provee el confidence score para el umbral de escalación
    └──► PBI-05 (A/B Infrastructure)           — PBI-01 es la variante del experimento; debe poder togglarse vía feature flag
```

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (Handoff facilitador) | Primera versión. 5 PBIs definidos para el ciclo. Dependencias mapeadas. |
