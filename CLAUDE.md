# CLAUDE.md — Instrucciones para agentes de Claude

> Este archivo le indica a Claude cómo navegar y usar este repositorio de contexto.
> Léelo SIEMPRE al inicio de una sesión de trabajo.

---

## Qué es este repositorio

Es un repositorio **SDPB-Context** — la capa de contexto del framework **E2E-SDPB** para un squad de producto. Contiene los artefactos de discovery, specs y metodología del ciclo de producto. El código del producto vive en uno o más repos separados. Este directorio es el **template canónico** de un SDPB-Context repo; los productos concretos tienen su propia carpeta en `product-building/`.

---

## Al inicio de cada sesión

1. Leer este archivo (`CLAUDE.md`).
2. Leer `bitacora/bitacora-agentica.md` para recuperar contexto de sesiones anteriores.
3. Si el usuario va a trabajar en un sub-proceso, leer el `_contexto/indice-contexto.md` correspondiente para saber exactamente qué archivos cargar.

---

## Mapa de archivos — Qué leer según la tarea

### Documentos maestros (raíz)

| Archivo | Cuándo leerlo |
|---------|---------------|
| `framework.md` | **Lectura obligatoria** al inicio de cualquier tarea de specs, discovery o estrategia. Define los tres sub-procesos, políticas de gestión y reglas de Claude. |

### Contexto del equipo (`contexto/`)

| Archivo | Cuándo leerlo |
|---------|---------------|
| `contexto/corporativo/estructura-organizacional.md` | Para entender la organización: empresa, área, estructura de equipos, roles |
| `contexto/corporativo/estrategia-producto.md` | Para entender la estrategia del producto: visión, OKRs, objetivos |
| `contexto/squad/squad.md` | Para entender el squad: composición, estado, modelo de trabajo, compromisos |
| `contexto/squad/glosario.md` | Cuando encuentres un término del dominio que no reconozcas, o al generar documentos con vocabulario del dominio |
| `contexto/estrategia/ost.md` | Para entender el Opportunity Solution Tree activo. **Fuente única del OST — nunca copiar.** |
| `contexto/estrategia/evidencia-validada.md` | Para conocer el conocimiento validado del equipo. Leer al iniciar cualquier sub-proceso. |
| `contexto/estrategia/roadmap-discovery-shape.md` | Para planificar actividades de discovery en la fase Shape |
| `contexto/estrategia/roadmap-discovery-ideate-validate.md` | Para planificar actividades de validación en Ideate & Validate |
| `contexto/estrategia/roadmap-delivery.md` | Para planificar entregas al equipo de desarrollo |
| `contexto/estrategia/backlog.md` | Para ver el backlog priorizado |
| `contexto/estrategia/epicas.md` | Para ver las épicas con sus dependencias |
| `contexto/design-system/` | Al generar prototipos, mockups o specs con detalle visual. Leer `tokens.md` y `components.md`. |
| `contexto/tech-stack/` | Al iniciar Ideate & Validate o Handoff to Delivery, para conocer restricciones tecnológicas |
| `contexto/evidencia/` | Para conocer la evidencia de usuario disponible. Leer entradas según `ost_nodes` activos. Leer `_schema.md` antes de crear o clasificar entradas. |
| `contexto/outer-work-log/` | Para conocer el trabajo que el equipo produjo fuera del repo (reuniones, Miro, Figma, decisiones). Leer al iniciar sub-proceso según heurísticas de context loading (regla 33). |

### Contexto extendido (`contexto/extendido/`) — NO leer por defecto

> **Regla crítica:** No leer esta carpeta por defecto. Solo acceder cuando una regla de sub-proceso lo requiera explícitamente o el usuario lo indique. El contenido puede ser extenso y saturará la ventana de contexto innecesariamente.

