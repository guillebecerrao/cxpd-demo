---
title: "PRD — [NOMBRE DEL FEATURE/EPIC]"
author: "[Nombre]"
created: YYYY-MM-DD
last_modified: YYYY-MM-DD
last_modified_by: "[Nombre]"
version: 0.1
modification_count: 0
status: draft
type: prd
epic: "[ID o nombre de la épica]"
owner: "[PM]"
sprint_target: "[sprint-XX]"
---

# PRD — [Nombre del Feature / Epic]

---

## 1. Resumen ejecutivo

*(2-3 párrafos: qué se va a construir, para quién, por qué, y qué resultado se espera.)*

---

## 2. Contexto y problema

### Problem Statement

*(Referencia al Product Brief si existe.)*

### Background

*(¿Qué ha pasado antes? ¿Qué se ha intentado? ¿Qué aprendimos?)*

### Evidencia de soporte

*(Datos, research, resultados de experimentos. Referencia archivos de `discovery/` y `conocimiento/`.)*

---

## 3. Objetivos y métricas

### Outcome esperado

| Métrica | Baseline actual | Target | Plazo |
|---------|----------------|--------|-------|
| *(métrica 1)* | *(valor actual)* | *(valor deseado)* | *(cuándo)* |

### Non-goals

*(Qué explícitamente NO es objetivo de este PRD.)*

---

## 4. User Stories

### Personas involucradas

*(Referencia personas de `discovery/personas/`.)*

### Stories

| ID | Como... | Quiero... | Para... | Prioridad |
|----|---------|-----------|---------|-----------|
| US-01 | *(persona)* | *(acción)* | *(beneficio)* | Must / Should / Could |

---

## 5. Diseño funcional

### User Flows

*(Referencia user flows de `specs/activas/` o describe aquí. Incluir link a prototipos si existen.)*

### Use Cases

*(Referencia use cases detallados si existen como archivos separados.)*

### Edge Cases y estados especiales

| Escenario | Comportamiento esperado |
|-----------|------------------------|
| Empty state | *(qué ve el usuario cuando no hay datos)* |
| Error state | *(qué pasa si algo falla)* |
| Loading state | *(qué ve el usuario mientras carga)* |
| Permisos insuficientes | *(qué pasa si el usuario no tiene acceso)* |

---

## 6. Requerimientos técnicos

### APIs y servicios involucrados

*(Endpoints, contratos, dependencias técnicas.)*

### Datos requeridos

*(Qué datos se necesitan, de dónde vienen, formato.)*

### Consideraciones de performance

*(SLAs, tiempos de respuesta esperados, volumen.)*

### Feature flags

*(¿Se necesita feature flag para rollout gradual?)*

---

## 7. Diseño visual

### Referencia de Design System

*(Componentes de `contexto/design-system/` que se usan. Link a prototipos si existen.)*

### Prototipos

*(Links a Figma, prototipos HTML/React locales, o screenshots.)*

---

## 8. Acceptance Criteria

*(Incluir aquí o referenciar archivo separado de `specs/activas/`.)*

### Feature: [Nombre]

```gherkin
Scenario: [Nombre del escenario]
  Given [precondición]
  When [acción del usuario]
  Then [resultado esperado]
```

---

## 9. Plan de rollout

| Fase | Alcance | Criterio de avance |
|------|---------|-------------------|
| 1. Experiment / Validation | *(alcance limitado)* | *(qué debe pasar para avanzar)* |
| 2. Soft launch | *(% de usuarios)* | *(métricas a monitorear)* |
| 3. Full rollout | 100% | *(criterio de éxito)* |

---

## 10. Dependencias y riesgos

| Dependencia / Riesgo | Owner | Status | Mitigación |
|----------------------|-------|--------|------------|
| *(item)* | *(quién)* | *(estado)* | *(plan B)* |

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1     | YYYY-MM-DD | [Nombre] | Draft inicial |
