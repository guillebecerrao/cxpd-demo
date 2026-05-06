---
title: "Experimento — [NOMBRE]"
author: "[Nombre]"
created: YYYY-MM-DD
last_modified: YYYY-MM-DD
last_modified_by: "[Nombre]"
version: 0.1
modification_count: 0
status: draft
type: experiment
phase: pre-build | post-build
technique: fake-door | concierge | wizard-of-oz | prototype | ab-test | survey | other
epic: "[ID o nombre de la épica]"
owner: "[PM / Designer]"
---

# Experimento — [Nombre]

---

## 1. Hipótesis

> Creemos que [variable independiente / cambio] para [segmento de usuarios] logrará [resultado medible]. Sabremos que es cierto cuando [criterio de éxito específico] en un plazo de [tiempo].

---

## 2. Contexto

### ¿Qué supuesto estamos testeando?

*(El supuesto más riesgoso que queremos validar.)*

### ¿Por qué un experimento y no construir directamente?

*(Justificación: alto costo de build, baja reversibilidad, divergencia interna, incertidumbre alta.)*

### Evidencia previa

*(Qué sabemos hasta ahora. Referencia `conocimiento/lo-que-sabemos.md`.)*

---

## 3. Diseño del experimento

### Técnica

*(Fake Door / Concierge / Wizard of Oz / Prototipo / A/B Test / Encuesta / Otra)*

### Setup

*(Descripción concreta de cómo se ejecuta el experimento. Qué ve el usuario, dónde, cómo.)*

### Audiencia

| Campo | Valor |
|-------|-------|
| Segmento target | *(quiénes)* |
| Tamaño de muestra | *(cuántos usuarios)* |
| Duración estimada | *(cuánto tiempo)* |
| % de tráfico (si aplica) | *(para A/B tests)* |

### Métricas

| Métrica | Cómo se mide | Criterio de éxito |
|---------|-------------|-------------------|
| *(métrica primaria)* | *(instrumento)* | *(umbral)* |
| *(métrica secundaria)* | *(instrumento)* | *(umbral)* |
| *(guardrail metric)* | *(instrumento)* | *(no debe empeorar)* |

---

## 4. Resultados

*(Completar después de ejecutar el experimento.)*

### Datos observados

| Métrica | Resultado | vs. Criterio |
|---------|-----------|-------------|
| *(métrica)* | *(valor)* | ✅ / ❌ |

### Interpretación

*(¿Qué aprendimos? ¿La hipótesis se validó, se invalidó, o fue inconclusa?)*

### Decisión

- [ ] **Avanzar**: La evidencia respalda construir la solución
- [ ] **Pivotar**: Aprendimos algo nuevo que cambia la dirección
- [ ] **Descartar**: La hipótesis fue invalidada
- [ ] **Profundizar**: Necesitamos otro experimento con más detalle

---

## 5. Siguiente paso

*(¿Qué hacemos con este aprendizaje? Actualizar `conocimiento/`, crear spec, diseñar otro experimento.)*

---

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1     | YYYY-MM-DD | [Nombre] | Draft inicial |
