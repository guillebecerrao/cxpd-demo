---
title: Configuración del Sistema de Presentaciones HTML
author: [Autor]
created: YYYY-MM-DD
last_modified: YYYY-MM-DD
last_modified_by: [Nombre]
version: 1.0
modification_count: 0
status: active
---

# Configuración del Sistema de Presentaciones HTML

> **Archivo de sistema — uso exclusivo del agente.**
> No editar manualmente. Este archivo es leído por el agente al ejecutar el skill `generar-presentacion-html`. Registra guías visuales por artefacto y el registro de documentos permanentes para la auto-referenciación entre HTMLs.
>
> Si querés registrar una preferencia visual o agregar un documento al registro, indicárselo al agente durante una sesión de trabajo.

---

## Documentos permanentes

Lista de HTMLs canónicos del ecosistema. El agente la lee antes de generar cualquier HTML para:
1. Construir el footer "Documentos relacionados" con links relativos (excluyendo el propio documento).
2. Determinar el estado de idiomas del artefacto a generar.

Si el registro está vacío, no se agrega footer.

| Nombre display | Archivo HTML | Descripción breve | Idioma base | Estado idiomas |
|---|---|---|---|---|
| OST — Opportunity Solution Tree | `ost.html` | Full opportunity tree with selected path highlighted. Shape reference document. | en | `single_language` |
| Sizing & Prioritization — Shape Cycle 01 | `sizing-priorizacion_shape-c01-2026.html` | Scoring criteria, node ranking, tie-break analysis, and selected opportunity for Cycle 01. | en | `single_language` |
| Ideas Register — I&V Cycle 01 | `ideas_ideate-validate-c01-2026.html` | All ideas generated for C1.1: 5 active (3 selected, 2 deferred) + 3 discarded in session. | en | `single_language` |
| Chosen Solution — I&V Cycle 01 | `solucion-elegida_ideate-validate-c01-2026.html` | Full solution design: Ideas 1+2+3, conversational flow, A/B experiment, and pre-build assumptions. | en | `single_language` |
| Solution Assumptions — I&V Cycle 01 | `supuestos-solucion_ideate-validate-c01-2026.html` | 10 assumptions in 3 tiers: Resolved (4), Pre-build (3), Post-build (3). Types D/U/V. | en | `single_language` |

**Estados de idiomas posibles:**

| Estado | Significado |
|---|---|
| `single_language` | El HTML se genera solo en el idioma base. Sin switcher ni auto-detección. Default para todos los documentos nuevos. |
| `multi_language_enabled` | El HTML incluye ES, EN y PT embebidos. Auto-detección de browser + switcher manual. |
| `multi_language_paused` | Tenía traducciones activas pero se pausaron temporalmente para iteración ágil. El agente genera en `single_language` y sugiere reactivar al consolidar. |

> **Notas para el agente:**
> - Cuando un documento registrado se regenera con nueva fecha, actualizar el nombre de archivo en esta tabla antes de cerrar la sesión.
> - Documentos no registrados en esta tabla siempre se generan como `single_language`.
> - Al actualizar el estado de idiomas, modificar solo la columna "Estado idiomas" de la fila correspondiente.

---

## Disposiciones transversales

Reglas que aplican a **todos** los HTMLs generados, independientemente del artefacto. Registradas aquí para que el agente las aplique consistentemente.

| # | Disposición | Detalle |
|---|-------------|---------|
| T1 | **Footer de autoría** | Todos los HTMLs deben incluir en el footer una zona central (`footer-meta`) con: autoría original del documento, fecha de última modificación y autor de la última modificación. Estilo sutil: `font-size: xs`, `color: neutral-300`, centrado. Traducir en las tres keys de idioma (`footer.meta`). |
| T2 | **Atribución de IA** | Cuando el HTML fue generado con asistencia de IA, la atribución en el footer debe decir **"Generado con asistencia de Claude"**. No mencionar el nombre específico del modelo. |

---

## Guías visuales por artefacto

Cada vez que el usuario indique cómo quiere ver un artefacto en HTML, registrar la preferencia bajo el encabezado correspondiente. Las guías son acumulativas: no eliminar guías anteriores salvo indicación explícita del usuario.

**Regla:** Antes de generar cualquier HTML, leer esta sección para aplicar las guías vigentes del artefacto. Si no hay guía registrada, generar con criterio propio basado en el design system y preguntar al usuario si quiere registrar preferencias.

---

### OST

*(Sin guías registradas aún. Se agregarán cuando el usuario indique preferencias.)*

---

### Cómo trabajamos

*(Sin guías registradas aún.)*

---

### Roadmap Discovery Shape

*(Sin guías registradas aún.)*

---

### Roadmap Discovery Ideate & Validate

*(Sin guías registradas aún.)*

---

### Roadmap Delivery

*(Sin guías registradas aún.)*

---

### Backlog

*(Sin guías registradas aún.)*

---

### Épicas

*(Sin guías registradas aún.)*

---

### Análisis de Oportunidades

*(Sin guías registradas aún.)*

---

### Sizing y Priorización

*(Sin guías registradas aún.)*

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | YYYY-MM-DD | [Autor] | Creación inicial |
