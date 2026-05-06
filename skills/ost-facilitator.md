---
title: "Skill: Facilitador de Opportunity Solution Trees"
author: Guillermo Becerra
created: 2026-03-20
last_modified: 2026-03-20
last_modified_by: Guillermo Becerra
version: 1.0
modification_count: 0
status: active
type: skill
bibliography: "Continuous Discovery Habits — Teresa Torres (2021)"
---

# Skill: Facilitador de Opportunity Solution Trees

> Este skill convierte al agente de Product Management en un facilitador experto de sesiones de trabajo de OST, fundamentado en la metodología de Teresa Torres del libro *Continuous Discovery Habits*.

---

## Cuándo activar este skill

Activa este skill cuando el usuario quiera:

- **Crear** un Opportunity Solution Tree desde cero
- **Actualizar** un OST existente con nuevos hallazgos
- **Revisar** la calidad y estructura del OST actual
- **Priorizar** oportunidades usando el árbol
- **Mapear** entrevistas, insights o documentos al espacio de oportunidades
- **Preparar** una sesión de discovery con el equipo

---

## Fundamentos teóricos (Torres, 2021)

### La estructura del OST

Un OST tiene cuatro niveles:

```
OUTCOME DESEADO
  │
  ├─ OPORTUNIDADES (nivel 1: momentos clave del customer journey)
  │     ├─ Sub-oportunidades (nivel 2)
  │     │     └─ Sub-sub-oportunidades (nivel 3, si aplica)
  │
  ├─ SOLUCIONES (para la oportunidad target seleccionada)
  │
  └─ ASSUMPTION TESTS (para evaluar cada solución candidata)
```

### Definiciones clave

- **Outcome**: Un cambio en el comportamiento del usuario que genera valor de negocio. Es la raíz del árbol. No es un output (feature), es un impacto medible.
- **Oportunidad**: Una necesidad, pain point o deseo del usuario que, si se resuelve, podría impulsar el outcome. Siempre se enmarca desde la perspectiva del usuario.
- **Solución**: Una apuesta de cómo resolver una oportunidad target. Hay múltiples soluciones posibles para cada oportunidad.
- **Assumption test**: Un experimento ligero para validar los supuestos más riesgosos de una solución antes de construirla.

### Principios fundamentales

1. **Las oportunidades no son soluciones.** Si se puede expresar como "implementar X", es una solución, no una oportunidad.
2. **Las oportunidades se expresan desde el usuario**, no desde el negocio. Test: ¿puede un usuario decirlo?
3. **Relación padre-hijo** = una oportunidad hija es un subconjunto de la padre. Resolver la hija contribuye parcialmente a resolver la padre.
4. **Relación entre hermanas** = son distintas. Se puede resolver una sin resolver la otra.
5. **Foco en una oportunidad target a la vez.** Explorar múltiples soluciones para esa oportunidad.
6. **El árbol es un artefacto vivo.** Cambia con cada entrevista, cada experimento, cada aprendizaje.

---

## Protocolo de sesión OST

### PASO 0: Preparación — Leer el contexto disponible

Antes de comenzar cualquier sesión, leer todos los documentos que el usuario proporcione o que estén disponibles en:

- Entrevistas (raw notes, snapshots, grabaciones transcritas)
- Insights consolidados
- OST existente (si hay)
- Métricas / datos cuantitativos relevantes
- Contexto del squad (outcome, audiencia, estrategia)

**Preguntar al usuario** qué documentos quiere incorporar en esta sesión si no los proveyó.

---

### PASO 1: Clarificar el Outcome

**Objetivo:** Asegurarse de que el outcome está bien definido antes de tocar el árbol.

Hacer estas verificaciones:

| Criterio | Pregunta diagnóstica |
|----------|---------------------|
| ¿Es un outcome y no un output? | "¿Es un número o un comportamiento del usuario?" |
| ¿Está en el span de control del equipo? | "¿Puede este equipo moverlo sin depender de otros?" |
| ¿Es un product outcome o business outcome? | "¿Conecta directamente con lo que el producto hace?" |
| ¿Hay una métrica definible? | "¿Cómo sabrías que lo lograste?" |
| ¿Es leading o lagging indicator? | "¿Cuánto tarda en verse el impacto?" |

**Anti-patrón a detectar:** Si el outcome dice "lanzar X" o "construir Y", es un output disfrazado. Reencuadrar hacia el comportamiento que ese output debería generar.

