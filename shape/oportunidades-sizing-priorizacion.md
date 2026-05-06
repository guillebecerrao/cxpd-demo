---
title: Sizing y Priorización de Oportunidades — Ciclo 01
author: Claude (Shape facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Shape facilitador)
version: 1.0
modification_count: 1
status: completed
cycle: ciclo-01-2026
---

# Sizing y Priorización de Oportunidades — Ciclo 01

> Metodología: Torres, *Continuous Discovery Habits*, Cap. 7 — Sizing y Priorización Jerárquica.
> Fuente de datos: contexto corporativo seeded (sin entrevistas). Ver supuestos en `shape/opportunity-assumptions.md`.

---

## Criterios de scoring

Cada nodo hoja se evalúa en cuatro dimensiones. El esfuerzo actúa como tiebreaker, no como penalizador.

| Dimensión | 1 | 2 | 3 |
|-----------|---|---|---|
| **Alcance** — % de usuarios en el journey que topan con este obstáculo | < 20% | 20–60% | > 60% |
| **Frecuencia** — Con qué regularidad ocurre para un mismo usuario | Rara / una vez | Ocasional | Frecuente / siempre |
| **Alineación OKR** — Impacto directo sobre KR1 (llamadas), KR2 (autoservicio) o KR3 (NPS) | Indirecto | Parcial | Directo en ≥1 KR |
| **Confianza del supuesto** — Certeza de que es un problema real dado el contexto disponible | Baja (hipótesis) | Media (inferido) | Alta (evidencia implícita) |

**Score base = Alcance + Frecuencia + Alineación OKR + Confianza** (máximo: 12)

---

## Scoring por nodo hoja

### Rama A — Encontrar el canal correcto

| Nodo | Alcance | Frecuencia | Alineación OKR | Confianza | Score | Esfuerzo |
|------|---------|-----------|----------------|-----------|-------|---------|
| A1.1 — No encuentra dónde consultar en la app | 2 | 1 | 2 | 2 | **7** | Alto (favorece) |
| A1.2 — No sabe que puede usar lenguaje natural | 3 | 2 | 3 | 2 | **10** | Alto (favorece) |
| A1.3 — Llama sin intentar el canal digital | 3 | 3 | 3 | 2 | **11** | Bajo — cambio de hábito, difícil atacar solo con producto |

**Nota A1.3:** Score alto pero la intervención de producto tiene bajo leverage — cambiar el hábito de llamar requiere comunicación, incentivos y confianza previa. No es el mejor punto de entrada para I&V.

### Rama B — Formular la consulta

| Nodo | Alcance | Frecuencia | Alineación OKR | Confianza | Score | Esfuerzo |
|------|---------|-----------|----------------|-----------|-------|---------|
| B1.1 — Nombre coloquial no reconocido | 3 | 3 | 3 | 3 | **12** | Medio |
| B1.2 — No sabe el nombre del procedimiento | 2 | 2 | 2 | 2 | **8** | Medio |
| B1.3 — Consulta compuesta no manejada | 1 | 1 | 1 | 1 | **4** | Medio |

**Nota B1.1:** Alta confianza porque el contexto estratégico describe explícitamente el problema actual: "el bot solo entiende keywords y responde con formularios PDF." Este nodo es la causa raíz de esa descripción.

### Rama C — Obtener una respuesta confiable

| Nodo | Alcance | Frecuencia | Alineación OKR | Confianza | Score | Esfuerzo |
|------|---------|-----------|----------------|-----------|-------|---------|
| C1.1 — Respuesta ambigua o técnica, no genera acción | 3 | 3 | 3 | 3 | **12** | Medio |
| C1.2 — No sabe si aplica a su plan específico | 2 | 2 | 2 | 2 | **8** | Medio |
| C1.3 — Desconfianza histórica en el sistema | 2 | 2 | 2 | 2 | **8** | Bajo — largo plazo, no atacable en 3 meses |

**Nota C1.1:** Alta confianza porque KR3 (NPS post-consulta) está marcado `at_risk` mientras KR1/KR2 están `on_track`. Eso implica que los usuarios están usando el canal digital pero la experiencia no satisface — señal directa hacia la calidad de la respuesta.

### Rama D — Actuar después de la respuesta

| Nodo | Alcance | Frecuencia | Alineación OKR | Confianza | Score | Esfuerzo |
|------|---------|-----------|----------------|-----------|-------|---------|
| D1.1 — Cubierto, pero no sabe qué hacer después | 3 | 3 | 2 | 2 | **10** | Alto (favorece) |
| D1.2 — No puede guardar ni compartir la respuesta | 2 | 2 | 1 | 2 | **7** | Alto (favorece) |
| D1.3 — "No cubierto" sin opciones claras | 2 | 2 | 2 | 2 | **8** | Medio |

