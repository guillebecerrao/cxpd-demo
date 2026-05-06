---
title: "Framework E2E-SDPB — End-to-End Spec-Driven Product Building"
author: Guillermo Becerra
created: 2026-03-17
last_modified: 2026-04-19
last_modified_by: Claude (harvest triad-sdpb-main + clarificación semántica)
version: 2.4
modification_count: 5
status: active
---

# Framework E2E-SDPB — End-to-End Spec-Driven Product Building

> **Lectura obligatoria** antes de trabajar en este repositorio.
> Este documento define cómo trabaja la tríada de producto y cómo opera Claude dentro del framework.

---

## 1. Qué es AI Native Product Development with Spec-Driven mindset.

Spec-Driven Development (SDD) es un paradigma de trabajo donde **todo lo que se construye primero se especifica**, y **todo lo que se especifica se respalda en evidencia de discovery**. Las especificaciones son el artefacto central que guía diseño, implementación y validación.

La tríada de producto (PM + Designer + Engineer) opera como **Product Builders**: no solo definen qué construir, sino que producen las especificaciones con el nivel de detalle necesario para que el equipo de desarrollo pueda implementar con mínima ambigüedad.

### Principio fundamental

```
Evidencia → Especificación → Implementación → Validación
    ↑                                              │
    └──────────────── Aprendizaje ─────────────────┘
```

Nada se construye sin spec. Ninguna spec se escribe sin evidencia. Todo lo construido se valida.

### Topología de implementación

El framework E2E-SDPB se implementa a través de dos tipos de repositorios:

| Repo | Identificador de tipo | Propósito |
|------|-----------------------|-----------|
| **Context repo** | `SDPB-Context` | Discovery, specs, artefactos del framework. Sigue el template de `AI-Framework/`. |
| **Codebase repo(s)** | — | Código fuente del producto. Uno o más repos según la arquitectura. |

Todo producto dentro del framework tiene al menos un SDPB-Context repo. Los codebase repos son independientes y viven por separado. La carpeta `AI-Framework/` en product-building es el template canónico de un SDPB-Context repo.

### Modos de operación

| Modo | Descripción | Topología |
|------|-------------|-----------|
| **Team mode** | PM + Designer + Engineer producen specs; un equipo de dev externo construye. | SDPB-Context repo + codebase repo(s) separados |
| **Solo-builder mode** | Una persona cubre todos los roles del producto. | SDPB-Context repo + codebase repo(s) separados. Para productos simples y personales, se acepta un mono-repo que combine contexto y código, declarado como tal en `syncignore.md`. |

---

## 2. La tríada de producto

### Composición

| Rol | Responsabilidad principal en SDD |
|-----|----------------------------------|
| **Product Manager** | Priorización, problem framing, product briefs, backlog, métricas, stakeholder management |
| **Product Designer** | Research de usuario, experiencia, user flows, prototipos, validación de usabilidad |
| **Product Engineer** | Viabilidad técnica, arquitectura, trade-offs, acceptance criteria, integración con dev team |

### Modelo de trabajo

La tríada trabaja de forma **mixta**: sesiones sincrónicas para alinear y decidir, trabajo asincrónico individual para producir artefactos. Cada miembro contribuye desde su expertise, pero todos revisan y aprueban las specs antes del handover.

### El coach _(opcional)_

En algunos equipos, un coach externo trabaja en modelo 2-in-a-Box con la PM, guiando la transformación hacia Continuous Discovery & Delivery. No es miembro permanente de la tríada pero participa activamente en la formación de la práctica.

---

## 3. Gestión del contexto compartido

### Por qué el contexto importa en este repositorio

En SDD, ninguna spec se escribe sin evidencia. Esa evidencia vive en el repositorio: en el OST, en los hallazgos de discovery, en las decisiones técnicas documentadas, en los artefactos de ciclos anteriores. El repositorio no es un archivo de documentos — es el sistema de contexto compartido del squad.

En un equipo que trabaja de forma mixta (sincrónico y asincrónico, humano y agente), este contexto crece con cada ciclo. Sin una arquitectura de acceso explícita, crecer se convierte en un problema: más documentos significa más ruido, más tiempo buscando qué leer y mayor riesgo de trabajar con información desactualizada o incompleta.

**Principio de diseño del repositorio:**

```
Archivos estratégicos centralizados (fuente única)
    +
Índices de sub-proceso (acceso selectivo por tarea)
    =
Contexto relevante sin sobrecarga
```

