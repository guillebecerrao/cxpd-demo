# Skill: Actualizar Bitácora Humana

## Cuándo usar este skill

Cuando cualquier miembro del equipo quiera consolidar sus notas personales en la bitácora humana compartida. Se puede activar en cualquier momento; no requiere estar en ningún sub-proceso específico.

**Activación:** El usuario dice algo como "actualiza la bitácora humana", "consolida las notas" o "sync bitácora".

---

## Proceso

### Paso 1 — Identificar el período a consolidar

1. Leer `bitacora/bitacora-humana.md` y registrar la fecha de la última entrada.
2. Identificar qué archivos de notas personales tienen entradas **posteriores** a esa fecha.

### Paso 2 — Leer notas personales

Leer los archivos de notas de **todas** las personas del equipo con entradas nuevas:
- `trabajo-individual/product-manager/notas/` — Product Manager
- `trabajo-individual/product-designer/notas/` — Product Designer
- `trabajo-individual/product-engineer/notas/` — Product Engineer
- `trabajo-individual/coach/notas/` — Coach / Advisor _(si aplica)_

Leer solo archivos con fecha de modificación posterior a la última actualización de la bitácora.

### Paso 3 — Extraer entradas nuevas

Por cada nota nueva encontrada, extraer:
- **Fecha** de la entrada
- **Persona** que la escribió
- **Tipo**: `reunion` / `decision` / `aprendizaje` / `accion` / `bloqueo`
- **Sub-proceso**: `shape` / `ideate-validate` / `handoff` / `general`
- **Contenido**: resumen conciso (1-3 líneas)

### Paso 4 — Presentar al usuario

Mostrar las entradas a agregar **antes de escribirlas**, para que el usuario pueda corregir o descartar alguna.

### Paso 5 — Actualizar la bitácora

Una vez aprobado, agregar las entradas nuevas a `bitacora/bitacora-humana.md` en orden cronológico y actualizar el campo `last_modified`.

---

## Formato de notas personales (referencia)

Los archivos de notas siguen este formato de nombre: `YYYY-WW_[persona].md`
Ejemplo: `2026-13_product-manager.md`

Estructura sugerida de cada entrada:
```markdown
## [Fecha] — [Contexto breve]
**Tipo:** reunion | decision | aprendizaje | accion | bloqueo
**Sub-proceso:** shape | ideate-validate | handoff | general
**Contenido:** [texto libre]
```