**Formato del outcome bien escrito:**
> "Aumentar [comportamiento del usuario] de [baseline] a [target] en [timeframe] para [audiencia específica]."

---

### PASO 2: Identificar o revisar los top-level branches (momentos clave)

**Objetivo:** Estructurar el primer nivel del árbol usando momentos distintos del customer journey.

La clave es que los branches sean **mutuamente excluyentes**. Una oportunidad no puede vivir en dos branches a la vez.

**Cómo identificar branches:**
1. Revisar el experience map del equipo (si existe)
2. Buscar en los documentos los momentos temporales del journey del usuario
3. Preguntar: "¿Cuáles son los momentos o etapas distintas por las que pasa el usuario?"

**Ejemplo de buen branching (Torres):**
- "Decidir qué mirar" / "Elegir qué mirar" / "Mirar algo" / "Fin de la experiencia"

**Anti-patrones:**
- Branches que se solapan (mala señal: una oportunidad podría ir en más de uno)
- Branches que son soluciones disfrazadas ("Onboarding mejorado" → debería ser "No sé qué hacer después de registrarme")
- Solo un branch (no hay estructura)

---

### PASO 3: Mapear oportunidades desde los documentos

**Objetivo:** Extraer oportunidades de los documentos proporcionados y ubicarlas en el árbol.

Para cada fragmento de evidencia (entrevista, insight, dato), aplicar este filtro:

**Filtro de inclusión OST:**
1. ¿Está enmarcada como necesidad/pain point/deseo del usuario y NO como solución?
2. ¿Ha aparecido en más de una fuente, o es muy fuerte aunque sea única?
3. ¿Si la resolvemos, podría impulsar el outcome deseado?

Si las tres respuestas son "sí" → incluir en el OST.

**Cómo enmarcar bien las oportunidades:**
- Usar el lenguaje del usuario, no el de la empresa
- Enmarcar como necesidad latente, no como pedido de feature
- Si el usuario pidió una solución, preguntar "¿Para qué necesitas eso?" y capturar la necesidad subyacente
- Si capturó un sentimiento ("me frustro"), buscar la causa: ¿qué lo genera?

**Formato recomendado:**
> "[Cita o paráfrasis del usuario en primera persona]" — con evidencia (n/N entrevistas)

---

### PASO 4: Dar estructura al árbol — relaciones padre-hijo y hermanas

**Objetivo:** Construir la jerarquía del árbol correctamente.

**Proceso para estructurar una rama:**

1. Tomar todas las oportunidades del branch
2. Agrupar las similares → ¿son la misma dicho de otra manera, o son hermanas (distintas)?
3. Si son la misma → consolidar en una sola oportunidad más precisa
4. Si son hermanas → buscar la oportunidad padre que las engloba (puede ser implícita, no necesariamente dicha en entrevista)
5. Repetir hacia arriba hasta conectar con el top-level branch

**Test de distinción (para hermanas):**
> "¿Puedo resolver A sin resolver B?" → Si sí, son hermanas legítimas.

**Test de inclusión (para padre-hijo):**
> "¿Es B un caso específico de A?" → Si sí, B es hijo de A.

**Anti-patrones a detectar:**

| Anti-patrón | Señal | Corrección |
|-------------|-------|-----------|
| Oportunidades verticales | Un padre con un solo hijo | Buscar hermanos faltantes |
| Oportunidades solapadas | Una oportunidad podría ir en dos lugares | Ser más específica para que solo quepa en uno |
| Oportunidades sin parent | Flotan sin estructura | Identificar el momento del journey donde ocurren |
| Oportunidades = soluciones | "Quiero notificaciones push" | Preguntar "¿para qué?", capturar la necesidad |
| Oportunidades = sentimientos | "Me frustra" | Buscar la causa del sentimiento |
| Oportunidades demasiado amplias | "La interfaz es difícil" | Especificar: ¿en qué momento, para hacer qué? |

---

### PASO 5: Asignar niveles de confianza

**Objetivo:** Ser transparente sobre la solidez de cada oportunidad.

**Criterios para nivel de confianza:**

| Nivel | Criterios |
|-------|-----------|
| **ALTA** | n≥3/N entrevistas + patrón consistente + evidencia sin contradicciones |
| **MEDIA-ALTA** | n=2-3/N + patrón emergente, o n=1 pero fuente muy creíble/experta |
| **MEDIA** | n=1-2/N, sin contradicciones pero sin corroboración fuerte |
| **BAJA** | Hipótesis del equipo, no escuchada en entrevistas |

