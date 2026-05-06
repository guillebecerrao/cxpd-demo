# Skill: Cierre de Ciclo

## Cuándo usar este skill

Al terminar un ciclo completo de cualquiera de los tres sub-procesos (Shape, Ideate & Validate, Handoff to Delivery). Captura aprendizajes sobre el **proceso** (no el producto), archiva artefactos del ciclo cerrado y prepara el contexto para el siguiente ciclo.

**Activación:** El usuario dice algo como "cerremos el ciclo", "hagamos el cierre", "retroespectiva de [sub-proceso]".

---

## Proceso

### Paso 1 — Identificar el sub-proceso a cerrar

Confirmar con el usuario qué sub-proceso se está cerrando: `shape`, `ideate-validate` o `handoff-delivery`.

### Paso 2 — Proponer entradas de retrospectiva

Basándose en la sesión de trabajo y los artefactos generados, proponer entradas para el documento de retrospectiva correspondiente:
- `shape/_retro/retro-shape.md`
- `ideate-validate/_retro/retro-ideate-validate.md`
- `handoff-delivery/_retro/retro-handoff-delivery.md`

Usar esta estructura para cada entrada:
```markdown
## Ciclo [fecha o identificador]
**Fecha de cierre:** YYYY-MM-DD
**Participantes:** [lista]

### ¿Qué funcionó bien?
### ¿Qué fue difícil o generó fricción?
### ¿Qué cambiaríamos al próximo ciclo?
### Sugerencias de cambios al framework o estructura de carpetas
```

Presentar el borrador al usuario y esperar aprobación antes de escribir.

### Paso 3 — Sugerir archivos a mover a `_historia/`

Identificar los artefactos activos del sub-proceso con `status: completed` y proponer moverlos a `_historia/` con el nombre `[archivo]_YYYY-MM-DD.md`.

**Importante:** Presentar la lista de movimientos propuestos al usuario. **No ejecutar ningún movimiento sin confirmación explícita.**

El usuario puede:
- Aprobar todos los movimientos → el LLM los ejecuta con `git mv`
- Aprobar algunos → el LLM ejecuta solo los aprobados
- Diferir todos → quedan documentadas las sugerencias en la retrospectiva para una reestructuración futura
- Rechazar → no se mueve nada

### Paso 4 — Actualizar la bitácora agéntica

Agregar una entrada en `bitacora/bitacora-agentica.md` con:
- Fecha de cierre
- Sub-proceso cerrado
- Artefactos generados durante el ciclo
- Decisiones clave tomadas
- Estado: `completed`
- Próximos pasos sugeridos (qué sub-proceso sigue o qué falta para el siguiente ciclo)

### Paso 5 — Confirmar al usuario

Resumir lo que quedó registrado y lo que quedó pendiente (movimientos diferidos, sugerencias de reestructuración futura).

---

## Notas importantes

- Este skill captura aprendizajes del **proceso**, no del producto. Los outputs del producto (OST actualizado, solución elegida, specs) se generan dentro del sub-proceso, no aquí.
- Los movimientos a `_historia/` son sugerencias, nunca acciones automáticas.
- Si el usuario no tiene tiempo para el cierre completo, al menos ejecutar el Paso 4 (bitácora agéntica) para preservar el contexto mínimo.