- **Centralización:** Todo el conocimiento estratégico vive en `contexto/estrategia/`. Ningún sub-proceso lo duplica ni copia.
- **Acceso selectivo:** Cada sub-proceso tiene un `_contexto/indice-contexto.md` que define exactamente qué subset del repositorio es input para ese momento del trabajo.

### Estructura mínima de un índice de contexto

Todo `_contexto/indice-contexto.md` debe definir los siguientes bloques:

| Bloque | Contenido | Nivel |
|--------|-----------|-------|
| **Input estratégico** | Archivos de `contexto/estrategia/` relevantes (OST, evidencia-validada, roadmaps) | 🔴 Crítico |
| **Output del sub-proceso anterior** | El artefacto de cierre que es input de este sub-proceso | 🔴 Crítico |
| **Artefactos del ciclo activo** | Los archivos de trabajo del sub-proceso en el ciclo en curso | 🔴 Crítico |
| **Contexto condicional** | Archivos que solo se cargan si se cumple una condición explícita (ej. tech-stack si hay decisiones técnicas pendientes, design-system si hay prototipo) | 🔵 Condicional |
| **Restricciones** | Qué no cargar por defecto en este sub-proceso y por qué | 🟡 Recomendado |

**Niveles de prioridad:**

| Nivel | Significado |
|-------|-------------|
| 🔴 Crítico | Avanzar sin este contexto tiene alta probabilidad de generar trabajo que hay que rehacer. Se levanta un warning explícito si no está disponible. |
| 🟡 Recomendado | Tenerlo mejora significativamente la calidad. Sin él se puede avanzar, con riesgo conocido y declarado. |
| 🔵 Condicional | Cargar solo si se cumple la condición indicada en el índice. |

> **Garbage in, garbage out.** El equipo puede avanzar con el contexto disponible — el framework no es bloqueante. Lo que sí hace es señalar el riesgo: las decisiones serán tan buenas como la información que las respalda. Si se avanza sin contexto crítico, documentarlo como supuesto en el artefacto correspondiente.

### Índices por sub-proceso

| Sub-proceso | Índice | Input estratégico base |
|-------------|--------|------------------------|
| Shape | `shape/_contexto/indice-contexto.md` | OST · evidencia-validada · roadmap-discovery-shape |
| Ideate & Validate | `ideate-validate/_contexto/indice-contexto.md` | OST (nodo hoja marcado) · evidencia-validada · output de Shape |
| Handoff to Delivery | `handoff-delivery/_contexto/indice-contexto.md` | OST · evidencia-validada · output de I&V · tech-stack · design-system |

---

## 4. Los sub-procesos del product lifecycle

El trabajo del product builder (persona, tríada o equipo) se organiza en sub-procesos que componen un ciclo completo de producto. Cada sub-proceso tiene su propia carpeta, su índice de contexto y sus artefactos.

```
Shape ──────────────→ Ideate & Validate ──────────────→ Handoff to Delivery ──→ Build
  │                         │                                    │                 │
  │ Oportunidad nodo        │ Solución elegida                   │ Specs +         │ Producto
  │ hoja elegida            │ con evidencia                      │ Release Plan    │ funcional
  ↓                         ↓                                    ↓                 ↓
contexto/estrategia/ost.md actualizado en cada etapa              Validación → Aprendizaje
```

### Política de bypass de sub-procesos

Un sub-proceso puede omitirse cuando su output ya existe o cuando su propósito
no aplica al contexto del producto. La omisión requiere un ADR que documente:

- Qué sub-proceso se omite
- Por qué su propósito no aplica (ej: oportunidad obvia, stack ya decidido,
  solución conocida)
- Qué artefactos se producen en su lugar (si hay alguno)

Ejemplos legítimos de bypass:
- Infraestructura pura (no hay incertidumbre de producto): saltar Shape e
  Ideate & Validate, ir directo a specs
- Producto con decisiones de diseño ya tomadas: saltar Ideate & Validate
- Producto existente que se incorpora al framework: iniciar desde el estado
  actual, no desde Shape

El bypass no es una excepción — es una regla del framework. Lo que no se
permite es omitir un sub-proceso sin justificación documentada.

---

### 4.1 Shape

**Propósito:** Descubrir y priorizar oportunidades. Termina con un nodo hoja del OST elegido con criterio explícito de sizing y priorización.