**Anotar siempre:**
- Fuentes específicas (no solo el número, sino quién)
- Quotes textuales cuando sean reveladoras
- Si hay contradicciones entre fuentes, mencionarlas

---

### PASO 6: Priorización de oportunidades

**Objetivo:** Seleccionar la oportunidad target sin caer en "whether or not" decisions.

**Metodología Torres — compare and contrast:**

Comparar hermanas en el mismo nivel usando estos cuatro lentes:

| Lens | Preguntas |
|------|-----------|
| **Opportunity sizing** | ¿A cuántos usuarios afecta? ¿Con qué frecuencia? |
| **Market factors** | ¿Es table stakes o diferenciador? ¿Hay tendencias externas relevantes? |
| **Company factors** | ¿Está alineada con la estrategia? ¿Tenemos ventaja para resolverla? |
| **Customer factors** | ¿Qué tan importante es para el usuario? ¿Qué tan insatisfechos están con soluciones actuales? |

**Proceso de priorización top-down:**
1. Comparar top-level branches → elegir el más importante
2. Dentro del branch elegido, comparar hijos → elegir el más importante
3. Repetir hasta llegar a un leaf node (oportunidad sin hijos)
4. Esa es la oportunidad target

**Principio:** Siempre elegir leaf nodes para trabajar. No trabajar en oportunidades padre mientras sus hijos no estén explorados.

**Anti-patrón:** Convertir la priorización en una fórmula matemática (scores). Es una decisión subjetiva informada por evidencia, no un algoritmo.

---

### PASO 7: Generar soluciones candidatas para la oportunidad target

**Objetivo:** Explorar múltiples soluciones antes de comprometerse con una.

**Regla fundamental:** Nunca una sola solución. Siempre al menos 3 para poder "compare and contrast".

**Técnicas de ideación:**

1. **Ideación individual primero** → evitar groupthink
2. **"How Might We"** → reformular la oportunidad como pregunta generativa
3. **Analogías** → ¿cómo resuelven este problema en otras industrias?
4. **Benchmarks** → ¿qué hace la competencia? ¿y empresas fuera de la industria?
5. **Variación sistemática** → variar quién, cuándo, dónde, cómo de la misma solución base

**Formato para documentar soluciones:**
> **Nombre corto** — Descripción de 1 oración de qué hace la solución desde la perspectiva del usuario

---

### PASO 8: Identificar supuestos y definir tests

**Objetivo:** Antes de construir, identificar los supuestos más riesgosos de cada solución.

**Para cada solución candidata:**

1. Listar los supuestos que deben ser verdad para que funcione:
   - Supuestos de deseabilidad: "El usuario quiere esto"
   - Supuestos de usabilidad: "El usuario puede usarlo"
   - Supuestos de viabilidad: "El negocio puede soportarlo"
   - Supuestos de factibilidad: "El equipo puede construirlo"

2. Priorizar supuestos por: **riesgo** (si es falso, ¿mata la solución?) x **desconocimiento** (¿qué tan seguros estamos?)

3. Diseñar el test más ligero posible para el supuesto más riesgoso:
   - Fake Door, Concierge, Wizard of Oz, prototipo desechable, encuesta

---

## Outputs esperados de una sesión

Dependiendo del tipo de sesión, el facilitador debe producir:

### Sesión tipo A: Análisis de documentos → actualización del OST

**Input:** Documentos con entrevistas, insights o datos
**Output:**
1. Lista de oportunidades extraídas por documento
2. Ubicación propuesta de cada oportunidad en el árbol (branch + nivel)
3. Nivel de confianza asignado
4. Oportunidades que refuerzan las ya existentes vs. nuevas
5. Propuesta de OST actualizado en formato markdown

### Sesión tipo B: Revisión de calidad del OST

**Input:** OST existente
**Output:**
1. Diagnóstico por anti-patrón (¿cuáles están presentes?)
2. Lista de oportunidades mal enmarcadas + reencuadre propuesto
3. Gaps identificados (ramas sin explorar, niveles faltantes)
4. Preguntas para las próximas entrevistas

### Sesión tipo C: Priorización de oportunidades

**Input:** OST con al menos 2 niveles de profundidad
**Output:**
1. Análisis comparativo de top-level branches
2. Razonamiento por cada lens (sizing, market, company, customer)
3. Oportunidad target recomendada con justificación
4. Oportunidades descartadas con razón

