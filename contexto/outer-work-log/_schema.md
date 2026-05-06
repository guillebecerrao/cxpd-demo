# Outer Work Log Schema — Contrato de frontmatter

**Versión**: 1.0.0 | **Creado**: [fecha de seed]
**Fuente de verdad para**: todo archivo `WL-NNN.md` en `contexto/outer-work-log/`

---

## Campos requeridos

| Campo | Tipo | Valores válidos | Notas |
|-------|------|----------------|-------|
| `id` | string | `WL-[code]_[YYYYMMDD]_[short-desc]` | Único por construcción — ver reglas de ID más abajo |
| `type` | enum | `session`, `design`, `workshop`, `decision`, `reference` | Determina carpeta y código en el ID |
| `method` | string | Libre; ver métodos iniciales por tipo más abajo | Técnica específica; extensible sin cambios de carpeta |
| `date` | date | `YYYY-MM-DD` | Fecha en que ocurrió el trabajo (no cuando se documentó). Fallback: fecha de modificación del archivo o git commit |
| `source` | string | Descripción legible; ej. `"Sesión de ideación squad — refinamiento feature X"` | Qué evento u origen produjo el artefacto |
| `sub_process` | enum | `shape`, `ideate-validate`, `handoff-delivery`, `build`, `experiment`, `strategic-iteration`, `general` | Sub-proceso al que pertenece; el agente intenta asignar uno específico antes de usar `general` |
| `cycle` | string | `ciclo-NN-YYYY` | Ciclo de producto; ej. `ciclo-01-2026` |
| `participants` | list | Nombres; ej. `[Nombre Persona, Nombre Persona 2]` | Quiénes participaron en el trabajo |
| `summary` | string | 1-2 oraciones, máx ~200 caracteres | Descripción concisa para scan del agente — DEBE permitir context loading sin leer el body |

## Campos opcionales

| Campo | Tipo | Valores válidos | Notas |
|-------|------|----------------|-------|
| `ost_nodes` | list | IDs válidos del OST en `contexto/estrategia/ost.md`; ej. `[B1.1, B2]` | **Recomendado.** Clave primaria para context loading cross-sub-proceso |
| `artifacts_informed` | list | Paths del repo o IDs; ej. `[ideate-validate/solucion-elegida.md]` | Qué artefactos del repo informa este trabajo |
| `tags` | list | Keywords libres | Filtrado adicional |
| `assets` | list | Paths relativos desde la raíz del repo o URLs externas | Archivos originales, links a Figma/Miro/etc. |
| `related` | list | WL-IDs | Cross-referencias temáticas a otras entradas |
| `session_id` | string | `SES-[YYYYMMDD]-[short-desc]` | Agrupa entradas del mismo evento |
| `deprecated_node` | list | IDs de nodos OST que ya no existen en el OST activo | Preserva citación histórica |

## Campos de versionado (convención estándar del repo)

| Campo | Tipo | Notas |
|-------|------|-------|
| `version` | string | Semántico; inicia en `1.0` |
| `modification_count` | integer | Inicia en `1`; se incrementa en cada actualización |
| `last_modified` | date | `YYYY-MM-DD` |
| `last_modified_by` | string | Nombre de persona o `Claude Code` |

---

## Reglas de ID

```
WL-[type-code]_[YYYYMMDD]_[short-desc]
```

### Códigos por tipo

| Tipo | Código | Ejemplo |
|------|--------|---------|
| `session` | `S` | `WL-S_20260101_ideacion-squad` |
| `design` | `D` | `WL-D_20260101_figma-variantes` |
| `workshop` | `W` | `WL-W_20260101_miro-dot-vote` |
| `decision` | `X` | `WL-X_20260101_decision-feature` |
| `reference` | `R` | `WL-R_20260101_pres-stakeholders` |

### Reglas de `[short-desc]`

- Minúsculas, separado por guiones
- Máximo 30 caracteres
- Derivado de la descripción del evento o artefacto
- Si hay colisión (mismo date + desc): el agente DEBE advertir y proponer sufijo antes de crear