**Contexto:** Ver `shape/_contexto/indice-contexto.md`

**Artefactos producidos:**

| Artefacto | Archivo |
|---|---|
| Análisis de oportunidades | `shape/analisis-oportunidades.md` |
| Sizing y priorización de oportunidades | `shape/oportunidades-sizing-priorizacion.md` |
| Opportunity Assumption Awareness | `shape/opportunity-assumptions.md` |
| Experience Map (si aplica) | `shape/experience-map.md` |
| OST actualizado (hasta Opportunity level) | `contexto/estrategia/ost.md` |
| Roadmap Discovery Shape actualizado | `contexto/estrategia/roadmap-discovery-shape.md` |

**Actividad crítica — Sizing y Priorización:**
Una vez identificadas y agrupadas las oportunidades en el OST, facilitar un ejercicio de sizing y priorización jerárquica por ramas. El objetivo es concluir en una **oportunidad nodo hoja elegida** con criterio explícito. Sin completar este ejercicio, Shape no está cerrado.
- Referencia metodológica: Capítulo 6 (Opportunity Mapping) y Capítulo 7 (Sizing y Priorización), *Continuous Discovery Habits*, Teresa Torres.

**Representación del nodo elegido en el OST:** El árbol completo se preserva siempre. El nodo hoja elegido se marca con `selected: true` y el camino desde el Business Outcome hasta ese nodo con `on_selected_path: true`. En la presentación HTML, el camino se destaca visualmente y el resto del árbol permanece visible en estado secundario.

**Cierre de Shape:** `shape/oportunidades-sizing-priorizacion.md` y `shape/opportunity-assumptions.md` con `status: completed`. OST actualizado con nodo hoja marcado.

---

### 4.2 Ideate & Validate

**Propósito:** Generar ideas de solución para la oportunidad elegida, identificar y validar sus supuestos, y elegir una solución respaldada en evidencia.

**Contexto:** Ver `ideate-validate/_contexto/indice-contexto.md`

**Artefactos producidos:**

| Artefacto | Archivo |
|---|---|
| Registro de ideas | `ideate-validate/ideas.md` |
| Solution Assumption Awareness | `ideate-validate/solution-assumptions.md` |
| Solution Assumption Test Plan | `ideate-validate/test-plan.md` |
| Plan de Discovery Validación | `ideate-validate/plan-discovery-validacion.md` |
| Prototipos | `ideate-validate/prototipos/` |
| Evidencia de validación | `ideate-validate/evidencia/` |
| Solución elegida | `ideate-validate/solucion-elegida.md` |
| OST completo actualizado | `contexto/estrategia/ost.md` |

**Criterio de fidelidad del prototipo:**
- **Alta fidelidad / producto real local**: feature de baja complejidad, reversible, baja incertidumbre técnica. El handoff a ingeniería puede ser solo testing e integración.
- **Baja fidelidad / demo funcional**: feature con alta incertidumbre o decisiones de arquitectura pendientes. El prototipo complementa las specs.

- Referencia metodológica: Capítulo 10 (Ideación), *Continuous Discovery Habits*, Teresa Torres.

**Cierre de Ideate & Validate:** `ideate-validate/solucion-elegida.md` con `status: completed`. OST actualizado con soluciones y assumption tests mapeados.

---

### 4.3 Handoff to Delivery

**Propósito:** Convertir la solución elegida en especificaciones de desarrollo listas para el equipo de ingeniería, con backlog priorizado y release plan.

**Contexto:** Ver `handoff-delivery/_contexto/indice-contexto.md`

**Artefactos producidos:**

| Artefacto | Archivo |
|---|---|
| Lista de PBIs | `handoff-delivery/pbi-list.md` |
| Release Plan | `handoff-delivery/release-plan.md` |
| Specs (una por PBI/feature) | `handoff-delivery/specs/activas/[nombre].md` |
| Prototipo de alta fidelidad (si aplica) | `handoff-delivery/prototipos/` |
| Backlog actualizado | `contexto/estrategia/backlog.md` |
| Roadmap Delivery actualizado | `contexto/estrategia/roadmap-delivery.md` |

**Estructura mínima de una spec (PRD):** Problem statement · Business outcome vinculado (OST) · Audiencias / User personas · Target JTBD · Solución propuesta · Flujos de usuario · Casos de borde · Criterios de aceptación · Requerimientos no funcionales · Ejemplos concretos · Notas para ingeniería.