---

## Ranking consolidado

| # | Nodo | Score | Esfuerzo | Nota |
|---|------|-------|---------|------|
| 1 | **B1.1** — Vocabulario coloquial no reconocido | 12 | Medio | Causa raíz explícita en la estrategia |
| 2 | **C1.1** — Respuesta ambigua/técnica, no genera confianza | 12 | Medio | Explica KR3 at_risk |
| 3 | A1.3 — Llama sin intentar digital | 11 | ↓ bajo leverage de producto | Descartado como nodo hoja para I&V |
| 4 | A1.2 — No sabe que puede usar lenguaje natural | 10 | Alto | Válido como oportunidad de onboarding |
| 5 | D1.1 — Cubierto pero sin saber qué hacer | 10 | Alto | Oportunidad de valor post-respuesta |
| 6–9 | B1.2, C1.2, C1.3, D1.3 | 8 | Varios | Segunda línea |
| 10–11 | A1.1, D1.2 | 7 | — | Menor impacto |
| 12 | B1.3 — Consulta compuesta | 4 | — | Edge case |

---

## Análisis del empate B1.1 vs C1.1

B1.1 y C1.1 tienen el mismo score (12). Son el mismo ciclo del problema visto desde ángulos distintos:

- **B1.1** es el problema de **input**: el usuario no puede expresar correctamente lo que necesita. El sistema falla en entender.
- **C1.1** es el problema de **output**: el usuario hizo la consulta, pero la respuesta no le genera suficiente claridad ni confianza para actuar.

**Argumento para B1.1:** Es la causa más upstream. Si el sistema no entiende la consulta, nunca llega a dar una buena respuesta. Atacar B1.1 desbloquea también C1.1.

**Argumento para C1.1:** KR3 (NPS) at_risk mientras KR1/KR2 están on_track es evidencia de que el sistema *está siendo usado* pero *no satisface*. El problema no es solo que no entiende la pregunta — es que incluso cuando responde, la respuesta no es suficientemente clara o confiable. C1.1 ataca directamente el indicador en riesgo.

**Decisión de priorización:** En un ciclo de tres meses con presupuesto acotado, la mejor apuesta es un nodo que tenga el mayor impacto directo sobre el indicador más urgente. KR3 at_risk es la señal más crítica.

---

## Nodo hoja seleccionado

> **C1.1 — El asegurado recibe una respuesta de Coverwise pero no le genera suficiente claridad ni confianza para actuar sin llamar.**
>
> `selected: true`

**Rationale de selección:**
1. **Indicador urgente:** KR3 (NPS post-consulta: 28 → 42) es el único KR `at_risk`. Los KR de volumen están on_track, lo que confirma que hay adopción — el problema es la calidad de la experiencia, no el acceso.
2. **Alcance total:** Afecta a todo usuario que llega a una respuesta, es decir, el universo completo de usuarios activos de Coverwise.
3. **Trazabilidad directa a la visión:** La visión de producto es *"saber si está cubierto sin llamar, sin esperar, sin formularios"*. Una respuesta que no genera confianza actúa como barrera equivalente a esos tres frenos.
4. **Confianza alta:** No es un supuesto puro — KR3 at_risk es evidencia implícita en el contexto estratégico.
5. **Espacio de solución rico:** Comprende respuestas en lenguaje natural, personalización por plan, indicadores de confianza, y tono conversacional — todos dentro del alcance de un ciclo I&V de 3 semanas.

**Relación con B1.1:** B1.1 (vocabulario coloquial) no se descarta — es altamente probable que forme parte de la solución a C1.1 en I&V. Una respuesta confiable presupone entender bien la consulta.

---

## Próximos pasos — Cierre de Shape

- [ ] Marcar `shape/oportunidades-sizing-priorizacion.md` como `status: completed`
- [ ] Marcar `shape/opportunity-assumptions.md` como `status: completed`
- [ ] Actualizar OST con `selected: true` en C1.1 y `on_selected_path: true` en el camino Rama C → C1 → C1.1
- [ ] Registrar bypass del Experience Map como decisión de ciclo
- [ ] Iniciar Ideate & Validate sobre C1.1

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | 2026-05-06 | Claude (Shape facilitador) | Primer ciclo. Scoring de 12 nodos hoja. Empate B1.1/C1.1 resuelto por urgencia del indicador KR3 at_risk. Nodo seleccionado: C1.1. |