| Recurso | Cuándo consultarlo |
|---------|-------------------|
| *Continuous Discovery Habits* (Torres) — Cap. 6 | Opportunity Mapping en Shape |
| *Continuous Discovery Habits* (Torres) — Cap. 7 | Sizing y Priorización de Oportunidades en Shape |
| *Continuous Discovery Habits* (Torres) — Cap. 10 | Ideación en Ideate & Validate |
| *Testing Business Ideas* (Bland & Osterwalder) | Técnicas de testing de ideas de negocio |
| `contexto/extendido/investigacion/` | Research histórico del producto (si existe) |

En todos los casos: buscar solo las secciones relevantes, no leer el documento completo.

### Sub-procesos

| Carpeta | Cuándo usarla |
|---------|---------------|
| `shape/` | Sub-proceso 1: descubrimiento y priorización de oportunidades |
| `ideate-validate/` | Sub-proceso 2: ideación, validación y elección de solución |
| `handoff-delivery/` | Sub-proceso 3: specs, backlog y release plan para el equipo de dev |

Al iniciar trabajo en cualquier sub-proceso, **leer primero su `_contexto/indice-contexto.md`**.

**Regla crítica:** No leer `[sub-proceso]/_historia/` por defecto. Solo si el usuario lo indica explícitamente con frases como "revisa el historial" o "compara con la versión anterior".

### Bitácora (`bitacora/`)

| Archivo | Cuándo leerlo |
|---------|---------------|
| `bitacora/bitacora-agentica.md` | Al inicio de cada sesión para recuperar contexto de trabajo previo |
| `bitacora/bitacora-humana.md` | Cuando necesites entender qué ha trabajado el equipo humano recientemente |

### Presentaciones (`presentaciones/`)

HTMLs ejecutivos generados para comunicación con stakeholders. Nunca editar manualmente. Generados con el skill `generar-presentacion-html`.

| Archivo | Propósito |
|---------|-----------|
| `_presentaciones-config.md` | Configuración del sistema: documentos permanentes, guías visuales, disposiciones transversales |
| `_sync-log.md` | Registro de cambios transversales al patrón de presentaciones. Usado por el procedimiento de sincronía para propagar aprendizajes entre esta instancia y Guilles-Universe. El skill lo lee al inicio (chequeo) y escribe al final (registro) de cada generación. |
| `History/` | Versiones anteriores de HTMLs archivados |

### Agentes (`agentes/`)

System prompts especializados. Activar cuando el usuario pida un perfil experto:

| Agente | Archivo | Cuándo usarlo |
|--------|---------|---------------|
| Product Management | `agentes/product-management.md` | Priorización, roadmaps, outcomes, métricas, stakeholder management |
| Spec Driven Development | `agentes/spec-driven-development.md` | Specs detalladas, acceptance criteria, edge cases |
| Ingeniería de Software | `agentes/ingenieria-software.md` | Arquitectura, viabilidad técnica, decisiones de implementación |
| Product Design | `agentes/product-design.md` | UX research, diseño de interacción, prototipos, design systems |

### Skills (`skills/`)

Protocolos de tarea que definen *cómo ejecutar una actividad concreta*. Cargar bajo demanda:

| Skill | Archivo | Cuándo cargarlo |
|-------|---------|----------------|
| Facilitador OST | `skills/ost-facilitator.md` | Crear, actualizar o priorizar el OST |
| Interview Snapshot | `skills/interview-snapshot.md` | Documentar transcripciones de entrevistas en formato snapshot |
| Actualizar Bitácora Humana | `skills/actualizar-bitacora-humana.md` | Consolidar notas personales del equipo en la bitácora humana |
| Cierre de Ciclo | `skills/cierre-de-ciclo.md` | Cerrar un ciclo de sub-proceso: retro, archivar artefactos, actualizar bitácora |
| Generar Presentación HTML | `skills/generar-presentacion-html.md` | Convertir cualquier artefacto estratégico en HTML ejecutivo para stakeholders |

### Contexto privado (`trabajo-individual/`)

Carpetas privadas por miembro del equipo. **Nunca cruzar información entre carpetas de diferentes personas.**

Las notas personales de cada miembro están en su subcarpeta `notas/YYYY-WW_[persona].md`.

