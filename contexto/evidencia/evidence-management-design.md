---
title: Evidence Management — Diseño del sistema
author: [autor]
created: [fecha de seed]
last_modified: [fecha de seed]
last_modified_by: [autor]
version: 1.0
modification_count: 1
status: reference
---

# Evidence Management — Diseño del sistema

> **Documento de referencia** — el contrato técnico activo (campos, tipos, IDs) vive en `_schema.md`.
>
> Este documento describe el diseño del sistema de gestión de evidencia del squad.

---

## 1. Problema que resuelve

La evidencia se genera continuamente y en paralelo durante el ciclo de producto —
entrevistas, user tests, datos cuantitativos, desk research — pero sin un lugar
que la organice con trazabilidad hacia los artefactos que le dan sentido (oportunidad
→ idea de solución → supuesto → feature). El proceso no es lineal: una feature puede
estar en desarrollo mientras se sigue generando evidencia que la retroalimenta. Además,
la evidencia llega en múltiples formatos y herramientas, lo que dificulta su ingesta
consistente.

---

## 2. Principio de diseño central

> **La evidencia declara su naturaleza. Los artefactos declaran sus fuentes.**

La trazabilidad es bidireccional pero distribuida:
- Cada archivo de evidencia describe **qué es** y **qué nodos del OST informa** — no a qué artefactos futuros llegará.
- Los artefactos (specs, test-plans, features) citan los `EV-IDs` de la evidencia que los justifica.

Esto resuelve el problema de que la evidencia creada hoy no puede apuntar a artefactos
que aún no existen.

---

## 3. Estructura de carpetas

```
contexto/evidencia/
├── _schema.md                    ← contrato de formato (fuente de verdad activa)
├── _inbox/                       ← zona de aterrizaje para evidencia sin procesar
├── interview/
│   ├── assets/
│   └── YYYY/MM/                  ← subdivisión mensual
├── user-test/
│   ├── assets/
│   └── YYYY/QN/                  ← subdivisión trimestral
├── analytics/
│   ├── assets/
│   └── YYYY/QN/
├── survey/
│   ├── assets/
│   └── YYYY/QN/
└── desk-research/
    ├── assets/
    └── YYYY/QN/
```

### Granularidad temporal

| Tipo | Subdivisión | Razón |
|------|-------------|-------|
| `interview/` | `/año/mes` | Alta frecuencia (~5/semana) — mes evita carpetas con 100+ archivos |
| `user-test/` | `/año/Q` | Frecuencia media — alineado con cadencia de OKRs |
| `analytics/` | `/año/Q` | Frecuencia baja-media — alineado con OKRs |
| `survey/` | `/año/Q` | Frecuencia baja-media — alineado con OKRs |
| `desk-research/` | `/año/Q` | Frecuencia baja — alineado con OKRs |

**Regla de quarters:**

| Quarter | Meses |
|---------|-------|
| Q1 | Enero – Marzo |
| Q2 | Abril – Junio |
| Q3 | Julio – Septiembre |
| Q4 | Octubre – Diciembre |

---

## 4. Convención de IDs

Los IDs son únicos por construcción — basados en tipo, fecha y fuente — sin coordinación
entre miembros del equipo.

| Tipo | Código | Ejemplo |
|------|--------|---------|
| `interview` | `I` | `EV-I_20260101_nombre-participante` |
| `user-test` | `T` | `EV-T_20260101_moderated-checkout` |
| `analytics` | `A` | `EV-A_20260101_ga4-funnel-q1` |
| `survey` | `S` | `EV-S_20260101_kano-activadores` |
| `desk-research` | `D` | `EV-D_20260101_referentes-feature` |

Formato: `EV-[código]_[YYYYMMDD]_[fuente-corta]`

`[fuente-corta]`: minúsculas, separado por guiones, máximo 30 caracteres.

---

## 5. Procedimiento de ingesta — Evidence Inbox

### Trigger

Cualquier miembro del equipo deposita un archivo en `_inbox/` con nombre descriptivo.

### Protocolo del agente

1. **Detectar** al inicio de sesión — si hay archivos en `_inbox/`, mencionarlo antes de cualquier otra tarea.
2. **Proponer** clasificación completa: `type`, `method`, `ost_nodes`, `confidence`, path destino — sin crear ni mover nada.
3. **Esperar confirmación** — el usuario ajusta o aprueba.
4. **Ejecutar** tras confirmación: crear `EV-NNN.md`, mover original a `[type]/assets/`, vaciar inbox.

**Regla crítica:** el agente nunca clasifica ni mueve sin confirmación explícita.

### Distinción inbox vs migración

| Escenario | Archivo original |
|-----------|-----------------|
| Archivo depositado vía inbox | Se mueve a `[type]/assets/` tras clasificación |
| Migración de evidencia pre-existente | Permanece en su ubicación; se referencia por path relativo en `assets:` |

---

## 6. Relación con artefactos existentes

| Artefacto | Relación |
|-----------|----------|
| `contexto/estrategia/evidencia-validada.md` | Sin cambios — sigue siendo la síntesis de insights validados. Capa de conclusiones sobre la capa de fuentes. |
| OST (`ost.md`) | Los artefactos que citen evidencia deben referenciar `EV-IDs`. El OST mismo puede citarlos para trazabilidad explícita. |
| Specs, test-plans | Deben citar los `EV-IDs` que justifican cada decisión. |

---

## 7. Comportamiento ante trabajo paralelo

Dos miembros del equipo pueden subir evidencia simultáneamente sin riesgo de conflicto
en git: cada pieza genera un archivo nuevo con ID único por construcción (fecha + fuente).
No se edita ningún archivo compartido durante la ingesta.

---

## Changelog

| Versión | Fecha | Autor | Descripción |
|---------|-------|-------|-------------|
| 1.0 | [fecha de seed] | [autor] | Versión inicial — seed desde AI-Framework |
