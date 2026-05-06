---
title: "Plan de 5 Días — Caso NexHealth / Coverwise"
version: 0.1
status: draft
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (Cowork)
type: engagement-plan
layer: applied
source: plan-5-dias.md
client: NexHealth
product: Coverwise
url: coverwise.becerra-ojeda.cl
---

# Plan de 5 Días — De la idea al prototipo en producción
## Caso aplicado: NexHealth · Coverwise

> Versión aplicada del plan abstracto (`plan-5-dias.md`). Toda la narrativa del workflow es idéntica al framework canónico. Lo que cambia aquí son los nombres, el contexto del cliente, y los ejemplos de artefactos. No modificar `plan-5-dias.md`.

---

## El caso

**Cliente**: NexHealth — aseguradora digital de salud, operación LATAM. 500K asegurados activos, crecimiento acelerado en segmento joven.

**El problema**: Los asegurados no saben si su prestación está cubierta en el momento en que la necesitan. La respuesta estándar es llamar al call center (costo operacional alto, NPS bajo) o simplemente no atenderse (pérdida de acceso, riesgo de salud). El chatbot actual no entiende preguntas en lenguaje natural y responde con formularios.

**El usuario objetivo**: Asegurado joven (25-40 años), plan digital, mobile-first, que pregunta "¿me cubre esto?" antes de ir al médico o a la clínica.

**El producto**: Coverwise — asistente conversacional que responde preguntas de cobertura en lenguaje natural, en tiempo real, desde el móvil.

**URL en producción**: `coverwise.becerra-ojeda.cl`

---

## Precondiciones del engagement

El `SDPB-Context repo` está inicializado con la estructura del AI-Framework. Los archivos de contexto corporativo y squad están en blanco — se populan durante el kickoff del Día 1.

**Modo de operación**: `single-repo mode` (demo). Todo el contexto del producto y el código viven en un único repo. En un engagement real, el codebase viviría en repos separados bajo las políticas del cliente.

---

## Día 1 — Kickoff + Shape: De la idea a la oportunidad priorizada

**Objetivo del día**: Pasar del briefing de NexHealth a una oportunidad de producto elegida con evidencia, documentada en el `OST`.

### Actividades

1. **Kickoff con NexHealth**: misión del producto, usuarios objetivo, contexto del negocio (crecimiento, NPS, carga del call center), restricciones técnicas (stack legacy de cobertura, APIs disponibles).
2. **Claude (modo `PM agent`)** popula los archivos de contexto corporativo y squad en tiempo real durante la sesión.
3. **Workshop de opportunity mapping**: el PM facilita, el equipo genera oportunidades desde la perspectiva del asegurado — "¿en qué momentos un asegurado falla en entender su cobertura?".
4. **Construcción colaborativa del `OST`**: Claude actúa como `OST Facilitator skill`, estructura el árbol de oportunidades en el repo en tiempo real.
5. **Sizing y priorización de oportunidades**: ejercicio con criterios explícitos (`impact`, `confidence`, `effort`).
6. **Elección del `leaf node`**: oportunidad seleccionada con justificación documentada.

### Oportunidades identificadas en el workshop (ejemplo)

| Oportunidad | Nivel en el OST |
|------------|----------------|
| El asegurado no sabe si su prestación está cubierta antes de ir al médico | `leaf node` — **elegida** |
| El asegurado no encuentra su póliza cuando la necesita | `leaf node` |
| El asegurado no confía en la respuesta del bot actual | `opportunity node` |
| El call center tarda demasiado en responder | `opportunity node` |
| El asegurado no entiende los topes y exclusiones de su plan | `leaf node` |

