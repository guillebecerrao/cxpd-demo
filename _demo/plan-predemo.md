---
title: "Plan Pre-Demo — Preparación TW Executives"
created: 2026-05-06
demo-date: 2026-05-06
hours-available: 4
status: active
type: internal-workplan
---

# Plan Pre-Demo — TW Executives
## Preparación en 4 horas — 2026-05-06

**Contexto**: La demo está agendada en ~4 horas. La audiencia ya conoce el framework (pidieron la demo porque les flipó el concepto). El objetivo es mostrar el E2E-SDPB en acción con un caso ficticio concreto, con un producto en producción al final.

**Estrategia de contingencia**: Grabar Loom como respaldo. Si algo falla en la demo en vivo, presentar el video y responder preguntas. Esto reduce el riesgo al mínimo y libera la reu para lo que importa: la conversación.

---

## Checklist de salida

Antes de entrar a la reu, marcar todos como completados:

- [x] Seed del AI-Framework en `cxpd-demo/` — hecho
- [x] Plan abstracto en `_demo/plan-5-dias.md` — hecho
- [x] Este plan pre-demo — hecho
- [x] Caso ficticio definido — NexHealth · Coverwise · `coverwise.becerra-ojeda.cl`
- [x] Plan aplicado en `_demo/plan-5-dias-nexhealth.md`
- [x] Slides generadas — `_demo/E2E-SDPB-Coverwise-TW.pptx` (10 slides EN)
- [x] Repo GitHub creado — `guillebecerrao/cxpd-demo` (público, mono-repo: contexto SDPB + codebase en `dist/`)
- [x] Cloudflare Pages project creado y conectado al repo GitHub (deploy automático en push/merge a `main`, output `dist/`)
- [x] DNS de `coverwise.becerra-ojeda.cl` apuntado — custom domain inicializando en Cloudflare Pages
- [ ] Seed populado con contexto mínimo del caso (opcional, alta recomendación)
- [ ] Loom grabado (opcional pero recomendado)

---

## Timeline de 4 horas

### Bloque 1 — T+0:00 a T+0:15 | Claude termina el setup ← COMPLETADO

Seed + plan abstracto + este plan. Sin intervención humana.

---

### Bloque 2 — T+0:15 a T+0:45 | Definir el caso ficticio

**Duración estimada**: 30 minutos  
**Quién**: Guillermo + Claude en sesión  
**Output**: caso ficticio validado

El caso ficticio tiene que cumplir:
- Reconocible para ejecutivos TW (empresa mediana-grande, industria que TW toca: fintech, retail, salud, utilities, gobierno)
- Problema de producto real y no trivial — suficiente como para que los 5 días tengan peso
- Producto que se pueda construir en horas de build con Claude Code (scope acotado)
- Un nombre memorable para el producto y para la empresa cliente

**Cómo activarlo**:  
Abrir nueva sesión en Claude Code y decir:  
> "Quiero definir el caso ficticio para la demo E2E-SDPB para TW executives. Lee `_demo/plan-5-dias.md` y propón 3 opciones de cliente ficticio con: nombre empresa, industria, problema de producto, usuario objetivo, nombre del producto, y URL sugerida del tipo `[nombre].becerra-ojeda.cl`."

Criterios para elegir entre las opciones:
- ¿Se puede construir en un día de build con Claude Code? (scope realista)
- ¿El problema es lo suficientemente universal para resonar con ejecutivos de consultoría?
- ¿El producto en producción se ve impresionante con poco build?

---

### Bloque 3 — T+0:45 a T+1:30 | Plan de 5 días aplicado al caso

**Duración estimada**: 45 minutos  
**Quién**: Claude (con validación de Guillermo en los puntos de decisión)  
**Output**: `_demo/plan-5-dias-[cliente].md` — copia del plan ya aplicada al caso

Instrucción para Claude:  
> "Con el caso definido de [cliente], crea `_demo/plan-5-dias-[cliente].md` como una copia de `_demo/plan-5-dias.md` adaptada al caso. Reemplaza las referencias genéricas por el cliente y el producto concreto. Mantén el workflow idéntico al abstracto — solo adapta los nombres, el contexto y los ejemplos de artefactos al caso. No toques `plan-5-dias.md`."

