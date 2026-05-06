---
title: Design System — [Nombre del Producto]
author: Guillermo Becerra
created: 2026-03-17
last_modified: 2026-03-17
last_modified_by: Guillermo Becerra
version: 1.0
modification_count: 0
status: draft
---

# Design System — [Nombre del Producto]

> Referencia de diseño compartida por la tríada. Contiene los tokens, paleta, tipografía, componentes y lineamientos de marca necesarios para prototipar y especificar interfaces.

---

## Estructura de esta carpeta

```
design-system/
├── README.md              ← Este archivo (índice y convenciones)
├── tokens.md              ← Design tokens: colores, spacing, radii, shadows, breakpoints
├── brand.md               ← Lineamientos de marca: logo, voz, tono, principios visuales
└── components.md          ← Catálogo de componentes reutilizables con uso y variantes
```

---

## Cómo usar esta carpeta

**Para specs y prototipos**: Cuando generes prototipos HTML/React locales o specs con detalle visual, referencia los tokens y componentes de esta carpeta para mantener consistencia con la marca.

**Para Claude**: Al generar cualquier prototipo o mockup, lee primero `tokens.md` para aplicar la paleta, tipografía y spacing correctos. Si el prototipo incluye componentes de UI, consulta `components.md`.

---

## Changelog

| Version | Date       | Author | Description      |
|---------|------------|--------|------------------|
| 1.0     | 2026-03-17 | Guillermo Becerra | Creación inicial |