**`leaf node` elegido**: "El asegurado no sabe si su prestación está cubierta en el momento en que la necesita" — mayor `impact` en NPS y en costo operacional, evidencia disponible de call center.

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `contexto/corporativo/estructura-organizacional.md` | NexHealth: área de producto digital, estructura de equipos, stakeholders |
| `contexto/corporativo/estrategia-producto.md` | Visión de Coverwise, OKRs: reducir llamadas por cobertura en 30%, NPS +10 puntos |
| `contexto/squad/squad.md` | Composición del squad, roles, modelo de trabajo TW |
| `shape/analisis-oportunidades.md` | Mapa de oportunidades del asegurado NexHealth |
| `shape/oportunidades-sizing-priorizacion.md` | Sizing con criterios `impact`, `confidence`, `effort` |
| `contexto/estrategia/ost.md` v1 | `OST` completo — `leaf node` elegido con `selected: true` |

### Agentes activos

`PM agent` · `OST Facilitator skill`

### Roles de la tríada

| Rol | Actividad principal en el Día 1 |
|-----|-------------------------------|
| **PM** | Lidera el kickoff, facilita el workshop, toma la decisión de priorización |
| **Designer** | Captura pain points del asegurado, identifica momentos de fricción en el flujo de cobertura |
| **Engineer** | Evalúa disponibilidad de APIs de cobertura, identifica restricciones del sistema legacy |

### Momento WOW

Claude construye el `OST` completo en tiempo real durante el workshop — cada oportunidad que el equipo nombra aparece en el repo en segundos. Al cierre del día, el documento de `sizing` y `prioritization` ya está listo.

### Cierre del día

`shape/oportunidades-sizing-priorizacion.md` con `status: completed`. `OST` con `leaf node` marcado (`selected: true`).

---

## Día 2 — Ideate: De la oportunidad a las ideas de solución

**Objetivo del día**: Generar un espacio amplio de soluciones posibles para la oportunidad elegida. Mapear `critical assumptions`. Diseñar el `test plan`.

### Actividades

1. **Claude facilita sesión de ideación estructurada**: analogías ("¿cómo resuelve esto Amazon?"), "How Might We" (HMW), inversión de supuestos ("¿qué pasaría si el asegurado no tuviera que preguntar?").
2. **Mapeo de `critical assumptions`** por idea: supuestos de `desirability`, `business viability` y `technical feasibility`.
3. **Diseño del `Solution Assumption Test Plan`**: qué validar, con qué método, a qué costo, cuál es el `success criterion`.

### Ideas generadas en la sesión (ejemplo)

| Idea | Evaluación inicial |
|------|-------------------|
| **Conversational AI assistant** (lenguaje natural, mobile) | `high impact` · `medium effort` · **elegida para validar** |
| Coverage calculator widget (formulario guiado) | `medium impact` · `low effort` |
| PDF de póliza con búsqueda semántica | `low impact` · `low effort` |
| WhatsApp bot | `medium impact` · `medium effort` |
| Chatbot con árbol de decisión (reglas) | `medium impact` · `low effort` |

### `Critical assumptions` para el Conversational AI assistant

| `Assumption` | `Risk level` | Método de validación |
|-------------|-------------|---------------------|
| El asegurado confía en una IA para decisiones de cobertura | `high` | Entrevistas de usuario |
| El asegurado prefiere lenguaje natural vs. formulario | `high` | Entrevistas + `Wizard of Oz` test |
| La API de cobertura tiene suficiente granularidad para responder bien | `medium` | Spike técnico |
| El asegurado usa el asistente desde el móvil en el momento de atención | `medium` | Entrevistas |

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `ideate-validate/ideas.md` | Ideas con evaluación de `impact` y `effort` |
| `ideate-validate/solution-assumptions.md` | `Critical assumptions` del Conversational AI assistant, clasificados por `risk level` |
| `ideate-validate/test-plan.md` | `Test plan`: 5 entrevistas + `Wizard of Oz` test, `success criteria` definidos |

### Agentes activos

`PM agent` · `Designer agent`

### Roles de la tríada