Después de generado, revisar:
- ¿Los artefactos del Día 1 tienen sentido para este cliente?
- ¿El producto del Día 5 se puede construir realmente?
- ¿Hay algo que simplificar para la demo sin perder la esencia del framework?

---

### Bloque 4 — T+1:30 a T+2:30 | Slides del engagement plan

**Duración estimada**: 60 minutos  
**Quién**: Claude genera, Guillermo revisa  
**Output**: archivo de slides listo para presentar

**Estructura del deck** (10 slides):

| # | Slide | Contenido |
|---|-------|-----------|
| 1 | Portada | Logo cliente ficticio · "E2E-SDPB en acción" · fecha |
| 2 | El brief del cliente | Empresa, problema, usuario objetivo — el punto de partida |
| 3 | La propuesta | 5 días de la idea al producto en producción |
| 4 | Cómo funciona el framework | Diagrama: Shape → Ideate & Validate → Handoff → Build |
| 5 | Día 1-2 | Shape + Ideate: artefactos, agentes, tríada en acción |
| 6 | Día 3 | Validate: evidencia real, solución elegida con justificación |
| 7 | Día 4 | Handoff: specs listas para dev, el contrato con el agente |
| 8 | Día 5 | Build + Deploy: Claude Code construye desde las specs, producto en prod |
| 9 | El repo | Screenshot/walkthrough del SDPB-Context repo: estructura, CLAUDE.md, artefactos generados |
| 10 | La propuesta para TW | Cómo lo haríamos juntos: roles, modelo de trabajo, infraestructura |

**Formato preferido**: HTML presentación (rápido, sin dependencias externas, editable después en código).  
**Fallback**: si se necesita PPT, solicitar versión PPT con python-pptx después de tener el HTML aprobado.

**Instrucción para Claude**:  
> "Genera el deck de slides para la demo TW executives. Usa el plan `_demo/plan-5-dias-[cliente].md` como fuente. Formato HTML presentación full-screen (estilo de los dashboards del sistema). Audiencia: ejecutivos de Thoughtworks que ya conocen el framework y quieren ver la ejecución. Tono: concreto, ejecutivo, con datos de artefactos reales del plan."

---

### Bloque 5 — T+2:30 a T+3:00 | Setup Cloudflare + Dominio

**Duración estimada**: 20 minutos (más simple que GCP)
**Quién**: Guillermo ejecuta, Claude guía  
**Output**: Cloudflare Pages project creado + `coverwise.becerra-ojeda.cl` apuntado

**Stack de deploy**: Cloudflare Pages (frontend/estático) + Workers si se necesita lógica de backend en la demo. Sin billing, sin proyectos, sin APIs que habilitar.

**Pasos**:

