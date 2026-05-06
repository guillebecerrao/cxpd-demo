---
title: "Skill: Documentador de Interview Snapshots"
author: Guillermo Becerra
created: 2026-03-24
last_modified: 2026-03-24
last_modified_by: Guillermo Becerra
version: 1.0
modification_count: 0
status: active
type: skill
bibliography: "Continuous Discovery Habits — Teresa Torres (2021), Capítulo 5"
---

# Skill: Documentador de Interview Snapshots

> Este skill convierte al agente de Product Management en un documentador experto de entrevistas de usuario, produciendo interview snapshots en el formato de Teresa Torres (*Continuous Discovery Habits*). Opera sobre transcripciones brutas generadas por IA (Gemini, u otras herramientas similares) y produce un artefacto de síntesis de una sola página que alimenta directamente el OST.

---

## Cuándo activar este skill

Activa este skill cuando el usuario quiera:

- **Documentar** una entrevista de usuario a partir de una transcripción bruta
- **Sintetizar** los aprendizajes clave de una entrevista en formato accionable
- **Extraer** oportunidades e insights de una conversación con un usuario
- **Preparar** el input para una sesión de actualización del OST

---

## Fundamentos teóricos (Torres, 2021)

### Qué es un interview snapshot

Un interview snapshot es un **artefacto de síntesis de una sola página** diseñado para capturar lo más importante de una entrevista individual. Su propósito es:

1. **Recordar** historias específicas semanas o meses después
2. **Identificar** oportunidades e insights de cada entrevista
3. **Construir** un banco de conocimiento del cliente con continuous interviewing
4. **Compartir** los aprendizajes con el equipo y stakeholders sin obligarlos a leer notas brutas

### Componentes del snapshot (Torres)

| Componente | Propósito |
|------------|-----------|
| **Nombre + Quick Facts** | Situar la historia en el contexto correcto; entender a qué tipo de usuario corresponde |
| **Quote memorable** | Ancla de memoria: un momento emocional o comportamiento distintivo dicho en las propias palabras del participante |
| **Oportunidades** | Necesidades, pain points o deseos expresados desde la perspectiva del usuario (no soluciones) |
| **Insights** | Observaciones interesantes que no encajan aún como oportunidades, pero que vale la pena registrar |

### Principios fundamentales

1. **La historia específica vale más que la generalización.** Lo que el usuario *hizo* en una instancia concreta es más confiable que lo que dice que *siempre hace*.
2. **Las oportunidades son necesidades, no soluciones.** Si el usuario pidió una feature, capturar la necesidad subyacente, no el pedido.
3. **Sintetizar inmediatamente.** El snapshot se crea justo después de la entrevista, mientras la memoria es fresca. No esperar a un batch de entrevistas.
4. **Ser exhaustivo.** Aunque algo parezca único de este usuario, capturarlo igual. Lo que hoy parece anecdótico mañana puede ser un patrón.

---

## Protocolo

### PASO 0: Pre-procesamiento de la transcripción

**Objetivo:** Preparar la transcripción bruta antes de analizarla.

Las transcripciones de IA (Gemini, u otras) tienen ruido estructural que debe resolverse antes de extraer insights.

**Acciones a realizar:**

1. **Identificar los speakers**
   - Gemini etiqueta por nombre cuando tiene acceso a los perfiles de Google Meet
   - Confirmar con el usuario cuál speaker es el entrevistador y cuál(es) son los participantes
   - Si hay más de un entrevistador, identificar quién conduce y quién observa

2. **Filtrar ruido de transcripción**
   - Ignorar muletillas ("eh", "o sea", "como que", "este")
   - Normalizar frases cortadas o autocorregidas: quedarse con la versión final de lo que el speaker quiso decir
   - Ignorar errores fonéticos obvios (nombres propios mal transcritos, tecnicismos distorsionados)

3. **Separar historia de generalización**
   - Marcar mentalmente los fragmentos donde el participante cuenta una instancia específica ("la última vez que usé la app fue cuando...")
   - Marcar los fragmentos donde el participante generaliza ("siempre hago X", "normalmente yo...")
   - El snapshot se ancla en las historias específicas; las generalizaciones son contexto secundario

4. **Verificar completitud**
   - ¿La transcripción cubre el inicio, medio y cierre de la entrevista?
   - ¿Hay fragmentos cortados o ilegibles que limiten el análisis? Mencionarlos en las notas del snapshot.

**Preguntar al usuario si:**
- No es posible identificar con certeza quién es el participante
- Hay partes de la transcripción que parecen cortadas o que el usuario quiera aclarar

---

### PASO 1: Reconstruir la historia cronológicamente

**Objetivo:** Extraer la historia específica que el participante contó y ordenarla en una línea de tiempo.

Las historias en las transcripciones aparecen fragmentadas: el participante salta entre el pasado, el presente, las generalizaciones y los pedidos de features. El trabajo del documentador es reconstruir la historia real.

**Proceso:**