| Rol | Actividad principal en el Día 2 |
|-----|-------------------------------|
| **PM** | Filtra ideas por impacto de negocio y estrategia de NexHealth |
| **Designer** | Lidera la ideación UX, propone flujos de usuario por idea, identifica supuestos de `desirability` |
| **Engineer** | Señala supuestos técnicos críticos sobre la API de cobertura, estima complejidad relativa |

### Cierre del día

`ideate-validate/test-plan.md` con `status: ready`. `Critical assumptions` mapeados y clasificados por `risk level`.

---

## Día 3 — Validate: De los supuestos a la evidencia

**Objetivo del día**: Ejecutar el `test plan` sobre los `critical assumptions` de mayor riesgo. Elegir una solución respaldada en evidencia.

### Actividades

1. **Ejecución del `test plan`**: 5 entrevistas con asegurados digitales (25-40 años) + sesión `Wizard of Oz` donde el Designer responde como si fuera la IA mientras el PM facilita.
2. **Claude documenta los hallazgos** usando el `Interview Snapshot skill`, los traza al `OST`.
3. **Síntesis**: qué supuestos se confirmaron, cuáles se refutaron, qué aprendimos sobre el asegurado.
4. **Decisión documentada**: qué solución se elige, por qué, con qué evidencia.

### Hallazgos clave del `test plan` (ejemplo)

| `Assumption` | Resultado | Hallazgo |
|-------------|-----------|---------|
| Confía en IA para decisiones de cobertura | ✅ Confirmado | "Si me dice sí, voy al médico. Si me dice no, llamo para verificar." — confianza condicional aceptable |
| Prefiere lenguaje natural vs. formulario | ✅ Confirmado | El formulario causa abandono en el tercer campo |
| Usa el asistente desde el móvil | ✅ Confirmado | 4 de 5 participantes mencionaron "antes de ir" como momento clave |
| API tiene granularidad suficiente | ⚠️ Parcial | El API retorna cobertura por código FONASA, no por nombre de prestación — requiere capa de traducción |

**Solución elegida**: Conversational AI assistant — Coverwise MVP con traducción de lenguaje natural a código de prestación y respuesta de cobertura en lenguaje simple.

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `ideate-validate/evidencia/EV-001.md` ... `EV-005.md` | `Interview snapshots` de cada sesión de validación |
| `contexto/estrategia/evidencia-validada.md` | Conocimiento validado del squad actualizado con los hallazgos |
| `ideate-validate/solucion-elegida.md` | Solución elegida con justificación y trazabilidad a evidencia (`EV-001` ... `EV-005`) |
| `contexto/estrategia/ost.md` v2 | `OST` actualizado con soluciones y `assumption tests` mapeados |

### Agentes activos

`PM agent` · `Designer agent` · `Interview Snapshot skill`

### Roles de la tríada

| Rol | Actividad principal en el Día 3 |
|-----|-------------------------------|
| **PM** | Conduce las entrevistas, facilita el `Wizard of Oz` test |
| **Designer** | Diseña prototipo `lo-fi` para el test; captura hallazgos de UX sobre el flujo conversacional |
| **Engineer** | Evalúa el hallazgo del API (capa de traducción FONASA): es buildeable, agrega ~1 día de esfuerzo |

### Cierre del día

`ideate-validate/solucion-elegida.md` con `status: completed`. `OST` v2 con soluciones mapeadas y `assumption tests` documentados.

---

## Día 4 — Handoff: De la solución a las specs

**Objetivo del día**: Producir specs con el nivel de detalle suficiente para que Claude Code construya Coverwise sin ambigüedad.

### Actividades

1. **Claude (modo `Spec-Driven Development agent`)** descompone Coverwise en `features` y `user stories`, trazadas al `OST`.
2. **Por cada `feature`**: `acceptance criteria`, `edge cases`, decisiones de UI/UX, restricciones técnicas.
3. **Engineer revisa y aprueba** las specs desde la perspectiva de implementación. PM valida vs. intención del producto.
4. **Claude genera el `release plan`** con dependencias y orden de construcción.

