---
title: "Plan de 5 Días — Engagement E2E-SDPB (abstracto)"
version: 0.1
status: draft
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Cowork)
type: engagement-plan
layer: abstract
note: "Este documento es la capa limpia del framework. No modificar para adaptar al caso. La versión aplicada va en plan-5-dias-[cliente].md"
---

# Plan de 5 Días — De la idea al prototipo en producción
## Engagement E2E-SDPB — Versión abstracta

> Este documento describe el workflow puro del framework, sin caso aplicado. Es la capa de referencia del engagement. Cuando se defina el cliente ficticio, se crea una copia (`plan-5-dias-[cliente].md`) que se adapta al caso. Los cambios de simplificación o atractivo para la demo van solo en la copia; esta versión refleja el framework en su forma canónica.

---

## Precondiciones del engagement

Antes de iniciar el Día 1, el SDPB-Context repo está inicializado con la estructura del AI-Framework. Los archivos de contexto corporativo y squad están en blanco — se populan durante el kickoff del Día 1.

**Modo de operación**: Tríada en modo-repo. Para esta demo, todo (contexto de producto y código) vive en un único repo. En un engagement real, el codebase viviría en repos separados bajo las políticas del cliente; el SDPB-Context repo es siempre independiente.

---

## Día 1 — Kickoff + Shape: De la idea a la oportunidad priorizada

**Objetivo del día**: Pasar del briefing inicial del cliente a una oportunidad de producto elegida con evidencia, documentada en el OST.

### Actividades

1. Kickoff con el cliente: misión del producto, usuarios objetivo, contexto de negocio, restricciones técnicas.
2. Claude (modo PM) popula los archivos de contexto corporativo y squad en tiempo real durante la sesión.
3. Workshop de opportunity mapping: el PM facilita, el equipo genera oportunidades desde la perspectiva del usuario.
4. Construcción colaborativa del OST inicial: Claude actúa como facilitador OST, estructura el árbol de oportunidades en el repo.
5. Sizing y priorización de oportunidades: ejercicio con criterios explícitos (impacto, confianza, esfuerzo).
6. Elección del nodo hoja con justificación documentada.

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `contexto/corporativo/estructura-organizacional.md` | Estructura de la empresa y el área del cliente |
| `contexto/corporativo/estrategia-producto.md` | Visión del producto, OKRs, objetivos de negocio |
| `contexto/squad/squad.md` | Composición del equipo, roles, modelo de trabajo |
| `shape/analisis-oportunidades.md` | Mapa de oportunidades identificadas |
| `shape/oportunidades-sizing-priorizacion.md` | Sizing y priorización con criterio explícito |
| `contexto/estrategia/ost.md` v1 | OST completo con nodo hoja elegido marcado |

### Agentes activos

PM agent · Facilitador OST skill

### Roles de la tríada

| Rol | Actividad principal en el Día 1 |
|-----|-------------------------------|
| **PM** | Lidera el kickoff, facilita el workshop de oportunidades, toma la decisión de priorización |
| **Designer** | Captura pain points UX, identifica patrones de experiencia del usuario durante el workshop |
| **Engineer** | Evalúa viabilidad técnica inicial, popula restricciones de tech-stack |

### Momento WOW

Claude construye el OST completo en tiempo real durante el workshop, lo actualiza iterativamente según las contribuciones del equipo, y produce el documento de sizing y priorización al cierre de la jornada.

### Cierre del día

`shape/oportunidades-sizing-priorizacion.md` con `status: completed`. OST con nodo hoja marcado (`selected: true`).

---

## Día 2 — Ideate: De la oportunidad a las ideas de solución

**Objetivo del día**: Generar un espacio amplio de soluciones posibles para la oportunidad elegida. Mapear supuestos críticos. Diseñar el plan de validación.

### Actividades