1. Identificar la **pregunta generadora de historia** que usó el entrevistador ("Cuéntame sobre la última vez que...")
2. Extraer todos los fragmentos que corresponden a esa historia específica (no las generalizaciones)
3. Ordenarlos cronológicamente: inicio de la situación → acciones → resultado / estado actual
4. Identificar los **momentos clave** de la historia:
   - ¿Cuál fue el detonante que inició la situación?
   - ¿Qué hizo el usuario paso a paso?
   - ¿Qué obstáculos encontró?
   - ¿Cómo terminó?

**Formato interno de trabajo (no va al output final):**
```
HISTORIA: [nombre del participante]
Detonante: [qué lo llevó a hacer lo que hizo]
Paso 1: [acción]
Paso 2: [acción]
...
Resultado: [cómo terminó / estado actual]
Momentos de fricción: [dónde hubo dificultad, confusión o frustración]
```

---

### PASO 2: Extraer oportunidades

**Objetivo:** Identificar las necesidades, pain points y deseos del participante a partir de la historia reconstruida.

**Reglas de extracción:**

- Una oportunidad es una **necesidad, pain point o deseo** — nunca una solución ni una feature
- Si el participante pidió algo concreto ("quiero notificaciones de millas"), preguntar mentalmente: "¿Para qué necesita eso?" y capturar la necesidad subyacente
- Expresar las oportunidades **en primera persona, con el lenguaje del participante**: no "los usuarios no entienden los beneficios" sino "no sé por dónde empezar a entender qué me da el programa"
- Incluir también oportunidades que emergen de los **momentos de fricción** de la historia, aunque el participante no las haya articulado explícitamente

**Filtro de inclusión:**

| Criterio | Pregunta diagnóstica |
|----------|---------------------|
| ¿Es una necesidad o un dolor, no una solución? | "¿Puede un usuario decirlo sin mencionar una feature?" |
| ¿Emergió de la historia específica? | "¿Sucedió en el relato, no en una generalización?" |
| ¿Podría conectarse al outcome del equipo? | "¿Resolverla podría mover la métrica que perseguimos?" |

**Anti-patrones a evitar:**

| Anti-patrón | Ejemplo | Corrección |
|-------------|---------|-----------|
| Oportunidad = solución | "Quiere notificaciones de estado de millas" | "No sabe cuándo se acreditarán sus millas y cuánto tiempo falta" |
| Oportunidad = generalización | "Siempre le cuesta entender los beneficios" | Solo si también apareció en la historia específica |
| Oportunidad = sentimiento sin causa | "Se frustra con la app" | "No puede completar [acción concreta] sin salir de la app" |
| Oportunidad demasiado amplia | "No entiende el programa" | "No sabe qué tiene que hacer para pasar al siguiente nivel de categoría" |

---

### PASO 3: Extraer insights

**Objetivo:** Capturar observaciones relevantes que no encajan como oportunidades pero que vale la pena registrar.

Un **insight** es cualquier observación que:
- Revela algo sorprendente o no obvio sobre el comportamiento del usuario
- Ayuda a entender el contexto del participante
- Podría convertirse en oportunidad con más evidencia

**Ejemplos de insights válidos:**
- Un comportamiento inusual que solo este participante mostró
- Una contradicción entre lo que el participante dice que hace y lo que realmente hizo en la historia
- Una creencia o modelo mental que influye en cómo interpreta el producto
- Una forma no prevista de usar o no usar una funcionalidad

**Nota:** Los insights no necesitan ser accionables ahora. Su valor es acumulativo — a menudo un insight solitario de una entrevista se convierte en patrón cuando aparece en tres o cuatro más.

---

### PASO 4: Completar los Quick Facts

**Objetivo:** Capturar los datos de contexto que permiten entender a qué tipo de usuario corresponde esta historia.

Los Quick Facts varían según el producto y el tipo de usuario. Los campos típicos incluyen:

| Campo | Qué capturar |
|-------|-------------|
| **País / región** | País o región de residencia del participante |
| **Perfil de uso** | Cómo y con qué frecuencia usa el producto o servicio |
| **Antigüedad como usuario** | Hace cuánto comenzó a usar el producto (o si es nuevo) |
| **Canal de llegada** | Cómo llegó al producto (recomendación, publicidad, búsqueda, etc.) |
| **Contexto de uso** | Situación en la que usa el producto (trabajo, personal, móvil, desktop, etc.) |
| **[Campo específico del dominio]** | _Agregar campos relevantes para el tipo de usuario que se entrevista_ |

Adaptar los Quick Facts al dominio del producto antes de iniciar el primer ciclo de entrevistas. Agregar o quitar campos según la información disponible en la transcripción. No inventar datos que no aparecieron.

---

### PASO 5: Seleccionar la quote memorable

**Objetivo:** Encontrar la frase que mejor ancla la memoria de esta entrevista.

Una buena quote memorable:
- Es una frase exacta del participante (no una paráfrasis)
- Revela algo emocional, sorprendente o particularmente específico
- Ayuda a distinguir a este participante de los demás
- Puede ser breve — la brevedad la hace más memorable

**Proceso de selección:**
1. Identificar los 3–5 fragmentos más vividos o reveladores de la transcripción
2. Elegir el que mejor "desbloquea" la memoria de la historia completa
3. Transcribirla textualmente, respetando el lenguaje coloquial del participante

