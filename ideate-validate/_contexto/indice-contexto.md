---
description: Archivos que el LLM debe leer al iniciar trabajo en Ideate & Validate
created: 2026-03-24
last_modified: 2026-03-24
---

# Índice de Contexto — Ideate & Validate

Al iniciar una sesión de Ideate & Validate, leer los siguientes archivos **en este orden**:

1. `contexto/estrategia/ost.md` — rama completa de la oportunidad elegida
2. `shape/oportunidades-sizing-priorizacion.md` — nodo hoja elegido y criterio de selección
3. `shape/opportunity-assumptions.md` — supuestos abiertos de la etapa anterior
4. `contexto/estrategia/evidencia-validada.md`
5. `contexto/estrategia/roadmap-discovery-ideate-validate.md`
6. `contexto/design-system/tokens.md`
7. `contexto/design-system/components.md`
8. `contexto/tech-stack/` — ADRs y restricciones tecnológicas disponibles

## No leer por defecto

- `ideate-validate/_historia/` — solo si el usuario lo indica explícitamente
- `contexto/extendido/` — solo cuando una regla de sub-proceso lo requiera
- `legacy/` — solo como referencia histórica si el usuario lo solicita

## Referencias metodológicas

Consultar solo las secciones específicas indicadas, no el libro completo:

- **Ideación y generación de soluciones**:
  Capítulo 10 — *Continuous Discovery Habits*, Teresa Torres
  `contexto/extendido/libros/Continuous Discovery Habits (Teresa Torres).pdf`