### Legacy (`legacy/`) — NO leer por defecto

Documentos obsoletos o reemplazados por documentos vivos. Solo consultar como referencia histórica si el usuario lo solicita explícitamente.

---

## Reglas de comportamiento

### Reglas de navegación y contexto

1. **Leer `bitacora/bitacora-agentica.md` al inicio de cada sesión** para recuperar contexto de trabajo previo.
2. **Leer `_contexto/indice-contexto.md`** al iniciar trabajo en un sub-proceso para saber exactamente qué archivos cargar.
3. **No leer `_historia/` por defecto.** Solo si el usuario lo indica explícitamente.
4. **No leer `legacy/` por defecto.** Solo como referencia histórica si el usuario lo solicita.
5. **No leer `contexto/extendido/` por defecto.** Solo cuando una regla de sub-proceso lo requiera o el usuario lo indique.
6. **Fuente única del OST.** Vive en `contexto/estrategia/ost.md`. Nunca copiar ni duplicar en carpetas de sub-proceso.

### Reglas de Git y branching

7. **Nunca trabajar directamente sobre `main`.** Todo trabajo — sin excepción — debe hacerse en una rama ad-hoc. `main` solo recibe merges.
8. **Al iniciar trabajo en un sub-proceso, verificar en qué rama está el repositorio** (`git branch --show-current`). Si está en `main`, crear o retomar la rama correspondiente antes de tocar cualquier archivo:
   - Shape: `shape/ciclo-NN-YYYY`
   - Ideate & Validate: `ideate-validate/ciclo-NN-YYYY`
   - Handoff to Delivery: `handoff-delivery/ciclo-NN-YYYY`
   - Trabajo puntual sin ciclo: `[tipo]/[descripcion-corta]`
9. **Si se detecta que commits recientes se hicieron sobre `main` por error**, alertar al usuario de inmediato y proponer la corrección: crear rama desde el HEAD actual, resetear `main` al commit previo al error.
10. **Si el producto vive como subcarpeta de un repo padre** (ej: dentro de Guilles-Universe), los scripts de Speckit no detectan `.git` y no pueden crear branches automáticamente. En ese caso, crear branches manualmente a nivel del repo padre antes de iniciar trabajo con Speckit. Patrón: `[nombre-carpeta-producto]/[feature-name]`.

### Reglas de continuidad y versionado

10. **Leer el estado antes de iniciar un sub-proceso.** Evaluar artefactos existentes y anunciar al usuario si hay trabajo en curso (`in_progress`) o si el ciclo anterior está cerrado (`completed`). Siempre ser explícito sobre la decisión que se toma.
11. **Confirmar antes de mover archivos a `_historia/`.** Claude sugiere los movimientos pero no los ejecuta sin confirmación explícita del usuario.

### Reglas de specs y artefactos

12. **Toda spec nueva se crea con `status: draft`.** Nunca en `approved` o `in_dev`.
13. **No modificar specs con `status: approved` o `in_dev`** sin autorización explícita. Si el usuario lo pide, advertir que puede afectar al equipo de desarrollo.
14. **Usar siempre los templates** de `handoff-delivery/specs/_templates/` al crear un nuevo artefacto.
15. **Guardar specs nuevas en `handoff-delivery/specs/activas/`.** Nunca en `cerradas/` directamente.
16. **Toda spec debe trazarse** a una oportunidad del OST o a un JTBD documentado.
17. **Al prototipar**, leer primero `contexto/design-system/tokens.md` y `components.md`.
18. **No mover specs entre carpetas** (activas → cerradas) sin que el usuario lo indique.

### Reglas de presentaciones HTML

19. **Confirmar antes de generar HTML.** Siempre preguntar al usuario antes de generar, incluso si el `.md` acaba de ser editado. El usuario puede tener más cambios pendientes.
20. **Para el OST:** el HTML renderiza el árbol completo con el camino elegido destacado. Nunca eliminar partes del árbol.

### Reglas de bitácora

