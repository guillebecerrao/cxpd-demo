---
title: "User Flow — [NOMBRE DEL FLUJO]"
author: "[Nombre]"
created: YYYY-MM-DD
last_modified: YYYY-MM-DD
last_modified_by: "[Nombre]"
version: 0.1
modification_count: 0
status: draft
type: user-flow
epic: "[ID o nombre de la épica]"
owner: "[Designer / PM]"
---

# User Flow — [Nombre del Flujo]

---

## Contexto

- **Persona**: *(referencia persona de `discovery/personas/`)*
- **JTBD asociado**: *(referencia de `discovery/jtbd/`)*
- **PRD relacionado**: *(link al PRD si existe)*
- **Trigger**: *(¿Qué inicia este flujo? ¿Dónde está el usuario cuando empieza?)*

---

## Flujo principal (Happy Path)

```
[Paso 1: Descripción]
        │
        ▼
[Paso 2: Descripción]
        │
        ▼
[Paso 3: Decisión]
       / \
      /   \
   Sí     No
    │       │
    ▼       ▼
[Paso 4a] [Paso 4b]
    │       │
    ▼       ▼
[Paso 5: Resultado final]
```

*(Reemplazar con diagrama Mermaid o descripción paso a paso si es más claro.)*

### Descripción paso a paso

| Paso | Pantalla / Componente | Acción del usuario | Respuesta del sistema |
|------|----------------------|--------------------|-----------------------|
| 1 | *(dónde)* | *(qué hace)* | *(qué pasa)* |
| 2 | *(dónde)* | *(qué hace)* | *(qué pasa)* |

---

## Flujos alternativos

### [Nombre del flujo alternativo 1]

*(Describir la variante y en qué punto diverge del flujo principal.)*

### [Nombre del flujo alternativo 2]

*(Idem.)*

---

## Edge Cases y estados de error

| Escenario | Punto del flujo | Comportamiento |
|-----------|----------------|----------------|
| *(qué puede salir mal)* | *(en qué paso)* | *(qué le mostramos al usuario)* |

---

## Notas de diseño

*(Consideraciones de UX, referencias al design system, componentes a usar, notas para el prototipo.)*

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1     | YYYY-MM-DD | [Nombre] | Draft inicial |
