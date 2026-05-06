---
title: Solution Assumptions — [Nombre de la solución] — Ciclo NN/YYYY
oportunidad: "[ID] — [descripción del nodo hoja elegido]"
author: [autor]
created: [fecha]
last_modified: [fecha]
last_modified_by: [autor]
version: 1.0
modification_count: 0
status: in_progress
---

# Solution Assumptions — [Nombre de la solución]

> **Solución elegida**: [Nombre]
>
> **Propósito**: Registro único de supuestos de la solución. Clasifica cada supuesto por
> estado de evidencia y su relación con los supuestos previos de la fase de elección.
>
> **Metodología**: Teresa Torres, *Continuous Discovery Habits*, Cap. 9 (Identifying Hidden Assumptions).

---

## 1. Supuestos activos

### Resueltos — sin validación dedicada

> Supuestos con evidencia suficiente para avanzar sin validación adicional.

| # | Supuesto | Tipo | Evidencia que lo resuelve |
|---|----------|------|--------------------------|
| SA-1 | [descripción del supuesto] | D / U / V | [EV-ID o WL-ID + descripción] |

---

### Pre-build — validar antes de construir

> Supuestos con evidencia débil cuyo fracaso requeriría cambios de diseño antes de invertir en desarrollo.

| # | Supuesto | Tipo | Evidencia actual | Riesgo si no se valida |
|---|----------|------|-----------------|------------------------|
| **SA-2** | [descripción] | D / U / V | [EV-ID o "sin evidencia"] | [consecuencia concreta si falla] |

> Ver técnicas de validación y criterios de éxito en `ideate-validate/test-plan.md`.

---

### Post-build — validar en producción

> Supuestos que solo son medibles con producto real y tráfico.

| # | Supuesto | Tipo | Evidencia actual | Experimento |
|---|----------|------|-----------------|-------------|
| **SA-3** | [descripción] | D / U / V | [EV-ID o "hipótesis"] | [XP1 / cohorte / etc.] |

> Ver diseño de experimentos en `ideate-validate/test-plan.md`.

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
| 1.0 | [fecha] | [autor] | Versión inicial |