### Features de Coverwise MVP

| `Feature` | Descripción | `Priority` |
|-----------|-------------|-----------|
| `FEAT-001` | **Coverage query interface** — campo de texto libre, sugerencias de autocompletado por prestación | `P0` |
| `FEAT-002` | **Coverage result display** — respuesta clara: `covered` / `not covered` / `partial coverage` + detalle del tope y condiciones | `P0` |
| `FEAT-003` | **Procedure name resolver** — capa de traducción entre nombre en lenguaje natural y código de prestación (mock de API para demo) | `P0` |
| `FEAT-004` | **Fallback to human agent** — cuando la confianza del `resolver` es baja, escalar con contexto al agente humano | `P1` |
| `FEAT-005` | **Coverage history** — últimas 3 consultas del usuario para referencia rápida | `P2` |

### Ejemplo de spec: `FEAT-001 — Coverage query interface`

```
user story: Como asegurado de NexHealth, quiero escribir en lenguaje natural
la prestación que necesito para obtener una respuesta de cobertura inmediata.

acceptance criteria:
- El campo acepta input de texto libre (mínimo 3 caracteres para activar sugerencias)
- Se muestran máximo 5 sugerencias de prestación mientras el usuario escribe
- El usuario puede seleccionar una sugerencia o continuar escribiendo
- El campo es accesible desde mobile (touch target ≥ 44px)
- Si no hay sugerencias, mostrar mensaje: "No encontramos esa prestación. ¿Quieres hablar con un ejecutivo?"

edge cases:
- Input vacío: no lanzar query
- Input con typos comunes: resolver debe manejar variantes ("radiografia" / "radiografía" / "rayos x")
- Prestaciones excluidas del plan: mostrar resultado "not covered" con explicación, no error
```

### Artefactos producidos

| Archivo | Descripción |
|---------|-------------|
| `handoff-delivery/specs/activas/FEAT-001.md` | Spec: `Coverage query interface` |
| `handoff-delivery/specs/activas/FEAT-002.md` | Spec: `Coverage result display` |
| `handoff-delivery/specs/activas/FEAT-003.md` | Spec: `Procedure name resolver` |
| `handoff-delivery/specs/activas/FEAT-004.md` | Spec: `Fallback to human agent` |
| `handoff-delivery/release-plan.md` | `Release plan` con orden de implementación: `FEAT-003` → `FEAT-001` → `FEAT-002` → `FEAT-004` |
| `contexto/estrategia/backlog.md` | `Backlog` priorizado listo para desarrollo |

### Agentes activos

`Spec-Driven Development agent` · `Engineer agent`

### Roles de la tríada

| Rol | Actividad principal en el Día 4 |
|-----|-------------------------------|
| **PM** | Valida que cada spec refleje la intención del producto y los OKRs del Día 1 |
| **Designer** | Completa los detalles UX en cada spec: flujos conversacionales, estados de respuesta, `error handling` |
| **Engineer** | Lidera la aprobación técnica, confirma el approach del `resolver` (mock API), estima esfuerzo del `FEAT-003` |

### Cierre del día

Todas las specs en `handoff-delivery/specs/activas/` con `status: approved`. `Release plan` completo con dependencias.

---

## Día 5 — Build + Deploy: Del repo al producto en producción

**Objetivo del día**: Construir Coverwise guiado por las specs del Día 4 y desplegarlo en producción. Demo a NexHealth.

### Actividades

1. **Claude Code construye Coverwise** guiado por las specs aprobadas — en el mismo repo, desde el `SDPB-Context`, respetando el `release plan`.
2. **Engineer revisa el código** generado, cierra el loop de calidad (`unit tests`, `edge cases` de las specs).
3. **Deploy a Cloudflare Pages** (`npx wrangler pages deploy ./dist` o direct upload desde el dashboard).
4. **Apuntar dominio** `coverwise.becerra-ojeda.cl` como custom domain en el Cloudflare Pages project — propagación instantánea si el dominio ya está en Cloudflare.
5. **Demo a NexHealth**: walkthrough del `SDPB-Context repo` + producto vivo en la URL.

