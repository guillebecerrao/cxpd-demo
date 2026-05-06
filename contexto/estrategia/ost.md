---
title: Opportunity Solution Tree — Coverage & Inquiries Squad
author: Claude (Shape facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Shape facilitador)
version: 1.0
modification_count: 1
status: active
---

# Opportunity Solution Tree — Coverage & Inquiries Squad

> Framework visual que conecta el outcome deseado con oportunidades identificadas y soluciones candidatas (Teresa Torres).
> Estrategia alineada a los OKRs y objetivos de producto del equipo.
>
> **Fuente única del OST.** Nunca copiar ni duplicar en carpetas de sub-proceso.

---

## Contexto estratégico

### Business Outcome

> El squad persigue que los asegurados de NexHealth resuelvan sus consultas de cobertura sin intervención humana, reduciendo la carga operativa del call center y mejorando la experiencia digital.

**Métrica norte:** % de consultas de cobertura resueltas vía autoservicio digital

**Baseline actual:** 12%

**Target:** 45% para Sep 2026

---

## Árbol de Oportunidades

> Las oportunidades se organizan en ramas que representan momentos del journey del asegurado en una consulta de cobertura.
> Nivel L2: agrupadores temáticos. Nivel L3: oportunidades concretas accionables (nodos hoja).

---

### Rama A — Encontrar el canal correcto

El asegurado no llega a Coverwise porque no sabe que existe, no lo encuentra, o prefiere el canal que ya conoce (teléfono).

**A1 — Acceso y visibilidad de Coverwise**

- A1.1 — El asegurado no encuentra dónde hacer la consulta dentro de la app
- A1.2 — El asegurado no sabe que puede usar Coverwise para preguntas en lenguaje natural
- A1.3 — El asegurado llama directamente al call center sin intentar la vía digital

---

### Rama B — Formular la consulta

El asegurado llega a Coverwise pero no logra expresar su necesidad de forma que el sistema la entienda.

**B1 — Expresión de la necesidad en lenguaje propio**

- B1.1 — El asegurado usa el nombre coloquial del procedimiento y el sistema no lo reconoce
- B1.2 — El asegurado no sabe el nombre del procedimiento y no sabe cómo describirlo
- B1.3 — El asegurado hace una consulta compuesta ("¿me cubre la consulta y el examen?") y el sistema solo responde a la primera parte

---

### Rama C — Obtener una respuesta confiable `on_selected_path: true`

El asegurado hace la consulta pero la respuesta que recibe no le genera suficiente confianza o claridad para actuar sin llamar.

**C1 — Claridad y confianza en la respuesta** `on_selected_path: true`

- **C1.1 — La respuesta es ambigua o contiene lenguaje técnico que el asegurado no entiende** `selected: true`
- C1.2 — El asegurado no sabe si la respuesta aplica a su plan específico o es genérica
- C1.3 — El asegurado recibe una respuesta pero no confía en ella porque "el sistema se equivoca a veces"

---

### Rama D — Actuar después de la respuesta

El asegurado obtiene la respuesta pero no sabe qué hacer con ella — el journey no termina en la respuesta, sino en la acción.

**D1 — Continuidad del journey post-respuesta**

- D1.1 — El asegurado sabe que está cubierto pero no sabe cómo agendar ni dónde ir
- D1.2 — El asegurado necesita mostrar la cobertura en la clínica pero no puede guardar ni compartir la respuesta
- D1.3 — El asegurado sabe que NO está cubierto pero no sabe qué opciones tiene (bonos, FONASA, etc.)

---

## Soluciones candidatas

> Las soluciones se gestionan en `ideate-validate/`. Registrar aquí solo la solución elegida una vez cerrado el ciclo de Ideate & Validate.

| Oportunidad | Solución elegida | Estado |
|-------------|-----------------|--------|
| C1.1 — Respuesta ambigua/técnica, no genera confianza | Coverwise Conversational Response (Ideas 1+2+3: respuesta LLM en lenguaje natural + indicador de plan/certeza + siguiente paso sugerido) | `in_progress` — Ciclo I&V 01/2026 |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.1 | 2026-05-06 | Claude (Shape facilitador) | Cierre Shape ciclo-01. Nodo seleccionado: C1.1 (respuesta ambigua/técnica). Rama C y C1 marcados on_selected_path. Selección basada en KR3 at_risk como evidencia más urgente. |
| 1.0 | 2026-05-06 | Claude (Shape facilitador) | Primer ciclo Shape. OST construido desde contexto corporativo seeded (sin entrevistas). Business Outcome anclado al OKR norte: % autoservicio 12% → 45% Sep 2026. Cuatro ramas de oportunidad: A (acceso), B (formulación), C (confianza en respuesta), D (acción post-respuesta). Bypassed: Experience Map (declarado en opportunity-assumptions.md). |
