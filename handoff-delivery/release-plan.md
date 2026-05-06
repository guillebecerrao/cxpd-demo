---
title: Release Plan — Coverwise Conversational Response — Ciclo 01/2026
author: Claude (Handoff facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Handoff facilitador)
version: 1.0
modification_count: 1
status: draft
cycle: ciclo-01-2026
---

# Release Plan — Coverwise Conversational Response

> **Engagement:** TW × NexHealth — 3 meses (Jun–Ago 2026)
> **Objetivo del ciclo:** Resolver C1.1 con Coverwise Conversational Response. Mover KR3 (NPS post-consulta: 28 → ≥ 38) y reducir llamadas post-consulta digital ≥ 20%.

---

## Hoja de ruta

| Sprint | Período | Foco | PBIs | Milestone |
|--------|---------|------|------|-----------|
| Sprint 01 | 02 Jun – 13 Jun | Fundación LLM | PBI-01 (core: integración LLM + llamada a API de cobertura + generación de respuesta conversacional) | Response Engine en staging con plan del asegurado |
| Sprint 02 | 16 Jun – 27 Jun | Completar Response Engine + Indicador | PBI-01 (completion) + PBI-02 | Respuesta conversacional con indicador de plan y certeza en staging |
| Sprint 03 | 30 Jun – 11 Jul | UX post-respuesta + Infra de experimento | PBI-03 + PBI-05 | Feature flag activo; A/B test listo para lanzar |
| Sprint 04 | 14 Jul – 25 Jul | Escalación inteligente + Launch A/B | PBI-04 + lanzamiento A/B test | A/B test en producción con 50% de tráfico |
| Sprint 05 | 28 Jul – 08 Ago | A/B test en curso — observación | Monitoreo, fixes de bugs críticos, iteración UX menor | 2 semanas de datos completas |
| Sprint 06 | 11 Ago – 22 Ago | Decisión y cierre | Análisis de resultados, ship o iterate, documentación | Feature en `validated` o plan de iteración |

---

## Estrategia de rollout

### Fase 1 — Staging (Sprint 01–02)
- Validación técnica con el equipo NexHealth
- Pruebas de precisión del LLM con casos reales de cobertura (SA-7: validación de alucinaciones)
- Aprobación de disclaimer legal con el equipo de compliance

### Fase 2 — A/B test en producción (Sprint 03–05)
- Feature flag: 50% tráfico a variante conversacional / 50% respuesta actual (control)
- Segmento inicial: usuarios del plan Digital Plus (segmento de mayor volumen)
- Monitoreo diario: NPS post-consulta, llamadas al call center en 24h, tasa de abandono
- Criterio de stop: si el LLM produce respuestas de cobertura incorrectas (tasa de error > 1%), rollback inmediato

### Fase 3 — Ship o iterate (Sprint 06)
- Si NPS +5 puntos ó reducción de llamadas ≥ 20%: rollout a 100%
- Si mejora parcial: iterar el componente más débil (lenguaje, CTA, o escalación)
- Si sin mejora: sesión de análisis con tríada — revisar SA-5 (preferencia por lenguaje coloquial)

---

## Riesgos del release

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|-------------|---------|------------|
| LLM produce respuestas de cobertura incorrectas (alucinaciones) | Media | Alto — implicación legal | Validación exhaustiva en staging + umbral de confianza bajo el cual se escala a humano (PBI-04) |
| Latencia total > 4s (legacy API ~2s + LLM ~1-2s) | Alta | Medio | Optimización de prompt + respuesta asíncrona con spinner informativo |
| Compliance no aprueba el disclaimer en el plazo | Baja | Alto — bloquea lanzamiento | Iniciar revisión legal en paralelo con Sprint 01, no al final |
| Baja tasa de respuesta en encuesta NPS in-app (< 10%) | Media | Medio — impide medir KR3 | Activar encuesta NPS post-consulta desde Sprint 01 en el control también |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (Handoff facilitador) | Primera versión. 6 sprints planificados. Estrategia de rollout en 3 fases. 4 riesgos identificados. |
