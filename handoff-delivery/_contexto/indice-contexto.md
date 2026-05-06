---
description: Archivos que el LLM debe leer al iniciar trabajo en Handoff to Delivery
created: 2026-03-24
last_modified: 2026-03-24
---

# Índice de Contexto — Handoff to Delivery

Al iniciar una sesión de Handoff to Delivery, leer los siguientes archivos **en este orden**:

1. `ideate-validate/solucion-elegida.md`
2. `contexto/estrategia/roadmap-delivery.md`
3. `contexto/estrategia/epicas.md`
4. `contexto/estrategia/backlog.md`
5. `contexto/design-system/tokens.md`
6. `contexto/design-system/components.md`
7. `contexto/tech-stack/` — ADRs y restricciones tecnológicas disponibles

## No leer por defecto

- `handoff-delivery/_historia/` — solo si el usuario lo indica explícitamente
- `contexto/extendido/` — solo cuando una regla de sub-proceso lo requiera
- `legacy/` — solo como referencia histórica si el usuario lo solicita
