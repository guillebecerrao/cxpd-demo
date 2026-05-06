---
title: "Solución Elegida — Coverwise Conversational Response — Ciclo 01/2026"
oportunidad: "C1.1 — El asegurado recibe una respuesta de Coverwise pero no le genera suficiente claridad ni confianza para actuar sin llamar"
author: Claude (I&V facilitador)
created: 2026-05-06
last_modified: 2026-05-06
last_modified_by: Claude (I&V facilitador)
version: 1.0
modification_count: 1
status: in_progress
cycle: ciclo-01-2026
---

# Solución Elegida — Coverwise Conversational Response

> **Oportunidad target:** C1.1 — La respuesta de Coverwise no genera claridad ni confianza para actuar sin llamar.
>
> **Outcome buscado:** Reducir el % de usuarios que llaman al call center después de recibir una respuesta digital. Mover KR3 (NPS post-consulta) de 28 a ≥ 38 en el primer ciclo post-build.
>
> **Estado:** Solución elegida por la tríada. Pendiente validación de SA-5, SA-6 y SA-7 pre-build.

---

## 1. Decisión de solución

### Solución elegida: Coverwise Conversational Response

La tríada eligió la **combinación de Ideas 1 + 2 + 3** como apuesta principal del ciclo:

- **Respuesta en lenguaje natural (Idea 1):** El LLM transforma el texto técnico de la póliza en una respuesta conversacional, breve y en el vocabulario del usuario.
- **Indicador de plan y certeza (Idea 2):** Cada respuesta indica explícitamente el plan del asegurado y el nivel de certeza de la respuesta. Elimina la ambigüedad de "¿esto aplica a mi cobertura?"
- **Siguiente paso sugerido (Idea 3):** Post-respuesta, el sistema sugiere una acción concreta (agendar, encontrar prestador, guardar la confirmación). Cierra el loop del journey en el canal digital.

**Razones de la decisión:**
- Las tres ideas atacan dimensiones complementarias de C1.1: claridad del lenguaje (I1), confianza en la personalización (I2), y acción post-respuesta (I3). Funcionan como un sistema, no como features independientes.
- SA-7 (precisión del LLM en coberturas) es el supuesto de mayor riesgo — pero es validable con una evaluación técnica rápida antes del build. No requiere investigación de usuario.
- La Idea 4 (escalación inteligente) se reserva como fallback para casos de baja certeza: está contemplada en el diseño pero no es el foco del experimento principal.

### Estado de las otras ideas

| Solución | Estado | Razón |
|----------|--------|-------|
| Idea 4 — Escalación inteligente | En pausa / fallback | Complementa la solución pero no es el experimento principal. Implementar solo para casos de certeza baja. |
| Idea 5 — Respuesta dual (simple + técnica) | Diferida | Válida para usuarios avanzados. Agregar como iteración post-validación si SA-5 sugiere que hay un segmento que prefiere texto técnico. |

---

## 2. Descripción de la solución

### Flujo conversacional propuesto

**1. El asegurado formula su consulta** en lenguaje coloquial (ej: "¿me cubren la resonancia de rodilla?")

**2. Coverwise procesa en dos capas:**
   - Capa semántica: mapea el vocabulario coloquial al procedimiento técnico (ej: "resonancia de rodilla" → "RMN articulación femoropatelar")
   - Capa LLM: genera la respuesta en lenguaje coloquial personalizada al plan del asegurado

**3. La respuesta incluye tres elementos:**
   - **Confirmación clara:** "Sí, está cubierto" / "No está cubierto" / "Necesita revisión"
   - **Indicador de plan y certeza:** "Aplicado a tu Plan Digital Plus · Alta certeza"
   - **Traducción práctica + siguiente paso:** "Esto significa que pagas solo $12.000 de copago. ¿Te ayudo a agendar?"

**4. Si la certeza es baja (< umbral a definir):**
   - Se activa la escalación inteligente (Idea 4): "No estoy 100% seguro. ¿Conectamos con un asesor que ya tiene tu consulta lista?"

### Restricciones regulatorias incorporadas

- La respuesta incluye siempre un disclaimer corto (no modal, no bloqueante): "Esta información es orientativa y no reemplaza la resolución formal de NexHealth."
- No se almacena el historial de consultas sin consentimiento explícito del usuario.

---

## 3. Diseño del experimento

| Campo | Detalle |
|-------|---------|
| **Tipo** | A/B test en producción |
| **Hipótesis central** | Si los asegurados reciben una respuesta conversacional personalizada a su plan + siguiente paso sugerido, entonces el NPS post-consulta mejorará ≥ 5 puntos y el % de usuarios que llaman en las 24h siguientes a una consulta digital caerá ≥ 20% |
| **Variantes** | Control: respuesta actual (texto de póliza + PDF). Variante: Coverwise Conversational Response |
| **Métricas primarias** | NPS post-consulta (encuesta in-app, 2 preguntas); % de llamadas al call center en las 24h post-consulta digital |
| **Métricas secundarias** | Tasa de adopción del CTA "siguiente paso"; tiempo en sesión post-respuesta; % de consultas escaladas (certeza baja) |
| **Criterio de éxito** | NPS +5 puntos ó reducción de llamadas ≥ 20% en los primeros 14 días. Si ambas mejoran: ship. Si NPS mejora pero llamadas no: iterar diseño del siguiente paso. Si ninguna mejora: revisar hipótesis SA-5. |
| **Muestra / duración** | N= a calcular con Paula Castillo (Data Analyst). Estimado: 3-4 semanas para significancia estadística con el tráfico actual de Coverwise |

---

## 4. Supuestos que respaldan la decisión

Ver registro completo en `ideate-validate/solution-assumptions.md`.

**Supuestos pre-build a validar antes de invertir en el build:**
- **SA-5** — El asegurado prefiere lenguaje coloquial sobre texto técnico de póliza como fuente de confianza
- **SA-6** — El asegurado comprende y actúa sobre el siguiente paso sugerido
- **SA-7** — El LLM genera respuestas de cobertura precisas sin alucinaciones sobre condiciones del plan

**Plan de validación pre-build:** Ver `ideate-validate/test-plan.md`

---

## Changelog

| Versión | Fecha | Autor | Descripción |
|---------|-------|-------|-------------|
| 1.0 | 2026-05-06 | Claude (I&V facilitador) | Versión inicial. Ideas 1+2+3 combinadas. Experimento A/B diseñado. 3 supuestos pre-build identificados. |
