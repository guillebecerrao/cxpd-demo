---
title: "Sync Log — Presentaciones HTML"
description: "Registro de cambios transversales al patrón de presentaciones para sincronía entre instancias"
status: active
created: 2026-03-28
last_modified: 2026-03-28
last_modified_by: claude
version: 1.0
modification_count: 0
scope: AI-Framework
---

# Sync Log — Presentaciones HTML (AI-Framework)

> **Propósito**: Registrar cambios transversales al patrón de presentaciones HTML que ocurran en esta instancia (AI-Framework). El procedimiento de sincronía lee este log junto con el de Guilles-Universe para propagar cambios entre instancias.
>
> **Quién escribe**: El agente, automáticamente al finalizar una generación de HTML donde se detecte un cambio transversal.
>
> **Qué es un cambio transversal**: Un cambio que afecta la arquitectura base del patrón (convenciones de naming, estructura de config, lógica de History, disposiciones transversales, multi-idioma). No son transversales los cambios específicos de un artefacto (guías visuales del OST, por ejemplo).

---

## Formato de registro

Cada entrada usa este formato:

```markdown
### [YYYY-MM-DD] — Título breve del cambio
- **Tipo**: disposición | convención | arquitectura | fix
- **Descripción**: Qué se cambió y por qué.
- **Archivos afectados**: Lista de archivos modificados en esta instancia.
- **Propagado**: ❌ No | ✅ Sí (YYYY-MM-DD)
```

---

## Registro de cambios

<!-- Agregar entradas nuevas arriba de este comentario, en orden cronológico inverso -->