**A. Crear el Cloudflare Pages project** (5 min):
1. Ir a [dash.cloudflare.com](https://dash.cloudflare.com) → Pages → Create a project
2. Opción: conectar repo de GitHub, o usar **Direct Upload** (más rápido para demo)
3. Nombre del project: `coverwise`
4. Con Direct Upload: subir el `dist/` o el `index.html` del build — URL inmediata `coverwise.pages.dev`

**B. Configurar dominio custom** (10 min):
1. En el project → Custom domains → Add custom domain
2. Ingresar `coverwise.becerra-ojeda.cl`
3. Cloudflare agrega el registro DNS automáticamente si `becerra-ojeda.cl` ya está en Cloudflare (verificar)
4. Si el dominio no está en Cloudflare DNS: agregar CNAME `coverwise` → `coverwise.pages.dev` en el panel del registrador
5. Propagación: instantánea si el dominio ya está en Cloudflare

**C. Deploy de placeholder** (5 min, opcional):
Un `index.html` mínimo con el nombre del producto — confirma que el dominio funciona antes de la demo.

```bash
# Con Wrangler CLI (si está instalado)
npx wrangler pages deploy ./dist --project-name coverwise

# O direct upload desde el dashboard — más rápido para demo
```

**Workers (si aplica)**: si Coverwise necesita lógica de API (proxy a Claude API, procedure resolver), usar un Worker en el mismo proyecto. Sin servidor, sin contenedores, sin región a elegir.

**Fallback de demo**: si el dominio custom no está listo, `coverwise.pages.dev` funciona igual de bien para la demo. La URL personalizada es el detalle, no el argumento.

---

### Bloque 6 — T+3:00 a T+3:30 | Populate seed mínimo (opcional, alto impacto)

**Duración estimada**: 30 minutos  
**Quién**: Claude  
**Output**: `contexto/corporativo/` y `contexto/estrategia/ost.md` v1 con contenido del caso ficticio

Esto permite abrir Claude Code durante la demo y mostrar que el agente "ya sabe" con quién está trabajando y qué problema está resolviendo — el contexto del cliente vive en el repo, no en la cabeza del PM.

**Instrucción para Claude**:  
> "Popula el seed de `cxpd-demo/` con el contexto mínimo del caso ficticio [cliente]. Llena: `contexto/corporativo/estructura-organizacional.md`, `contexto/corporativo/estrategia-producto.md`, `contexto/squad/squad.md`, y `contexto/estrategia/ost.md` v1 con el árbol de oportunidades hasta el nodo hoja elegido. Usa `plan-5-dias-[cliente].md` como fuente de verdad."

---

### Bloque 7 — T+3:30 a T+4:00 | Ensayo + Loom

**Duración estimada**: 30 minutos  
**Quién**: Guillermo  
**Output**: video Loom listo como backup + Guillermo ensayado para la reu

**Estructura del Loom** (10-15 minutos):

| Minuto | Contenido |
|--------|-----------|
| 0:00-1:00 | Intro: "les muestro cómo funciona el E2E-SDPB con un caso real en 5 días" |
| 1:00-3:00 | El repo: abrir `cxpd-demo/` en Claude Code, mostrar la estructura, leer el CLAUDE.md |
| 3:00-5:00 | El contexto: abrir `contexto/corporativo/` y el OST — el agente ya sabe con quién trabaja |
| 5:00-8:00 | Walkthrough del plan de 5 días: artefactos de cada día, quién hace qué |
| 8:00-10:00 | El producto en prod: abrir la URL en el browser |
| 10:00-12:00 | La propuesta TW: cómo lo haríamos con un equipo Thoughtworks |

**Estrategia de presentación en la reu**:

**Opción A — Loom primero** (recomendada): Presentar el video grabado, parar al terminar, responder preguntas. Elimina el riesgo de fallo en demo en vivo. El video garantiza coherencia narrativa.

**Opción B — Mixta**: Mostrar los primeros 3 minutos en vivo (abrir Claude Code en el repo, mostrar el contexto populado), luego cortar a video para el build y el deploy. Más impresionante si sale bien.

**Opción C — Todo en vivo**: Solo si hay confianza alta en que todo está listo y hay señal estable. Riesgo: cualquier demora de Claude rompe el ritmo.

---

## Estimación de tiempo total

| Bloque | Tarea | Tiempo | Quién |
|--------|-------|--------|-------|
| 1 | Setup (seed + planes) | 15 min | Claude |
| 2 | Definir caso ficticio | 30 min | Guillermo + Claude |
| 3 | Plan aplicado al caso | 45 min | Claude |
| 4 | Slides | 60 min | Claude + Guillermo |
| 5 | Cloudflare Pages + Dominio | 20 min | Guillermo |
| 6 | Populate seed | 30 min | Claude |
| 7 | Ensayo + Loom | 30 min | Guillermo |
| **Total** | | **~4 horas** | |

Si el tiempo es ajustado, el orden de sacrificio es: Bloque 6 (populate seed) → Bloque 7 Loom (solo ensayo) → Bloque 5 dominio custom (usar `coverwise.pages.dev` directo en vez de `coverwise.becerra-ojeda.cl`).

---

## Próximo paso inmediato

Abrir una sesión con Claude y ejecutar el Bloque 2: definir el caso ficticio.

Prompt de inicio:

> Quiero definir el caso ficticio para la demo E2E-SDPB que haré en ~3.5 horas a ejecutivos de Thoughtworks. Lee el archivo `activities/business/product-building/latam-tw/tw/cxpd-demo/_demo/plan-5-dias.md` y propón 3 opciones de cliente ficticio. Cada opción debe incluir: nombre de la empresa cliente, industria, el problema de producto que quieren resolver, el usuario objetivo del producto, el nombre del producto, y la URL sugerida (formato `[nombre].becerra-ojeda.cl`). Las opciones deben ser reconocibles para ejecutivos de una consultora de tecnología enterprise, con un problema de producto que no sea trivial, y un MVP buildeable en un día con Claude Code.
