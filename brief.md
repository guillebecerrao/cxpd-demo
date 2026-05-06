---
title: "E2E-SDPB — Brief"
author: Guillermo Becerra
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Cowork)
version: 0.1
modification_count: 0
status: draft
type: brief
audience: external
---

# E2E-SDPB — End-to-End Spec-Driven Product Building

La comunidad de IA ya resolvió el "cómo construir rápido". Con Claude Code, Cursor o cualquier LLM con acceso a bash, un solo builder produce en horas lo que antes tomaba semanas. Ese problema está resuelto.

El que no está resuelto es el que va antes: **¿qué construyo, por qué eso y no otra cosa, y cómo le paso al agente el contexto suficiente para que construya algo que realmente impacta al usuario en la dirección que le importa al negocio?** Eso sigue siendo informal, ad-hoc e inconsistente en la mayoría de los equipos.

**E2E-SDPB** es un framework que toma todo lo que hace un Product Leader — descubrir oportunidades, priorizar, validar soluciones, especificar con precisión — y lo lleva a un repositorio en git, operado con agentes de IA. El resultado es un sistema operativo del producto que vive donde vive el código: en el repo. Sin Jira, sin Notion, sin Figma obligatorio. Solo git y un vendor de LLM.

El ciclo es simple: *Evidencia → Especificación → Implementación → Validación → Aprendizaje.* Nada se construye sin spec. Ninguna spec se escribe sin evidencia. Todo lo construido se valida. Eso garantiza que el agente siempre tenga el contexto correcto, en el momento correcto, para construir lo correcto.

Funciona en modo tríada (PM + Designer + Engineer con equipo de desarrollo externo) o en modo solo-builder (una persona + agentes especializados). Agnóstico al proveedor de LLM y al de repo.

---

*Creado por Guillermo Becerra.*  
*Para el detalle completo: `framework.md`*