---

## Convención de Session ID

```
SES-[YYYYMMDD]-[short-desc]
```

- No es una entidad formal — es un valor de string compartido
- El agente lo propone automáticamente al detectar una entrada existente del mismo evento
- Mismas reglas que `[short-desc]`: minúsculas, guiones, máx 30 caracteres

---

## Métodos iniciales por tipo

| Tipo | Métodos iniciales (extensibles) |
|------|--------------------------------|
| `session` | `ideation`, `refinement`, `planning`, `retrospective`, `sync`, `review`, `kickoff` |
| `design` | `exploration`, `wireframe`, `prototype`, `critique`, `iteration` |
| `workshop` | `brainstorming`, `affinity-mapping`, `dot-vote`, `journey-mapping`, `assumption-mapping` |
| `decision` | `adr`, `trade-off-analysis`, `prioritization`, `go-no-go` |
| `reference` | `presentation`, `report`, `brief`, `benchmark`, `stakeholder-request` |

---

## Estructura de carpetas

```
contexto/outer-work-log/
├── _inbox/          ← archivos sin clasificar (no referenciar desde otros artefactos)
├── _schema.md       ← este archivo
├── session/
│   ├── assets/
│   └── YYYY/MM/     ← creada on demand
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

**Regla de assets**: Archivos depositados vía `_inbox/` se mueven a `[type]/assets/` tras
la clasificación confirmada. Artefactos externos (Figma, Miro, Google Slides) se referencian
por URL en el campo `assets` — no se descargan al repo.

**Carpetas temporales on demand**: Las carpetas `YYYY/MM/` se crean solo cuando se clasifica
la primera entrada para ese período. No se pre-crean.

---

## Estructura de una entrada

```markdown
---
id: WL-S_20260101_ideacion-squad
type: session
method: ideation
date: 2026-01-01
source: "Sesión de ideación squad — exploración alternativas feature X"
sub_process: ideate-validate
cycle: ciclo-01-2026
participants: [Nombre PM, Nombre Designer, Nombre Tech Lead]
summary: "Squad evaluó 3 alternativas para feature X; se priorizó opción Y sobre Z."
ost_nodes: [B1.1]
artifacts_informed:
  - ideate-validate/solucion-elegida.md
tags: [feature-x, ux-alternatives]
assets:
  - contexto/outer-work-log/session/assets/transcript_20260101_ideacion.md
session_id: SES-20260101-squad-ideacion
related: [WL-W_20260101_miro-dot-vote]
version: "1.0"
modification_count: 1
last_modified: 2026-01-01
last_modified_by: [autor]
---

# WL-S_20260101_ideacion-squad — [Título descriptivo]

[Resumen de 3-5 líneas del contenido principal.]

## Contexto

[Breve descripción del contexto que motivó la sesión.]

## Contenido principal

[Extracto relevante o descripción del artefacto.]

## Takeaways

- [Punto clave 1]
- [Punto clave 2]

## Changelog

| Version | Date | Author | Change |
|---------|------|--------|--------|
| 1.0 | 2026-01-01 | [autor] | Entrada inicial |
```

---

## Extensibilidad de tipos

Agregar un nuevo `type` requiere:
1. Un nuevo código de una letra sin colisión con los existentes (S, D, W, X, R) ni con los códigos de evidencia (I, T, A, S, D)
2. Una nueva carpeta a nivel raíz con subcarpeta `assets/`
3. Confirmación explícita del usuario

El prefijo `WL-` previene ambigüedad con el sistema de evidencia (`EV-`).

---

## Mutabilidad de entradas

Las entradas son actualizables después de su creación. Campos como `summary`,
`artifacts_informed`, `related`, `tags` pueden enriquecerse. Cada actualización
DEBE incrementar `modification_count` y agregar una línea al changelog de la entrada.

---

## Changelog

| Versión | Fecha | Autor | Cambio |
|---------|-------|-------|--------|
| 1.0.0 | [fecha de seed] | [autor] | Versión inicial — seed desde AI-Framework |