1. Claude facilita sesión de ideación estructurada (analogías, "¿cómo podríamos...?", inversión de supuestos).
2. Mapeo de supuestos críticos por idea: supuestos de deseabilidad, viabilidad de negocio y factibilidad técnica.
3. Diseño del Solution Assumption Test Plan: qué validar, con qué método, a qué costo, cuál es el criterio de éxito.

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `ideate-validate/ideas.md` | Registro de ideas con evaluación inicial de impacto y esfuerzo |
| `ideate-validate/solution-assumptions.md` | Supuestos críticos por idea, clasificados por riesgo |
| `ideate-validate/test-plan.md` | Plan de validación: métodos, participantes, criterio de éxito |

### Agentes activos

PM agent · Designer agent

### Roles de la tríada

| Rol | Actividad principal en el Día 2 |
|-----|-------------------------------|
| **PM** | Filtra ideas por impacto de negocio y feasibility estratégica |
| **Designer** | Lidera la ideación UX, propone flujos de usuario por idea, identifica supuestos de desabilidad |
| **Engineer** | Señala supuestos técnicos críticos, estima complejidad relativa por idea |

### Cierre del día

`ideate-validate/test-plan.md` con `status: ready`. Supuestos críticos mapeados y clasificados.

---

## Día 3 — Validate: De los supuestos a la evidencia

**Objetivo del día**: Ejecutar el test plan sobre los supuestos más críticos. Elegir una solución respaldada en evidencia.

### Actividades

1. Ejecución del test plan: entrevistas de usuario, Wizard of Oz, encuesta rápida o smoke test — según el riesgo de los supuestos.
2. Claude documenta los hallazgos en el sistema de evidencia usando el Interview Snapshot skill, los traza al OST.
3. Síntesis de hallazgos: qué supuestos se confirmaron, cuáles se refutaron, qué aprendimos.
4. Decisión documentada: qué solución se elige, por qué, con qué evidencia.

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `ideate-validate/evidencia/EV-001.md` ... | Hallazgos de validación en formato snapshot (uno por sesión/test) |
| `contexto/estrategia/evidencia-validada.md` | Conocimiento validado del squad actualizado |
| `ideate-validate/solucion-elegida.md` | Solución elegida con justificación y trazabilidad a evidencia |
| `contexto/estrategia/ost.md` v2 | OST actualizado con soluciones y assumption tests mapeados |

### Agentes activos

PM agent · Designer agent · Interview Snapshot skill

### Roles de la tríada

| Rol | Actividad principal en el Día 3 |
|-----|-------------------------------|
| **PM** | Conduce o facilita las entrevistas/experimentos |
| **Designer** | Diseña prototipos lo-fi para los tests si aplica; captura hallazgos de UX |
| **Engineer** | Evalúa viabilidad técnica de la solución elegida antes de la decisión final |

### Cierre del día

`ideate-validate/solucion-elegida.md` con `status: completed`. OST v2 con soluciones mapeadas.

---

## Día 4 — Handoff: De la solución a las specs

**Objetivo del día**: Producir especificaciones con el nivel de detalle suficiente para que Claude Code (o un equipo de desarrollo) pueda construir sin ambigüedad.

### Actividades

1. Claude (modo Spec-Driven Development) descompone la solución elegida en features y user stories, trazadas al OST.
2. Para cada feature: acceptance criteria, edge cases, decisiones de UI/UX, restricciones técnicas.
3. Engineer revisa y aprueba las specs desde la perspectiva de implementación. PM valida vs. intención del producto.
4. Claude genera el release plan con dependencias y orden de construcción.

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `handoff-delivery/specs/activas/FEAT-001.md` ... | Specs detalladas por feature (una por feature o user story) |
| `handoff-delivery/release-plan.md` | Plan de entrega con orden de implementación y dependencias |
| `contexto/estrategia/backlog.md` | Backlog priorizado listo para desarrollo |

### Agentes activos

Spec-Driven Development agent · Engineer agent

### Roles de la tríada

| Rol | Actividad principal en el Día 4 |
|-----|-------------------------------|
| **PM** | Valida que cada spec refleje la intención del producto y los OKRs del Día 1 |
| **Designer** | Completa los detalles UX en cada spec: flujos, estados de UI, manejo de errores |
| **Engineer** | Lidera la aprobación técnica, identifica dependencias ocultas, estima esfuerzo de implementación |