**Calidad para Spec-Kit:** Las specs deben ser input directo para herramientas asistidas por LLM (como Spec-Kit): lenguaje preciso, criterios de aceptación testeables, ejemplos explícitos, casos de borde documentados.

**Cierre de Handoff to Delivery:** Specs en `activas/` con `status: draft` listas para revisión. Release plan con `status: completed`.

---

### 4.4 Build

**Propósito:** Convertir las specs aprobadas en producto funcional. Es la fase
donde las decisiones de producto se materializan en código, configuración e
infraestructura.

**Quién ejecuta el build depende del modo de operación:**

| Modo | Quién construye |
|------|-----------------|
| Solo builder + agentes | El builder ejecuta el build asistido por agentes de IA. Speckit es la herramienta recomendada para orquestar la implementación. |
| Tríada + dev team | Las specs se entregan al dev team, que implementa con su propio tooling y proceso. |
| Híbrido | Combinación según la naturaleza de cada spec. |

**Build agéntico con Speckit:**

Cuando el build es ejecutado por agentes (modo solo builder o híbrido), Speckit
orquesta la implementación. Los artefactos del framework alimentan Speckit, pero
la forma específica depende del estado inicial del producto:

- **Producto nuevo (post-seed):** ADRs y decisiones técnicas → constitution de
  speckit. Specs aprobadas de handoff-delivery → `/speckit.specify`. Stack →
  `/speckit.plan`.
- **Producto existente (incorporado):** La constitution de speckit puede ya
  existir. Las specs pueden alimentar speckit parcialmente o completas según
  lo que ya esté implementado.

**Paso obligatorio:** Antes de ejecutar `/speckit.implement`, ejecutar
`/speckit.analyze` para detectar inconsistencias, dependencias faltantes y
riesgos. Los issues detectados deben resolverse antes de proceder.

**Pipeline Speckit (referencia):**
```
/speckit.constitution → /speckit.specify → /speckit.plan → /speckit.tasks → /speckit.analyze → /speckit.implement
```

**Cierre de Build:** Producto deployado y verificado. Las specs pasan a `in_dev`
o `validated` según el resultado. Los aprendizajes del build se registran en
`framework-learnings.md`.

---

## 5. Ciclo de vida de una spec

| Estado | Significado | Quién actúa |
|--------|-------------|-------------|
| `draft` | En construcción. Puede cambiar libremente. | Cualquier miembro de la tríada |
| `in_review` | Lista para revisión de la tríada. | Tríada completa revisa |
| `approved` | Aprobada por la tríada. Lista para entrar al sprint. | Tríada en sesión |
| `in_dev` | En implementación por el equipo de desarrollo. | Dev team |
| `validated` | Implementada y validada con experimento post-build. | PM + Designer |

### Reglas

1. Solo la tríada completa puede mover una spec a `approved`.
2. Specs en `in_dev` no se modifican sin comunicar al dev team. Si hay cambio, se crea nueva versión.
3. Specs en `draft` son borradores libres. Cualquier miembro puede iterar.
4. Toda spec debe trazarse a una oportunidad en `contexto/estrategia/ost.md` o a un JTBD documentado.

---

## 6. Políticas de gestión

### 6.1 Continuidad antes que reinicio

Cuando se inicia trabajo en un sub-proceso, Claude **primero lee el estado de los artefactos existentes** antes de proponer cualquier movimiento de archivos.

- **Si hay artefactos `in_progress`**: anunciar que hay trabajo en curso y proponer continuar. No mover archivos.
- **Si los artefactos están `completed`**: anunciar que el ciclo anterior está cerrado y preguntar si se desea iniciar un nuevo ciclo. Si el usuario confirma, sugerir movimientos a `_historia/` pero esperar confirmación antes de ejecutar.
- **Si no hay artefactos previos**: anunciar que se está iniciando el primer ciclo y proceder.

Claude debe ser explícito sobre la decisión que toma o la pregunta que hace. Nunca proceder silenciosamente.

### 6.2 Versionado e iteraciones

- Los artefactos activos siempre están en el path principal del sub-proceso.
- Los artefactos de ciclos cerrados van a `[sub-proceso]/_historia/` con nombre `[archivo]_YYYY-MM-DD.md`.
- **Claude nunca lee `_historia/` por defecto.** Solo si el usuario lo indica explícitamente.