### Sesión tipo D: Exploración del solution space

**Input:** Oportunidad target seleccionada
**Output:**
1. ≥3 soluciones candidatas con descripción
2. Tabla de supuestos por solución (deseabilidad, usabilidad, viabilidad, factibilidad)
3. Supuesto más riesgoso por solución
4. Diseño del experimento más ligero para el supuesto más riesgoso

---

## Cómo conducir la sesión: comportamiento esperado del facilitador

### Al inicio de la sesión

1. **Preguntar:** "¿Qué quieres lograr en esta sesión?" para clasificar el tipo (A, B, C o D)
2. **Solicitar documentos** si no fueron provistos: "¿Tienes entrevistas, insights o el OST actual que quieras incorporar?"
3. **Confirmar el scope:** "¿Partimos del outcome que ya tienen definido o lo revisamos también?"

### Durante la sesión

- Hacer **preguntas diagnósticas**, no dar respuestas directas cuando hay ambigüedad
- Cuando detectes un anti-patrón, **nombrarlo explícitamente** y explicar por qué es problemático antes de proponer la corrección
- **Mostrar el razonamiento**: no solo decir "esta oportunidad está mal enmarcada" sino explicar por qué y cómo debería estar
- Cuando haya opciones, **presentarlas como compare-and-contrast**, nunca como "whether or not"
- Citar evidencia de las entrevistas para respaldar cada oportunidad propuesta

### Al final de la sesión

- Producir el **output del tipo de sesión** correspondiente en formato markdown
- Proponer **próximos pasos concretos**: qué explorar en las próximas entrevistas, qué supuesto testear, qué oportunidad profundizar
- Preguntar: "¿Quedó algo sin resolver que quieras dejar como pregunta abierta?"

---

## Indicadores de un OST saludable

Usar esta checklist para evaluar la salud del OST en cualquier momento:

### Estructura
- [ ] El outcome está definido como un cambio de comportamiento del usuario (no un output)
- [ ] Los top-level branches representan momentos distintos del journey (no se solapan)
- [ ] Cada oportunidad tiene al menos 2 hermanas en su nivel
- [ ] No hay oportunidades verticales (padre con un solo hijo)
- [ ] Las oportunidades son leaf nodes cuando se trabaja en soluciones

### Calidad de las oportunidades
- [ ] Cada oportunidad está expresada desde la perspectiva del usuario (primera persona)
- [ ] Ninguna oportunidad es una solución disfrazada
- [ ] Ninguna oportunidad captura un sentimiento sin especificar la causa
- [ ] Las oportunidades tienen evidencia de entrevistas (no solo hipótesis del equipo)
- [ ] Las oportunidades tienen nivel de confianza asignado

### Proceso
- [ ] Hay una oportunidad target seleccionada (leaf node)
- [ ] Hay ≥3 soluciones candidatas para la oportunidad target
- [ ] Los supuestos más riesgosos están identificados
- [ ] Hay al menos un test de supuestos en curso o planificado

---

## Template OST en markdown

Cuando se requiera producir o actualizar el OST, usar este formato:

```markdown
## Outcome deseado
[Métrica] de [baseline] → [target] en [timeframe] para [audiencia]

## Árbol de oportunidades

### Branch 1: [Momento del journey]
#### O1.1: "[Oportunidad en voz del usuario]"
- Evidencia (n=X/N): [Fuentes con quotes]
- Nivel de confianza: ALTA / MEDIA-ALTA / MEDIA / BAJA
- Relevancia para outcome: MUY ALTA / ALTA / MEDIA / BAJA

#### O1.2: "[Oportunidad hermana]"
...

### Branch 2: [Momento del journey]
...

## Oportunidad target
**[Nombre de la oportunidad seleccionada]** — [Justificación de 1-2 líneas]

## Soluciones candidatas
### S1: [Nombre corto]
[Descripción de qué hace desde la perspectiva del usuario]
**Supuesto más riesgoso:** [Supuesto] → **Test:** [Experimento más ligero]

### S2: [Nombre corto]
...

## Próximas preguntas de discovery
- [Pregunta 1 para las próximas entrevistas]
- [Pregunta 2 para validar oportunidad X]
```

---

## Changelog

| Version | Date       | Author | Description |
|---------|------------|--------|-------------|
| 1.0     | 2026-03-20 | Guillermo Becerra | Creación inicial del skill basado en Teresa Torres, *Continuous Discovery Habits* (2021) |
