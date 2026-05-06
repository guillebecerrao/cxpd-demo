# Repositorio de Contexto — SDD-4-ProductTriad

> Repositorio de contexto para tríadas de producto que trabajan con el framework Spec-Driven Development.
> Diseñado para alimentar agentes de IA (Claude) y alinear al equipo humano.

---

## Propósito

Este repositorio centraliza el conocimiento de contexto del squad de producto. Sirve para:

1. Dar contexto estructurado a agentes de Claude para diferentes tareas.
2. Mantener una fuente de verdad compartida entre los miembros de la tríada.
3. Separar contexto público (compartido) de contexto privado (individual).

---

## Estructura de carpetas

```
[raíz]/
├── README.md                          ← Este archivo
├── CLAUDE.md                          ← Instrucciones para Claude sobre cómo usar este repo
├── framework.md                       ← Framework SDD-4-ProductTriad (lectura obligatoria)
│
├── contexto/                          ← Documentos vivos de contexto compartido
│   ├── corporativo/
│   │   ├── estructura-organizacional.md  ← Organización, equipo, roles
│   │   └── estrategia-producto.md        ← Visión, OKRs, objetivos estratégicos
│   ├── squad/
│   │   ├── squad.md                      ← Composición, estado y modelo de trabajo del squad
│   │   └── glosario.md                   ← Vocabulario del dominio
│   ├── estrategia/
│   │   ├── ost.md                        ← Opportunity Solution Tree (fuente única)
│   │   ├── evidencia-validada.md         ← Conocimiento validado del equipo
│   │   ├── backlog.md                    ← Backlog priorizado
│   │   ├── epicas.md                     ← Épicas con dependencias
│   │   ├── roadmap-discovery-shape.md    ← Roadmap de discovery Shape
│   │   ├── roadmap-discovery-ideate-validate.md  ← Roadmap de validación
│   │   └── roadmap-delivery.md           ← Roadmap de delivery
│   ├── design-system/                    ← Tokens, marca, componentes para prototipos
│   │   ├── template-examples/            ← Ejemplos de estructura (rellenar con el DS del producto)
│   │   │   ├── tokens.md
│   │   │   ├── brand.md
│   │   │   └── components.md
│   └── tech-stack/                       ← ADRs y stack tecnológico del producto
│
├── contexto/extendido/                ← Deep-dives bajo demanda (NO leer por defecto)
│   └── libros/                        ← PDFs de libros de referencia metodológica
│
├── shape/                             ← Sub-proceso 1: Discovery y priorización
│   ├── _contexto/indice-contexto.md
│   ├── _historia/                     ← Ciclos anteriores (NO leer por defecto)
│   ├── _retro/retro-shape.md
│   └── entrevistas/
│       ├── snapshots/
│       └── transcripts/
│
├── ideate-validate/                   ← Sub-proceso 2: Ideación y validación
│   ├── _contexto/indice-contexto.md
│   ├── _historia/
│   ├── _retro/retro-ideate-validate.md
│   ├── evidencia/
│   └── prototipos/
│
├── handoff-delivery/                  ← Sub-proceso 3: Specs y entrega a desarrollo
│   ├── _contexto/indice-contexto.md
│   ├── _historia/
│   ├── _retro/retro-handoff-delivery.md
│   ├── specs/
│   │   ├── _templates/               ← Templates de specs (PRD, JTBD, AC, etc.)
│   │   ├── activas/
│   │   └── cerradas/
│   └── sprints/
│
├── agentes/                           ← System prompts especializados para Claude
│   ├── product-management.md
│   ├── spec-driven-development.md
│   ├── ingenieria-software.md
│   └── product-design.md
│
├── skills/                            ← Protocolos de tarea para Claude
│   ├── ost-facilitator.md
│   ├── interview-snapshot.md
│   ├── actualizar-bitacora-humana.md
│   ├── cierre-de-ciclo.md
│   └── generar-presentacion-html.md
│
├── bitacora/
│   ├── bitacora-agentica.md           ← Registro automático del agente
│   └── bitacora-humana.md            ← Registro consolidado del equipo humano
│
├── presentaciones/                    ← HTMLs ejecutivos para stakeholders
│
├── legacy/                            ← Documentos obsoletos (NO leer por defecto)
│
└── trabajo-individual/                ← Carpetas privadas por persona (NO se suben a git)
    └── [persona]/notas/
```

---

## Cómo inicializar este repositorio para un nuevo producto

1. Completar `contexto/corporativo/estructura-organizacional.md` con la organización real.
2. Completar `contexto/corporativo/estrategia-producto.md` con la visión y OKRs del producto.
3. Completar `contexto/squad/squad.md` con el equipo y su modelo de trabajo.
4. Agregar términos del dominio a `contexto/squad/glosario.md`.
5. Poblar `contexto/design-system/` con el design system del producto (usar `template-examples/` como guía).
6. Poblar `contexto/tech-stack/` con el stack tecnológico y los ADRs del equipo.
7. Comenzar el primer ciclo de Shape: leer `shape/_contexto/indice-contexto.md`.

---

## Modelo de colaboración vía Git

**Contexto compartido** (`contexto/`, `agentes/`, `shape/`, `ideate-validate/`, `handoff-delivery/`, etc.): visible para todos, versionado en git.

**Contexto privado** (`trabajo-individual/`): cada persona tiene su subcarpeta local. Esta carpeta completa está en `.gitignore` — nada de su contenido se sube al repositorio remoto.

```bash
git clone <url-del-repo>
# Tu carpeta trabajo-individual/ estará vacía.
# Crea tu subcarpeta y trabaja libremente — no se subirá a git.
```

---

## Convenciones

### Header de documentos

```yaml
---
title: Nombre del documento
author: Nombre del autor original
created: YYYY-MM-DD
last_modified: YYYY-MM-DD
last_modified_by: Nombre
version: X.Y
modification_count: N
status: active | draft | deprecated
---
```

### Changelog

```markdown
## Changelog
| Version | Date       | Author | Description      |
|---------|------------|--------|------------------|
| 1.0     | YYYY-MM-DD | [Autor] | Creación inicial |
```

### Idioma

Mixto: metadata y headers técnicos en inglés, contenido descriptivo en español, anglicismos técnicos del dominio (discovery, delivery, squad, touchpoint, etc.) tal cual.

---

*Este documento es un artefacto vivo. Actualizar con cada cambio estructural del repositorio.*