### 6.3 Status de artefactos

Todo artefacto de sub-proceso incluye en su frontmatter YAML:
```yaml
status: in_progress   # o: completed
last_modified: YYYY-MM-DD
```

### 6.4 Bitácora agéntica

Claude actualiza `bitacora/bitacora-agentica.md` en estos momentos:

1. **Cierre de sub-proceso completo.**
2. **Cierre de sesión anunciado** por el usuario.
3. **Checkpoint por volumen**: cuando se acumula trabajo significativo sin cierre anunciado, Claude sugiere al usuario si desea guardar un checkpoint. No lo hace sin confirmación.
4. **Inicio de sesión**: Claude lee la bitácora para recuperar contexto y propone retomar desde donde se dejó.

### 6.5 Bitácora humana

Actualizada mediante el skill `actualizar-bitacora-humana`. Consolida notas desde `trabajo-individual/[persona]/notas/YYYY-WW_[persona].md`. Cualquier miembro puede activarlo.

### 6.6 Retrospectiva por sub-proceso

Al cerrar un ciclo, el skill `cierre-de-ciclo` facilita una retrospectiva del **proceso** (no del producto) en:
- `shape/_retro/retro-shape.md`
- `ideate-validate/_retro/retro-ideate-validate.md`
- `handoff-delivery/_retro/retro-handoff-delivery.md`

Claude sugiere movimientos de archivos a `_historia/` pero no los ejecuta sin confirmación. El usuario puede ejecutarlos, diferirlos o solo documentar las ideas para reestructuraciones futuras.

### 6.7 Presentaciones HTML ejecutivas

El skill `generar-presentacion-html` convierte cualquier artefacto estratégico en una presentación HTML ejecutiva almacenada en `presentaciones/YYYY-MM-DD_[nombre].html`.

- Claude siempre pregunta al usuario antes de generar, incluso si el `.md` acaba de ser editado.
- Los HTMLs son artefactos generados. Nunca editarlos manualmente.
- Para el OST: el HTML renderiza el árbol completo con el camino elegido destacado visualmente. El resto del árbol permanece visible en estado secundario.
- `presentaciones/` es accesible en GitLab para stakeholders con acceso Guest.

---

## 7. Reglas de comportamiento de Claude

Claude debe respetar siempre estas reglas al trabajar en este repositorio:

1. **No leer `_historia/` por defecto.** Solo si el usuario lo indica explícitamente.
2. **No leer `legacy/` por defecto.** Solo como referencia histórica si el usuario lo solicita.
3. **No leer `contexto/extendido/` por defecto.** Solo cuando una regla de sub-proceso lo requiera o el usuario lo indique.
4. **Fuente única del OST.** Vive en `contexto/estrategia/ost.md`. Nunca copiar ni duplicar.
5. **Leer el estado antes de iniciar un sub-proceso.** Evaluar artefactos existentes y anunciar al usuario el estado. Siempre ser explícito.
6. **Confirmar antes de mover archivos a `_historia/`.** Claude sugiere, no ejecuta sin aprobación.
7. **Confirmar antes de generar HTML.** Siempre preguntar al usuario primero.
8. **Toda spec nueva se crea con `status: draft`.** Nunca en `approved` o `in_dev`.
9. **No modificar specs `approved` o `in_dev`** sin autorización explícita.
10. **Leer `bitacora/bitacora-agentica.md` al inicio de cada sesión** para recuperar contexto.
11. **Leer `_contexto/indice-contexto.md`** al iniciar trabajo en un sub-proceso para saber qué archivos cargar.
12. **Privacidad de `trabajo-individual/`.** Nunca cruzar información entre carpetas de personas distintas.
13. **Los inputs durante sesiones no son listas taxativas.** Las listas de inputs en las definiciones de sub-proceso son ejemplos orientadores, no restricciones.

---

## 8. Estructura del repositorio