### Stack de Coverwise (para la demo)

| Capa | Tecnología |
|------|-----------|
| `Frontend` | React + Tailwind CSS (mobile-first) |
| `Backend` | Cloudflare Workers (API routes, procedure resolver) |
| `AI layer` | Claude API (`claude-sonnet-4-6`) — interpreta la query y estructura la respuesta |
| `Coverage resolver` | Mock data de prestaciones NexHealth (JSON estático para demo) |
| `Deploy` | Cloudflare Pages (frontend) + Workers (backend) |
| `Domain` | `coverwise.becerra-ojeda.cl` → Cloudflare Pages custom domain |

### Artefactos producidos

| Entregable | Descripción |
|------------|-------------|
| **Coverwise** en producción | Accesible en `https://coverwise.becerra-ojeda.cl` |
| `Codebase` | Código fuente en rama del repo — buildado 100% por Claude Code desde las specs |
| `bitacora/bitacora-agentica.md` actualizada | Registro del ciclo completo: `Shape` → `Ideate & Validate` → `Handoff` → `Build` |

### Agentes activos

`Engineer agent` · Claude Code (`build mode`)

### Roles de la tríada

| Rol | Actividad principal en el Día 5 |
|-----|-------------------------------|
| **Engineer** | Lidera el `build`, supervisa la salida de Claude Code, gestiona el `deploy` y el DNS |
| **PM** | Prepara y facilita la demo a NexHealth |
| **Designer** | Guía el walkthrough del UX durante la demo: flujo conversacional, estados de respuesta |

### Momento WOW

Claude Code construye Coverwise directamente desde las specs del `SDPB-Context repo`. El `Engineer` no escribe una línea — revisa, aprueba y hace `deploy`. El cliente ve su idea en producción cinco días después de haberla planteado. La URL en vivo es el cierre de la demo.

### Cierre del día

Coverwise accesible en `coverwise.becerra-ojeda.cl`. `bitacora/bitacora-agentica.md` con el ciclo completo documentado.

---

## Resumen del engagement — NexHealth / Coverwise

| Día | Sub-proceso E2E-SDPB | `Output` clave | `Agent` principal |
|-----|---------------------|----------------|-----------------|
| 1 | `Shape` | `OST` con `leaf node` elegido: "El asegurado no sabe si su prestación está cubierta" | `PM agent` + `OST Facilitator skill` |
| 2 | `Ideate & Validate — Ideate` | Ideas + `Test Plan` para el Conversational AI assistant | `PM agent` + `Designer agent` |
| 3 | `Ideate & Validate — Validate` | Solución elegida: Coverwise MVP con `procedure resolver` | `PM agent` + `Designer agent` + `Interview Snapshot skill` |
| 4 | `Handoff to Delivery` | 4 specs aprobadas + `Release Plan` | `SDD agent` + `Engineer agent` |
| 5 | `Build + Deploy` | Coverwise en `coverwise.becerra-ojeda.cl` | Claude Code |

---

## OKRs del engagement (para la demo)

Los ejecutivos de NexHealth midieron el éxito del engagement con estos `OKRs`:

| `Objective` | `Key Result` |
|-------------|-------------|
| Reducir carga del call center por consultas de cobertura | Reducción del 30% en llamadas por cobertura en los primeros 60 días post-lanzamiento |
| Mejorar experiencia del asegurado en el momento de atención | `NPS` del flujo de consulta de cobertura ≥ 70 |
| Validar la propuesta antes de invertir en desarrollo | Solución elegida con evidencia en 3 días — sin código escrito aún |

---

*Plan aplicado al caso NexHealth / Coverwise. Fuente canónica del workflow: `_demo/plan-5-dias.md`.*