21. **Actualizar `bitacora/bitacora-agentica.md`** al cierre de un sub-proceso, al cierre de sesión anunciado, o cuando el usuario confirme un checkpoint intermedio.
22. **Sugerir checkpoint** vía chat cuando se acumule trabajo significativo sin cierre anunciado. No actualizar sin confirmación.

### Reglas de privacidad y lenguaje

23. **Privacidad de `trabajo-individual/`.** Nunca cruzar información entre carpetas de personas distintas.
24. **Idioma mixto:** metadata en inglés, contenido en español, anglicismos técnicos tal cual (discovery, delivery, squad, touchpoint, etc.).
25. **Usar el glosario** al generar documentos: `contexto/squad/glosario.md`.
26. **Los inputs durante sesiones no son listas taxativas.** Las listas de ejemplos en las definiciones de sub-proceso son orientadoras, no restrictivas.

### Reglas de evidencia

27. **Inbox detection.** Al inicio de cada sesión, verificar si hay archivos en `contexto/evidencia/_inbox/`. Si los hay, mencionarlo al usuario antes de cualquier otra tarea. No clasificar sin que el usuario lo solicite explícitamente.

28. **Clasificación sin acción.** Al clasificar un archivo del inbox, proponer `type`, `method`, `ost_nodes`, `confidence` y `destination path` de forma explícita y estructurada. No mover, crear ni eliminar ningún archivo hasta recibir confirmación expresa del usuario. El schema de referencia es `contexto/evidencia/_schema.md`.

29. **Creación de entradas.** Al crear un `EV-NNN.md`, verificar primero que el ID propuesto no existe ya en `contexto/evidencia/` (búsqueda por nombre de archivo). Si existe, advertir y proponer alternativa antes de crear nada. Todo archivo creado DEBE tener todos los campos requeridos del schema.

### Reglas de outer-work-log

30. **Inbox detection.** Al inicio de cada sesión, verificar si hay archivos en `contexto/outer-work-log/_inbox/`. Si los hay, mencionarlo al usuario antes de cualquier otra tarea. No clasificar sin que el usuario lo solicite explícitamente.

31. **Clasificación sin acción.** Al clasificar un archivo del inbox, proponer `type`, `method`, `sub_process`, `cycle`, `participants`, `summary`, `ost_nodes` (recomendado), `session_id` (si hay entrada relacionada del mismo evento) y `destination path`. No mover, crear ni eliminar ningún archivo hasta recibir confirmación expresa del usuario. El schema de referencia es `contexto/outer-work-log/_schema.md`.

32. **Creación de entradas.** Al crear un `WL-NNN.md`, verificar primero que el ID propuesto no existe ya en `contexto/outer-work-log/` (búsqueda por nombre de archivo). Si existe, advertir y proponer alternativa. Todo archivo creado DEBE tener todos los campos requeridos del schema.

33. **Context loading.** Al iniciar una sesión de trabajo en un sub-proceso, surfacear entradas relevantes del outer-work-log usando dos heurísticas: (1) por oportunidad — buscar entradas cuyo `ost_nodes` coincida con la oportunidad activa, cross-ciclo y cross-sub-proceso; (2) por recencia — ventana de 30 días filtrada por `sub_process` activo, como fallback. Leer campos `summary` del frontmatter primero; leer body completo solo de las entradas más relevantes. Para `strategic-iteration`, usar ventana más amplia y esperar indicación manual de scope del usuario.

---

## Cómo actualizar documentos

Cuando modifiques un documento de este repositorio:

1. Actualiza el campo `last_modified` en el front-matter YAML
2. Actualiza `last_modified_by` con el nombre de quien hizo el cambio
3. Incrementa `modification_count`
4. Actualiza `version` (minor para ajustes, major para reestructuraciones)
5. Agrega una línea al changelog al final del documento

---

*Este archivo es parte del framework SDD-4-ProductTriad. Actualizar cuando cambie la estructura del repositorio o las reglas de comportamiento del agente.*