```
[raíz]
├── CLAUDE.md                          # Instrucciones para el LLM
├── framework.md                       # Este documento
├── README.md
│
├── agentes/                           # System prompts especializados
├── skills/                            # Protocolos de tarea
│   ├── ost-facilitator.md
│   ├── interview-snapshot.md
│   ├── actualizar-bitacora-humana.md
│   ├── cierre-de-ciclo.md
│   └── generar-presentacion-html.md
│
├── bitacora/
│   ├── bitacora-agentica.md
│   └── bitacora-humana.md
│
├── presentaciones/                    # HTMLs para comunicación con stakeholders
│
├── contexto/
│   ├── corporativo/                   # Estrategia de producto, estructura organizacional
│   ├── squad/                         # squad.md, glosario
│   ├── estrategia/                    # OST, evidencia-validada, roadmaps, backlog, épicas
│   ├── design-system/                 # Tokens, componentes
│   ├── tech-stack/                    # ADRs, stack tecnológico
│   └── extendido/                     # Libros e investigación (NO leer por defecto)
│
├── shape/                             # Sub-proceso 1
│   ├── _contexto/indice-contexto.md
│   ├── _historia/                     # Ciclos anteriores (NO leer por defecto)
│   ├── _retro/retro-shape.md
│   └── entrevistas/
│
├── ideate-validate/                   # Sub-proceso 2
│   ├── _contexto/indice-contexto.md
│   ├── _historia/
│   ├── _retro/retro-ideate-validate.md
│   ├── evidencia/
│   └── prototipos/
│
├── handoff-delivery/                  # Sub-proceso 3
│   ├── _contexto/indice-contexto.md
│   ├── _historia/
│   ├── _retro/retro-handoff-delivery.md
│   ├── specs/
│   │   ├── _templates/
│   │   ├── activas/
│   │   └── cerradas/
│   └── sprints/
│
├── framework-learnings.md             # Aprendizajes capturados (E2E-SDPB learning loop)
├── syncignore.md                      # Divergencias intencionales del template
│
├── src/                               # Código fuente del producto (si aplica)
├── [otros directorios de código]      # Según tech-stack del producto
│
├── legacy/                            # Solo referencia histórica (NO leer por defecto)
└── trabajo-individual/                # Privado por persona
    └── [persona]/notas/
```

### Principio de contexto autocontenido

El SDPB-Context repo de un producto es autocontenido: toda la información estratégica,
de equipo y de ciclo de trabajo necesaria para operar el framework vive en él.
Cualquier sesión de trabajo en el contexto tiene todo lo que necesita sin
dependencias externas al repo de contexto.

El codebase repo vive por separado. En modo solo-builder con productos simples,
contexto y código pueden coexistir en un mono-repo como excepción; debe declararse
explícitamente en `syncignore.md` bajo el área `repo-topology`.

### Dónde va cada cosa

| Quiero... | Lo pongo en... |
|-----------|---------------|
| Iniciar un ciclo de Shape | Leer `shape/_contexto/indice-contexto.md`, luego trabajar en `shape/` |
| Iniciar un ciclo de Ideate & Validate | Leer `ideate-validate/_contexto/indice-contexto.md`, luego trabajar en `ideate-validate/` |
| Escribir una nueva spec | `handoff-delivery/specs/activas/` usando template de `_templates/` |
| Agregar una entrevista nueva | Skill `interview-snapshot` → `shape/entrevistas/snapshots/` |
| Registrar conocimiento validado | `contexto/estrategia/evidencia-validada.md` |
| Actualizar el OST | `contexto/estrategia/ost.md` (fuente única) |
| Generar presentación para stakeholders | Skill `generar-presentacion-html` → `presentaciones/` |
| Preparar un handover a dev | `handoff-delivery/sprints/` |
| Tomar notas personales | `trabajo-individual/[persona]/notas/YYYY-WW_[persona].md` |
| Cerrar un ciclo de sub-proceso | Skill `cierre-de-ciclo` |

---

## 9. Modelo de branching con Git

### Tres niveles, un flujo por sub-proceso

| Nivel | Rama | Propósito |
|-------|------|-----------|
| 1 | `main` | Estado aprobado. Solo recibe merges de `triada`. Dev team hace pull aquí. |
| 2 | `triada` | Rama de integración de la tríada. Recibe merges de ramas de sub-proceso al cierre de cada ciclo. |
| 3 | `[sub-proceso]/ciclo-NN-YYYY` | Rama de trabajo activo por ciclo de sub-proceso. |
| 3b | `[sub-proceso]/ciclo-NN-YYYY/[actividad]` | Rama paralela dentro de un ciclo, nombrada por artefacto o actividad. Solo cuando dos o más miembros trabajan en simultáneo sobre artefactos claramente distintos. |

### Convención de nombres

