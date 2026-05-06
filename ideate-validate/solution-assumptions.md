---
title: Solution Assumptions — Respuesta Conversacional Coverwise — Ciclo 01/2026
oportunidad: "C1.1 — El asegurado recibe una respuesta de Coverwise pero no le genera suficiente claridad ni confianza para actuar sin llamar"
author: Claude (I&V facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (I&V facilitador)
version: 1.0
modification_count: 1
status: in_progress
cycle: ciclo-01-2026
---

# Solution Assumptions — Respuesta Conversacional Coverwise

> **Solución elegida:** Coverwise Conversational Response — combinación de Ideas 1 + 2 + 3: respuesta en lenguaje natural generada por LLM, personalizada al plan del asegurado, con indicador de certeza y siguiente paso sugerido.
>
> **Metodología:** Torres, *Continuous Discovery Habits*, Cap. 9 (Identifying Hidden Assumptions).

---

## 1. Supuestos activos

### Resueltos — sin validación dedicada

> Supuestos con evidencia suficiente del contexto estratégico disponible para avanzar sin validación adicional.

| # | Supuesto | Tipo | Evidencia que lo resuelve |
|---|----------|------|--------------------------|
| SA-1 | Los asegurados están usando Coverwise para hacer consultas de cobertura | V | KR1/KR2 on_track — hay adopción del canal digital |
| SA-2 | El sistema actual responde con lenguaje técnico de póliza, no conversacional | D | Estrategia producto: "el bot responde con formularios PDF" |
| SA-3 | Los datos de cobertura por plan existen en APIs del sistema legacy | V | Tech context: "APIs REST disponibles con latencia ~2s y schema complejo" |
| SA-4 | Existe diferencia entre planes que justifica personalizar la respuesta | V | Contexto org: NexHealth opera múltiples planes digitales en 3 países |

---

### Pre-build — validar antes de construir

> Supuestos con evidencia débil cuyo fracaso requeriría cambios de diseño antes de invertir en desarrollo.

| # | Supuesto | Tipo | Evidencia actual | Riesgo si no se valida |
|---|----------|------|-----------------|------------------------|
| **SA-5** | Una respuesta en lenguaje coloquial genera más confianza que el texto de la póliza para el asegurado promedio | D | Hipótesis — sin evidencia de usuario | Si el asegurado prefiere el texto técnico como "fuente oficial", la solución no genera confianza y puede empeorar la percepción |
| **SA-6** | El asegurado comprende y actúa sobre el "siguiente paso sugerido" post-respuesta | U | Hipótesis — no hay datos de uso de CTAs post-respuesta | Si el CTA es ignorado, el diseño del flujo post-respuesta necesita rediseño antes del build |
| **SA-7** | El LLM puede generar respuestas de cobertura suficientemente precisas sin alucinaciones sobre las condiciones del plan | V | Sin evidencia — requiere evaluación técnica | Si el LLM produce errores de cobertura, hay implicaciones legales (ley chilena: respuesta es informativa pero no puede inducir a error) |

> Ver técnicas de validación en `ideate-validate/test-plan.md`.

---

### Post-build — validar en producción

> Supuestos que solo son medibles con producto real y tráfico.

| # | Supuesto | Tipo | Evidencia actual | Experimento |
|---|----------|------|-----------------|-------------|
| **SA-8** | Asegurados que reciben respuesta conversacional no llaman al call center después | V | KR3 at_risk sugiere que hoy sí llaman | A/B test: respuesta actual (control) vs. respuesta conversacional (variante). Métrica: % de usuarios que llaman en las 24h siguientes a la consulta |
| **SA-9** | El NPS post-consulta mejora con respuesta conversacional + certeza + siguiente paso | V | KR3: 28 → 42 es el target | Medición de NPS post-consulta separado por variante en el A/B test |
| **SA-10** | La latencia adicional del LLM (~1-2s sobre la API legacy) no afecta negativamente la experiencia | U | Hipótesis técnica — latencia legacy ya ~2s | Monitoreo de abandono de sesión según tiempo de respuesta total |

---

## Leyenda de tipos de supuesto

| Tipo | Descripción |
|------|-------------|
| **D** | Deseable — ¿Los usuarios quieren esto? |
| **U** | Usable — ¿Pueden usarlo sin fricción? |
| **V** | Viable — ¿Genera el resultado de negocio esperado? |

---

## Changelog

| Versión | Fecha | Autor | Descripción |
|---------|-------|-------|-------------|
| 1.0 | 2026-05-06 | Claude (I&V facilitador) | Primera versión. 4 supuestos resueltos, 3 pre-build, 3 post-build. Solución: Ideas 1+2+3 combinadas. |