**Tip:** Las mejores quotes suelen ser aquellas que suenan a algo que solo esta persona podría decir.

---

### PASO 6: Producir el snapshot

**Objetivo:** Compilar todo lo anterior en el documento final.

Producir el snapshot en el **template markdown** definido al final de este skill. Guardarlo en:

```
shape/entrevistas/snapshots/snapshot_[nombre]_[fecha].md
```

Formato del nombre de archivo: `snapshot_nombre-apellido_YYYY-MM-DD.md`

---

## Comportamiento esperado del agente

### Al iniciar

1. **Solicitar la transcripción** si no fue provista: "¿Tienes la transcripción de la entrevista? Puedes pegarla directamente aquí."
2. **Confirmar speakers**: "¿Puedes confirmarme quién es el entrevistador en esta transcripción para que pueda identificar bien las voces?"
3. **Preguntar por contexto mínimo** si no está en la transcripción: "¿Sabes el país de origen del participante y su frecuencia de viajes aproximada?"

### Durante el análisis

- **Mostrar el trabajo**: al extraer oportunidades, indicar de qué fragmento de la historia provienen
- **Distinguir historia de generalización**: cuando una oportunidad emerge de una generalización y no de la historia, mencionarlo y bajarle el peso relativo
- **Preguntar ante ambigüedad**: si un fragmento podría ser una oportunidad o un insight, proponer ambas opciones y pedir criterio al usuario
- **No fabricar datos**: si algo no está en la transcripción, no incluirlo en el snapshot. Dejar el campo vacío o marcarlo como "no mencionado"

### Al finalizar

- Presentar el snapshot completo en formato markdown listo para guardar
- Indicar el nombre de archivo sugerido
- Señalar explícitamente si hay oportunidades que podrían alimentar el OST actual
- Sugerir si algún insight debería quedar en el plan de aprendizaje

---

## Anti-patrones del documentador

| Anti-patrón | Por qué es problemático |
|-------------|------------------------|
| Mezclar lo que dijo el entrevistador con lo que dijo el participante | Contamina las oportunidades con las hipótesis del equipo |
| Capturar lo que el participante *dijo que haría* en lugar de lo que *hizo* | Las intenciones declaradas son menos confiables que el comportamiento pasado |
| Escribir las oportunidades en lenguaje de empresa o producto | Pierde la perspectiva del usuario; las oportunidades deben poder ser dichas por el participante |
| Sintetizar tanto que se pierde el detalle | El snapshot debe recordar la historia, no solo el resumen |
| Omitir oportunidades que "parecen únicas" | Lo único de hoy puede ser el patrón de mañana |

---

## Template del snapshot

```markdown
---
tipo: interview-snapshot
participante: [Nombre completo]
fecha_entrevista: YYYY-MM-DD
fecha_snapshot: YYYY-MM-DD
estudio: [Nombre del estudio o ronda de entrevistas]
entrevistadores: [Nombre(s)]
fuente_transcripcion: Gemini / Google Meet
---

# Interview Snapshot — [Nombre del participante]

## Quote memorable

> *"[Frase exacta del participante]"*

---

## Quick Facts

| Campo | Valor |
|-------|-------|
| País / región | |
| Perfil de uso | |
| Antigüedad como usuario | |
| Canal de llegada | |
| Contexto de uso | |
| _[Campo específico del dominio]_ | |

---

## Historia

*Resumen cronológico de la historia específica que contó el participante. No generalizar — capturar lo que sucedió en esa instancia concreta.*

**Detonante:** [qué lo llevó a hacer lo que hizo]

**Lo que hizo:**
1. [paso]
2. [paso]
3. [paso]

**Cómo terminó / estado actual:** [resultado de la historia]

**Momentos de fricción:** [dónde hubo dificultad, confusión o frustración en la historia]

---

## Oportunidades

*Necesidades, pain points o deseos expresados desde la perspectiva del participante. Nunca soluciones.*

- **O1:** "[Oportunidad en primera persona, con el lenguaje del participante]"
  *Origen:* [fragmento de la historia que la respalda]

- **O2:** "[Oportunidad]"
  *Origen:* [fragmento de la historia que la respalda]

*(Agregar todas las que apliquen)*

---

## Insights

*Observaciones relevantes que no encajan aún como oportunidades.*

- [Insight 1]
- [Insight 2]

*(Puede quedar vacío si no hay insights distinguibles de las oportunidades)*

---

## Citas adicionales

> *"[Cita 2]"*

> *"[Cita 3]"*

---

## Notas del documentador

*Observaciones sobre la calidad de la transcripción, fragmentos ilegibles, dudas sobre la atribución de speakers, o contexto adicional que no encajó en las secciones anteriores.*
```

---

## Changelog

| Version | Date       | Author | Description |
|---------|------------|--------|-------------|
| 1.0     | 2026-03-24 | Guillermo Becerra | Creación inicial del skill basado en Teresa Torres, *Continuous Discovery Habits* (2021), Cap. 5 |
