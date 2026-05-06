---
title: Opportunity Assumption Awareness — Ciclo 01
author: Claude (Shape facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Shape facilitador)
version: 1.0
modification_count: 1
status: completed
cycle: ciclo-01-2026
---

# Opportunity Assumption Awareness — Ciclo 01

> Supuestos que sostienen las oportunidades del OST en este ciclo.
> Todo lo que aquí se lista es una hipótesis — no evidencia validada.
> Los supuestos confirmados se mueven a `contexto/estrategia/evidencia-validada.md`.

---

## Bypasses de sub-proceso declarados

| Bypass | Justificación | Riesgo |
|--------|---------------|--------|
| Experience Map omitido | Demo: contexto suficiente para estructurar el OST sin mapear el journey completo | El OST puede estar incompleto en momentos del journey no cubiertos por el contexto seeded. Compensar con entrevistas en próximo ciclo. |
| Sin entrevistas de usuario | Demo: no hay snapshots disponibles en `shape/entrevistas/` | Las oportunidades reflejan el conocimiento del equipo, no la voz del usuario. Alta probabilidad de supuestos no validados en ramas B y D. |

---

## Supuestos por rama del OST

### Rama A — Encontrar el canal correcto

| # | Supuesto | Impacto si es falso | Prioridad de validación |
|---|----------|---------------------|------------------------|
| A-01 | La mayoría de los asegurados que llaman al call center no intentaron primero el canal digital | Alto — si ya intentaron y fallaron, el problema es en B/C, no en A | Alta |
| A-02 | Coverwise no es suficientemente visible en la navegación actual de la app | Medio — si ya es visible, la oportunidad A1.1 desaparece | Media |
| A-03 | El asegurado conoce la existencia de Coverwise pero no confía en él para consultas reales | Alto — cambia el diseño de la solución completamente | Alta |

### Rama B — Formular la consulta

| # | Supuesto | Impacto si es falso | Prioridad de validación |
|---|----------|---------------------|------------------------|
| B-01 | Los asegurados usan nombres coloquiales de procedimientos que el sistema actual no mapea | Alto — si el matching es bueno, B1.1 no es el problema | Alta |
| B-02 | Existen consultas compuestas frecuentes que el sistema actual no maneja | Medio — puede ser edge case, no oportunidad de alto impacto | Media |
| B-03 | El asegurado no tiene claridad del nombre técnico de su procedimiento antes de la consulta | Alto — valida toda la rama B | Alta |

### Rama C — Obtener una respuesta confiable

| # | Supuesto | Impacto si es falso | Prioridad de validación |
|---|----------|---------------------|------------------------|
| C-01 | Los asegurados llaman igual después de usar Coverwise porque la respuesta no les da suficiente confianza | Alto — es el insight clave detrás de KR3 en riesgo | Alta |
| C-02 | El lenguaje técnico en las respuestas actuales es una barrera significativa | Medio — puede ser percepción, no causa real de la llamada | Media |
| C-03 | Los asegurados perciben diferencia entre la respuesta para "mi plan" vs. una respuesta genérica | Alto — si no hay distinción percibida, C1.2 no es oportunidad | Alta |

### Rama D — Actuar después de la respuesta

| # | Supuesto | Impacto si es falso | Prioridad de validación |
|---|----------|---------------------|------------------------|
| D-01 | El journey del asegurado no termina en saber si está cubierto — continúa hacia la acción (agendar, ir a clínica) | Alto — si el asegurado solo quiere saber y no actuar, toda la rama D pierde relevancia | Alta |
| D-02 | Los asegurados necesitan mostrar la confirmación de cobertura en la clínica o guardarla | Medio — puede ser necesidad real o supuesto del equipo | Media |
| D-03 | Cuando la respuesta es "no cubierto", el asegurado queda sin opciones claras en el canal digital | Alto — este es un momento de alta fricción y posible abandono | Alta |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (Shape facilitador) | Primer ciclo. Supuestos mapeados por rama desde el OST inicial. Bypasses documentados (Experience Map + sin entrevistas). |
