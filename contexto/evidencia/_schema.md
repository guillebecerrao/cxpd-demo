# Evidence Schema — Contrato de frontmatter

**Versión**: 1.0.0 | **Creado**: [fecha de seed]
**Fuente de verdad para**: todo archivo `EV-NNN.md` en `contexto/evidencia/`

---

## Campos requeridos

| Campo | Tipo | Valores válidos | Notas |
|-------|------|----------------|-------|
| `id` | string | `EV-[code]_[YYYYMMDD]_[short-source]` | Único por construcción — ver reglas de ID más abajo |
| `type` | enum | `interview`, `user-test`, `analytics`, `survey`, `desk-research` | Determina carpeta y código en el ID |
| `method` | string | Libre; ej. `exploratory`, `moderated`, `unmoderated`, `google-analytics`, `fullstory`, `nps`, `kano-model`, `competitive-analysis` | Técnica específica; extensible sin cambios de carpeta |
| `date` | date | `YYYY-MM-DD` | Fecha en que se recolectó la evidencia (no cuando se documentó). Fallback: fecha del git commit del archivo fuente |
| `source` | string | Descripción legible; ej. `"Nombre Participante — entrevista exploratoria Shape ciclo 01"` | Quién o qué generó la evidencia |
| `sub_process` | enum | `shape`, `ideate-validate`, `handoff-delivery` | Sub-proceso en el que se produjo la evidencia |
| `cycle` | string | `ciclo-NN-YYYY` | Ciclo de producto; ej. `ciclo-01-2026` |
| `confidence` | enum | `weak`, `moderate`, `strong` | Fuerza de la señal que la evidencia aporta a las oportunidades que cita |
| `ost_nodes` | list | IDs válidos del OST en `contexto/estrategia/ost.md`; ej. `[B1.1, B2, A1]` | Destino primario de citación |

## Campos opcionales

| Campo | Tipo | Valores válidos | Notas |
|-------|------|----------------|-------|
| `tags` | list | Keywords libres; ej. `[onboarding, registro]` | Filtrado adicional |
| `assets` | list | Paths relativos desde la raíz del repo o URLs externas | Archivos originales, links externos (Figma, Miro, dashboards) |
| `deprecated_node` | list | IDs de nodos OST que ya no existen en el OST activo | Preserva la citación histórica cuando un nodo fue removido o renombrado |

---

## Reglas de ID

```
EV-[type-code]_[YYYYMMDD]_[short-source]
```

### Códigos por tipo

| Tipo | Código | Ejemplo |
|------|--------|---------|
| `interview` | `I` | `EV-I_20260101_nombre-participante` |
| `user-test` | `T` | `EV-T_20260101_moderated-checkout` |
| `analytics` | `A` | `EV-A_20260101_ga4-funnel-q1` |
| `survey` | `S` | `EV-S_20260101_kano-activadores` |
| `desk-research` | `D` | `EV-D_20260101_referentes-feature` |

### Reglas de `[short-source]`

- Minúsculas, separado por guiones
- Máximo 30 caracteres
- Derivado del nombre del participante o título del documento
- Si hay colisión (mismo date + source): el agente DEBE advertir y proponer sufijo antes de crear

---

## Heurística de confidence (guía normativa para agentes)

| Patrón | Asignar |
|--------|---------|
| Participante único, cualitativo | `weak` |
| 2–4 participantes con señales convergentes, o uno con evidencia conductual fuerte | `moderate` |
| 5+ participantes convergentes, o estudio cuantitativo (n≥30) | `strong` |

---

## Estructura de carpetas

```
contexto/evidencia/
├── _inbox/          ← archivos sin clasificar (no referenciar desde otros artefactos)
├── _schema.md       ← este archivo
├── interview/
│   ├── assets/
│   └── YYYY/MM/     ← subdivisión mensual (alta frecuencia)
├── user-test/
│   ├── assets/
│   └── YYYY/QN/     ← subdivisión trimestral
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

**Regla de assets**: Archivos depositados vía `_inbox/` se mueven a `[type]/assets/` tras
la clasificación confirmada. Archivos migrados permanecen en su ubicación original y se
referencian por path relativo.

---

## Estructura de una entrada de evidencia

```markdown
---
id: EV-I_20260101_nombre-participante
type: interview
method: exploratory
date: 2026-01-01
source: "Nombre Participante — entrevista exploratoria Shape ciclo 01"
sub_process: shape
cycle: ciclo-01-2026
confidence: weak
ost_nodes: [B1.1, A1]
tags: [onboarding, new-user]
assets:
  - shape/entrevistas/snapshots/snapshot_nombre-participante_2026-01-01.md
---

# EV-I_20260101_nombre-participante — [Título descriptivo]

[Resumen de 2–5 líneas del hallazgo principal. Qué revela la evidencia
sobre los nodos OST que cita. Sin interpretación — describe lo observado.]

**Cita clave o dato** (opcional):
> "[Cita textual o métrica]"

**Detalle**: [link al asset o snapshot si existe en otro lugar]
```

---

## Changelog

| Versión | Fecha | Autor | Cambio |
|---------|-------|-------|--------|
| 1.0.0 | [fecha de seed] | [autor] | Versión inicial — seed desde AI-Framework |