```
# Nivel 3 — rama de sub-proceso
shape/ciclo-01-2026
ideate-validate/ciclo-01-2026
handoff-delivery/ciclo-01-2026

# Nivel 3b — ramas paralelas (nombradas por artefacto o actividad, nunca por persona)
shape/ciclo-01-2026/mapeo-experiencia
shape/ciclo-01-2026/sizing-priorizacion
ideate-validate/ciclo-01-2026/prototipo-flujo-pago
ideate-validate/ciclo-01-2026/test-plan-suposiciones
```

### Diagrama

```
main ──────────────────────────────────────────●──────→
                                               ↑ merge + tag
triada ──────────────────────────────────●────●──○──→
                                         ↑ merge
                                         │
shape/ciclo-01-2026 ──○──●──────────●───●
                          ↑ merge    ↑ merge
                          │          │
    shape/.../mapeo-experiencia ──○──●
    shape/.../sizing-priorizacion ──○──●
```

### Cuándo usar ramas paralelas (nivel 3b)

| Situación | Modelo recomendado |
|-----------|-------------------|
| Trabajo secuencial o artefactos independientes sin urgencia de paralelismo | Todos en la rama de sub-proceso (nivel 3) |
| Dos o más miembros trabajan en simultáneo sobre artefactos claramente distintos | Ramas paralelas nombradas por artefacto/actividad → merge a nivel 3 al completar |
| Dos miembros necesitan editar el mismo artefacto | No abrir ramas paralelas — resolver en sesión sincrónica |

**Guardrail de diseño:** El nombre de la rama debe indicar el artefacto o actividad que se modifica, no quién la trabaja. Si dos ramas activas bajo el mismo ciclo no pueden nombrarse con alcances distintos, es señal de que el trabajo debe coordinarse antes de paralelizar.

### Flujo de handover (una vez por sprint)

1. Asegurarse que todas las specs del sprint están en `approved`
2. Crear carpeta `handoff-delivery/sprints/sprint-XX/` con manifiesto y notas de handover
3. El engineer de la tríada hace merge: `git checkout main && git merge triada`
4. Tagear: `git tag sprint-XX-handover`
5. Push: `git push origin main --tags`
6. Comunicar al dev team que haga pull de `main`

### Anti-patrones de branching

| Anti-patrón | Problema | Alternativa |
|-------------|----------|-------------|
| Nombrar ramas por persona (`/pm`, `/designer`) | Oculta qué archivos se tocan y no garantiza separación de alcance | Nombrar por artefacto o actividad |
| Abrir ramas paralelas sobre el mismo artefacto | Genera conflictos de merge y decisiones divergentes | Trabajar en sesión sincrónica o secuencialmente |
| Trabajar directamente en `triada` durante un ciclo activo | Mezcla ciclos sin trazabilidad | Crear siempre la rama de sub-proceso (nivel 3) |
| No mergear la rama paralela antes del cierre del ciclo | La rama de sub-proceso queda incompleta para el merge a `triada` | Mergear al completar cada actividad, no acumular al final |

---

## 10. Agentes disponibles

| Agente | Archivo | Cuándo activarlo |
|--------|---------|-----------------|
| Product Management | `agentes/product-management.md` | Priorización, briefs, backlog, métricas, stakeholder comms |
| Spec Driven Development | `agentes/spec-driven-development.md` | Specs detalladas, acceptance criteria, edge cases |
| Ingeniería de Software | `agentes/ingenieria-software.md` | Viabilidad técnica, arquitectura, trade-offs |
| Product Design | `agentes/product-design.md` | Research, user flows, prototipos, design system |

---

## 11. Ceremonias del squad

| Ceremonia | Frecuencia | Objetivo | Participantes |
|-----------|-----------|----------|---------------|
| **Tríada sync** | 2-3x por semana | Alinear trabajo en curso, revisar artefactos, tomar decisiones | PM + Designer + Engineer |
| **Discovery review** | Semanal | Revisar hallazgos, actualizar OST, priorizar siguiente aprendizaje | Tríada + Coach |
| **Sprint planning** | Cada 2 semanas | Definir qué specs entran al próximo sprint de dev | Tríada |
| **Handover** | Cada 2 semanas | Entregar specs aprobadas al dev team | Tríada + Dev team |
| **Validation review** | Según necesidad | Revisar resultados de experimentos post-build | Tríada |
| **Stakeholder update** | Quincenal/mensual | Comunicar progreso y hallazgos | PM (+ tríada si necesario) |

---

## 12. Anti-patrones

