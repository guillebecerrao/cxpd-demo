---
title: Outer Work Log — Diseño del sistema
author: [autor]
created: [fecha de seed]
last_modified: [fecha de seed]
last_modified_by: [autor]
version: 1.0
modification_count: 1
status: reference
---

# Outer Work Log — Diseño del sistema

> **Documento de referencia** — el contrato técnico activo (campos, tipos, IDs) vive en `_schema.md`.
>
> Este documento describe el diseño del sistema de outer work log del squad.

---

## 1. Problema que resuelve

El equipo genera continuamente artefactos de trabajo fuera del repositorio — transcripts
de reuniones, exports de Miro, capturas de Figma, presentaciones corporativas, registros
de decisiones — pero sin un lugar estructurado donde el agente pueda acceder a ese
contexto. El resultado: al iniciar cada sesión, el agente solo conoce lo que pasó
*dentro* del repo (bitácora) y las señales de usuario (evidencia), pero desconoce lo que
el equipo discutió, evaluó y decidió fuera.

### Las tres capas de contexto

| Capa | Carpeta | Qué captura | Quién lo genera |
|------|---------|-------------|-----------------|
| Evidencia de usuario | `contexto/evidencia/` | Señales del mercado/usuario | Usuarios, datos, investigación |
| **Trabajo externo del equipo** | **`contexto/outer-work-log/`** | Lo que la tríada y el squad producen fuera del repo | La tríada, el squad |
| Sesiones agénticas | `bitacora/` | Lo que pasa dentro del repo con Claude | Claude Code |

---

## 2. Principio de diseño central

> **El artefacto declara su naturaleza. Los documentos del repo declaran sus fuentes.**

Igual que en el sistema de evidencia, la trazabilidad es bidireccional pero distribuida:
- Cada entrada de work-log describe **qué es** y opcionalmente **qué artefactos del repo informa**.
- Los artefactos del repo (specs, test-plans, solución elegida) citan los `WL-IDs` del
  work-log que los justifica.

---

## 3. Estructura de carpetas

```
contexto/outer-work-log/
├── _schema.md                    ← contrato de formato (fuente de verdad activa)
├── _inbox/                       ← zona de aterrizaje para artefactos sin procesar
├── session/
│   ├── assets/
│   └── YYYY/MM/
├── design/
│   ├── assets/
│   └── YYYY/MM/
├── workshop/
│   ├── assets/
│   └── YYYY/MM/
├── decision/
│   ├── assets/
│   └── YYYY/MM/
└── reference/
    ├── assets/
    └── YYYY/MM/
```

Todos los tipos usan `YYYY/MM/` uniforme. Las carpetas temporales se crean on demand.

---

## 4. Procedimiento de ingesta — Work Log Inbox

### Trigger

Cualquier miembro del equipo deposita un archivo en `_inbox/` con nombre descriptivo.

### Protocolo del agente

1. **Detectar** al inicio de sesión — si hay archivos en `_inbox/`, mencionarlo antes de cualquier otra tarea.
2. **Proponer** clasificación completa: `type`, `method`, `sub_process`, `cycle`, `participants`, `summary`, `ost_nodes` (recomendado), `session_id` (si hay entrada relacionada del mismo evento) y path destino — sin crear ni mover nada.
3. **Esperar confirmación** — el usuario ajusta o aprueba.
4. **Ejecutar** tras confirmación: crear `WL-NNN.md`, mover original a `[type]/assets/`, vaciar inbox.

### Múltiples entradas por evento

Una reunión puede producir múltiples artefactos (transcript + Miro export + decisión).
Cada uno se convierte en su propia entrada tipada. Todas las entradas del mismo evento
comparten un `session_id` y se cross-referencian vía `related`.

---

## 5. Context loading — Cómo el agente usa el work-log

Dos heurísticas complementarias:

1. **Por oportunidad**: Match de `ost_nodes` con la oportunidad activa. Funciona cross-ciclo y cross-sub-proceso. Heurística primaria.
2. **Por recencia**: Ventana de 30 días filtrada por `sub_process` activo. Fallback cuando no hay match de oportunidad o como suplemento.

El agente lee los campos `summary` del frontmatter primero (eficiente), luego lee el body
completo solo de las entradas más relevantes.

**Excepción**: para `strategic-iteration`, usar ventana más amplia y esperar indicación manual de scope del usuario.

---

## 6. Relación con artefactos existentes

| Artefacto | Relación |
|-----------|----------|
| `contexto/evidencia/` | Sistemas independientes. Evidencia = señales de usuario/mercado; work-log = trabajo del equipo. Ambos pueden citar los mismos `ost_nodes`. |
| `bitacora/bitacora-agentica.md` | Complementarios. Bitácora = dentro del repo con Claude. Work-log = fuera del repo con el equipo. |
| Sub-procesos (`shape/`, `ideate-validate/`, etc.) | Las entradas del work-log informan artefactos de sub-proceso vía `artifacts_informed`. Los artefactos citan `WL-IDs`. |
| OST (`contexto/estrategia/ost.md`) | Las entradas pueden citar `ost_nodes`. El OST no referencia WL-IDs — referencia `EV-IDs`. |

---

## Changelog

| Versión | Fecha | Autor | Descripción |
|---------|-------|-------|-------------|
| 1.0 | [fecha de seed] | [autor] | Versión inicial — seed desde AI-Framework |
