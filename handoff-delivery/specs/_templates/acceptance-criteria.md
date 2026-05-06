---
title: "Acceptance Criteria — [NOMBRE DEL FEATURE]"
author: "[Nombre]"
created: YYYY-MM-DD
last_modified: YYYY-MM-DD
last_modified_by: "[Nombre]"
version: 0.1
modification_count: 0
status: draft
type: acceptance-criteria
epic: "[ID o nombre de la épica]"
prd: "[Referencia al PRD]"
owner: "[PM / Engineer]"
---

# Acceptance Criteria — [Nombre del Feature]

---

## Feature: [Nombre]

### Scenario 1: [Nombre del escenario — Happy Path]

```gherkin
Given [precondición / estado inicial]
  And [otra precondición si aplica]
When [acción del usuario]
  And [otra acción si aplica]
Then [resultado esperado]
  And [otro resultado si aplica]
```

### Scenario 2: [Nombre — Flujo alternativo]

```gherkin
Given [precondición]
When [acción diferente]
Then [resultado diferente]
```

### Scenario 3: [Nombre — Edge case / Error]

```gherkin
Given [precondición que genera el edge case]
When [acción del usuario]
Then [sistema muestra error o maneja el caso]
  And [estado del sistema después del error]
```

---

## Criterios no funcionales

| Criterio | Especificación |
|----------|---------------|
| Performance | *(tiempo de respuesta máximo, e.g., < 200ms)* |
| Accesibilidad | *(nivel WCAG, e.g., AA)* |
| Responsive | *(breakpoints que debe soportar)* |
| Browser support | *(navegadores y versiones)* |

---

## Checklist de Definition of Done

- [ ] Todos los scenarios pasan en testing
- [ ] Edge cases cubiertos
- [ ] Responsive verificado en breakpoints definidos
- [ ] Accesibilidad verificada
- [ ] Feature flag configurado (si aplica)
- [ ] Métricas / tracking implementado
- [ ] Documentación actualizada

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1     | YYYY-MM-DD | [Nombre] | Draft inicial |