| Anti-patrón | Por qué es un problema | Qué hacer en cambio |
|-------------|----------------------|---------------------|
| Escribir specs sin evidencia | Se construye sobre supuestos no validados | Buscar evidencia en `contexto/estrategia/evidencia-validada.md`. Si no hay, agregar al roadmap de discovery. |
| Saltar directo a soluciones | Se pierde el problema de vista | Completar Shape antes de entrar a Ideate & Validate |
| Aprobar specs sin revisión de tríada | Se pierden perspectivas críticas | Toda spec pasa por `in_review` antes de `approved` |
| Modificar specs en `in_dev` | Genera confusión y retrabajo en dev | Crear nueva versión o esperar al siguiente sprint |
| Leer `_historia/` sin que el usuario lo pida | Contamina el contexto activo con trabajo obsoleto | Solo leer artefactos activos por defecto |
| Copiar el OST en carpetas de sub-proceso | Genera dos fuentes de verdad | El OST siempre vive en `contexto/estrategia/ost.md` |
| Crear specs sin vincular al OST | Se pierde la trazabilidad problema → solución | Toda spec referencia una oportunidad del OST o un JTBD |

---

## 13. Checklist de onboarding

Para un nuevo miembro de la tríada:

- [ ] Leer este documento completo (`framework.md`)
- [ ] Leer `contexto/squad/squad.md` para entender el squad
- [ ] Leer `contexto/corporativo/estructura-organizacional.md` para entender la organización
- [ ] Leer `contexto/corporativo/estrategia-producto.md` para entender la estrategia del producto
- [ ] Revisar `contexto/squad/glosario.md` para familiarizarse con el vocabulario
- [ ] Revisar `contexto/estrategia/ost.md` para entender las oportunidades activas
- [ ] Revisar `contexto/estrategia/evidencia-validada.md` para conocer el conocimiento acumulado
- [ ] Configurar git: clonar el repo, verificar acceso a rama `triada`, familiarizarse con la convención de ramas por sub-proceso y actividad (ver Sección 9)
- [ ] Revisar los templates en `handoff-delivery/specs/_templates/`

---

*Este documento es un artefacto vivo. Actualizar cuando cambie el proceso de trabajo de la tríada.*

## Changelog

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 2.4 | 2026-04-19 | Claude (harvest triad-sdpb-main) | Clarificación semántica: E2E-SDPB como nombre del framework; SDPB-Context como identificador del tipo de context repo (reemplaza SDD-4-ProductTriad). Nueva subsección "Topología de implementación" y "Modos de operación" en Sección 1. Corrección del Principio de repositorio autocontenido → "Principio de contexto autocontenido": codebase vive separado; mono-repo es excepción declarable en syncignore. |
| 2.3 | 2026-03-30 | Claude (harvest guilles-blog) | Primer harvest E2E-SDPB: nueva sección 4.4 Build (build agéntico con Speckit, pipeline, analyze obligatorio). Política de bypass de sub-procesos con ADR. Principio de repositorio autocontenido (contexto + código juntos). Regla de branching condicional para mono-repo en CLAUDE.md. framework-learnings.md y syncignore.md en estructura de carpetas. |
| 2.2 | 2026-03-24 | Guillermo Becerra | Nueva Sección 3: Gestión del contexto compartido. Principio de centralización + acceso selectivo, estructura mínima de índices de contexto con niveles Crítico/Recomendado/Condicional, principio garbage in garbage out. Renumeración de secciones 3–12 → 4–13. |
| 2.1 | 2026-03-24 | Guillermo Becerra | Actualización Sección 9: modelo de branching expandido a tres niveles con ramas ad-hoc por sub-proceso y ramas paralelas nombradas por actividad/artefacto. Incluye guardrail de diseño, tabla de cuándo usar cada nivel, diagrama actualizado y anti-patrones de branching. |
| 2.0 | 2026-03-24 | Guillermo Becerra | Reescritura completa. Incorpora los tres sub-procesos (Shape, Ideate & Validate, Handoff to Delivery), políticas de gestión (continuidad, versionado, bitácora, HTML, retrospectiva), 13 reglas de comportamiento de Claude, y nueva estructura de carpetas. Elimina referencias a trabajo-compartido/, lo-que-no-sabemos.md y plan-aprendizaje.md. |
| 1.0 | 2026-03-17 | Guillermo Becerra | Creación inicial |