### Cierre del día

Todas las specs en `handoff-delivery/specs/activas/` con `status: approved`. Release plan completo.

---

## Día 5 — Build + Deploy: Del repo al producto en producción

**Objetivo del día**: Construir el prototipo funcional guiado por las specs del Día 4 y desplegarlo en producción. Demo al cliente.

### Actividades

1. Claude Code construye el producto guiado por las specs aprobadas del Día 4.
2. Engineer revisa el código generado, cierra el loop de calidad (tests, edge cases).
3. Deploy a Google Cloud (Cloud Run).
4. Apuntar dominio al endpoint del producto.
5. Demo al cliente: walkthrough del SDPB-Context repo + producto vivo en la URL.

### Artefactos producidos

| Entregable | Descripción |
|------------|-------------|
| Producto funcional | Accesible en `https://[cliente].[dominio]` |
| Codebase | Código fuente en rama del repo (modo-demo) o en repo separado (modo-real) |
| `bitacora/bitacora-agentica.md` actualizada | Registro del ciclo completo: Shape → I&V → Handoff → Build |

### Agentes activos

Engineer agent · Claude Code (modo build)

### Roles de la tríada

| Rol | Actividad principal en el Día 5 |
|-----|-------------------------------|
| **Engineer** | Lidera el build, supervisa la salida de Claude Code, gestiona el deploy y el DNS |
| **PM** | Prepara y facilita la demo al cliente |
| **Designer** | Guía el walkthrough del UX con el cliente durante la demo |

### Momento WOW

Claude construye el producto desde las specs en tiempo real (o acelerado en el video), el deploy ocurre en el mismo flujo de trabajo. El cliente ve su idea en producción el Día 5 de haberla planteado.

### Cierre del día

Producto accesible en URL pública. `bitacora/bitacora-agentica.md` con el ciclo completo documentado.

---

## Resumen del engagement

| Día | Sub-proceso E2E-SDPB | Output clave | Agente principal |
|-----|---------------------|--------------|-----------------|
| 1 | Shape | OST con nodo hoja elegido | PM agent + OST Facilitator skill |
| 2 | Ideate & Validate — Ideate | Ideas + Test Plan | PM agent + Designer agent |
| 3 | Ideate & Validate — Validate | Solución elegida con evidencia | PM + Designer agents + Interview Snapshot |
| 4 | Handoff to Delivery | Specs aprobadas + Release Plan | SDD agent + Engineer agent |
| 5 | Build + Deploy | Producto en prod | Claude Code |

---

## Sobre la tríada en un engagement real TW

En esta demo, la tríada opera sobre un único repo simplificado. En un engagement real en contexto de cliente:

- El **SDPB-Context repo** puede vivir bajo la organización GitHub/GitLab del cliente o en un repo neutro compartido con el equipo consultor.
- El **codebase** viviría en repos separados bajo las políticas del cliente (accesos, branching, CI/CD, compliance, revisión de seguridad).
- La tríada operaría sobre los repos del cliente, no en repos propios del equipo consultor.
- El framework es agnóstico al provider de repo y al vendor de LLM.
- En equipos más grandes, el SDPB-Context repo puede tener múltiples squads operando en paralelo sobre ramas distintas.

---

## Nota sobre la velocidad de ejecución

Cinco días de idea a producción es posible porque:

1. **Claude comprime el tiempo de producción de artefactos**: un OST que toma horas construir manualmente se genera en minutos con el facilitador OST. Las specs que toman días escribir se generan en horas.
2. **El framework elimina la ambigüedad**: el agente siempre sabe qué construir porque las specs son el contrato explícito. No hay "¿qué quisiste decir con...?" en el build.
3. **El SDPB-Context repo es el sistema de contexto compartido**: toda la memoria del producto — decisiones, evidencia, supuestos — vive en el repo. No hay pérdida de contexto entre sesiones ni entre miembros del equipo.
